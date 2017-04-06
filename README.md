# api documentation for  [detective (v4.5.0)](https://github.com/substack/node-detective#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-detective.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-detective) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-detective.svg)](https://travis-ci.org/npmdoc/node-npmdoc-detective)
#### find all require() calls by walking the AST

[![NPM](https://nodei.co/npm/detective.png?downloads=true)](https://www.npmjs.com/package/detective)

[![apidoc](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-detective_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-detective/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Halliday",
        "email": "mail@substack.net",
        "url": "http://substack.net"
    },
    "bugs": {
        "url": "https://github.com/substack/node-detective/issues"
    },
    "dependencies": {
        "acorn": "^4.0.3",
        "defined": "^1.0.0"
    },
    "description": "find all require() calls by walking the AST",
    "devDependencies": {
        "tap": "^5.7.1"
    },
    "directories": {},
    "dist": {
        "shasum": "6e5a8c6b26e6c7a254b1c6b6d7490d98ec91edd1",
        "tarball": "https://registry.npmjs.org/detective/-/detective-4.5.0.tgz"
    },
    "gitHead": "4aa3713807feb699f18d83152e5475d0ec5345b6",
    "homepage": "https://github.com/substack/node-detective#readme",
    "keywords": [
        "require",
        "source",
        "analyze",
        "ast"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "substack",
            "email": "substack@gmail.com"
        },
        {
            "name": "zertosh",
            "email": "zertosh@gmail.com"
        }
    ],
    "name": "detective",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/substack/node-detective.git"
    },
    "scripts": {
        "test": "tap test/*.js"
    },
    "version": "4.5.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module detective](#apidoc.module.detective)
1.  [function <span class="apidocSignatureSpan">detective.</span>find (src, opts)](#apidoc.element.detective.find)



# <a name="apidoc.module.detective"></a>[module detective](#apidoc.module.detective)

#### <a name="apidoc.element.detective.find"></a>[function <span class="apidocSignatureSpan">detective.</span>find (src, opts)](#apidoc.element.detective.find)
- description and source-code
```javascript
find = function (src, opts) {
    if (!opts) opts = {};

    var word = opts.word === undefined ? 'require' : opts.word;
    if (typeof src !== 'string') src = String(src);

    var isRequire = opts.isRequire || function (node) {
        return node.callee.type === 'Identifier'
            && node.callee.name === word
        ;
    };

    var modules = { strings : [], expressions : [] };
    if (opts.nodes) modules.nodes = [];

    var wordRe = word === 'require' ? requireRe : RegExp('\\b' + word + '\\b');
    if (!wordRe.test(src)) return modules;

    var ast = parse(src, opts.parse);

    function visit(node, st, c) {
        var hasRequire = wordRe.test(src.slice(node.start, node.end));
        if (!hasRequire) return;
        walk.base[node.type](node, st, c);
        if (node.type !== 'CallExpression') return;
        if (isRequire(node)) {
            if (node.arguments.length) {
                var arg = node.arguments[0];
                if (arg.type === 'Literal') {
                    modules.strings.push(arg.value);
                }
                else {
                    modules.expressions.push(src.slice(arg.start, arg.end));
                }
            }
            if (opts.nodes) modules.nodes.push(node);
        }
    }

    walk.recursive(ast, null, {
        Statement: visit,
        Expression: visit
    });

    return modules;
}
```
- example usage
```shell
...
        opts.allowReturnOutsideFunction, true
    ),
    allowHashBang: defined(opts.allowHashBang, true)
});
}

var exports = module.exports = function (src, opts) {
return exports.find(src, opts).strings;
};

exports.find = function (src, opts) {
if (!opts) opts = {};

var word = opts.word === undefined ? 'require' : opts.word;
if (typeof src !== 'string') src = String(src);
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
