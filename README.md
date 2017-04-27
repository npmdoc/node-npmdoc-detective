# npmdoc-detective

#### basic api documentation for  [detective (v4.5.0)](https://github.com/substack/node-detective#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-detective.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-detective) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-detective.svg)](https://travis-ci.org/npmdoc/node-npmdoc-detective)

#### find all require() calls by walking the AST

[![NPM](https://nodei.co/npm/detective.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/detective)

- [https://npmdoc.github.io/node-npmdoc-detective/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-detective/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-detective/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-detective/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Halliday",
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
            "name": "substack"
        },
        {
            "name": "zertosh"
        }
    ],
    "name": "detective",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/substack/node-detective.git"
    },
    "scripts": {
        "test": "tap test/*.js"
    },
    "version": "4.5.0",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
