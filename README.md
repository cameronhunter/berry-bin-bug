# Yarn Berry bin bug

See [issue on yarnpkg/berry](https://github.com/yarnpkg/berry/issues/882).

When a project defines a `bin` field to create a binary, yarn 2.0 seems to
expect the file to be authored in JS rather than executing it using its shebang.

Yarn `2.0.0-rc.28` is bundled in this example repo showing the issue.

```sh
$ yarn --version
2.0.0-rc.28
```

## How to reproduce

```sh
$ yarn install
$ yarn berry-bin-bug
/Users/chunter/workspace/github/cameronhunter/berry-bin-bug/bin/berry-bin-bug:3
echo "Hello world!"
     ^^^^^^^^^^^^^^

SyntaxError: Unexpected string
    at Module._compile (internal/modules/cjs/loader.js:895:18)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:995:10)
    at Module.load (internal/modules/cjs/loader.js:815:32)
    at Function.module_1.Module._load (/Users/chunter/workspace/github/cameronhunter/berry-bin-bug/.pnp.js:13519:14)
    at Function.Module.runMain (internal/modules/cjs/loader.js:1047:10)
    at internal/main/run_main_module.js:17:11
```
