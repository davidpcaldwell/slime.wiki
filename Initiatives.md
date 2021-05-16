# TypeScript

Integrate TypeScript declarations with api.html files; see [TSDoc](https://github.com/microsoft/tsdoc) (which contains a parser for TypeScript documentation comments, probably necessary), a library for running [JSDoc tests](https://www.npmjs.com/package/jsdoc-test), [Compiler API](https://github.com/microsoft/TypeScript/wiki/Using-the-Compiler-API) and [Parser](https://github.com/buehler/node-typescript-parser/blob/master/src/TypescriptParser.ts).

## Use at runtime; see `jsh/tools/test/typescript.jsh.js`.

* Insert https://www.ietf.org/mailman/listinfo/media-types into comment in code loader
* When running TypeScript under Rhino, get/set code causes problems
* When running under Nashorn, lack of native Map causes problems

# Create better HTML management

Would like to replace `jsapi` model used by tests with a new, universal HTML parsing model. Should be trying to advance [loader/api/test/new-document-implementation.jsh.js](https://bitbucket.org/davidpcaldwell/slime/src/default/loader/api/test/new-document-implementation.jsh.js).

# Improve testing structure

## Improve testability of `jrunscript` unit tests

Document new structure of tests, including the split between suite.jsh.js and jrunscript.jsh.js

## Restructure browser tests

* Create (if needed; document if not) a way to isolate certain browser tests in a suite to be run

# Separate contributor-related code

# Get SLIME running on GraalVM

## Get unit tests running

`env JSH_ENGINE=graal xJSH_DEBUG_SCRIPT=graal SLIME_UNIT_JSH_UNBUILT_ONLY=true ./jsh.bash contributor/jrunscript.jsh.js`

### Get `$api` tests running

See #328.

Above with `-part \$api`

### Get `jsh` build working

## JVisualVM does not work

See GraalVM [Known Issues](https://www.graalvm.org/docs/release-notes/known-issues/).