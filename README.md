# Deno `mocha -r` missing module bug

It seems like deno doesn't install all packages listed in `package.json`.

Error:

```sh
✖ ERROR: Error: Cannot find module '@babel/register'
Require stack:
- /project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/nodejs/esm-utils.js
- /project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/mocha.js
- /project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/cli/one-and-dones.js
- /project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/cli/options.js
- /project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/bin/mocha.js
    at Function.Module._resolveFilename (ext:deno_node/01_require.js:828:15)
    at Function.Module._load (ext:deno_node/01_require.js:675:27)
    at Module.require (ext:deno_node/01_require.js:894:19)
    at require (ext:deno_node/01_require.js:1030:16)
    at exports.requireOrImport (file:///project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/nodejs/esm-utils.js:53:16)
    at async exports.handleRequires (file:///project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/cli/run-helpers.js:94:28)
    at async file:///project/node_modules/.deno/mocha@10.2.0/node_modules/mocha/lib/cli/run.js:349:25 {
  code: "MODULE_NOT_FOUND",
  requireStack: [
    "/project/node_modules/.deno/mocha@10.2.0/"... 42 more characters,
    "/project/node_modules/.deno/mocha@10.2.0/"... 31 more characters,
    "/project/node_modules/.deno/mocha@10.2.0/"... 43 more characters,
    "/project/node_modules/.deno/mocha@10.2.0/"... 37 more characters,
    "/project/node_modules/.deno/mocha@10.2.0/"... 31 more characters
  ]
}
```

## Steps to reproduce

1. Clone this repository
2. Run `deno run -A npm:mocha -r @babel/register`
