# esbuild

This is the cross-platform WebAssembly binary for esbuild, a JavaScript bundler
and minifier. See https://github.com/evanw/esbuild and the
[JavaScript API documentation](https://esbuild.github.io/api/) for details.

## Description

`@spike-land-ai/esbuild-wasm` provides the esbuild API backed by a WASM binary,
enabling use in browsers and any environment that cannot run native esbuild
binaries. It is a drop-in replacement for the official `esbuild-wasm` package,
published under the `@spike-land-ai` scope to GitHub Packages.

## Installation

```bash
npm install @spike-land-ai/esbuild-wasm
```

> **Note:** This package is published to GitHub Packages. You must authenticate
> with the registry and set the scope in your `.npmrc`:
>
> ```
> @spike-land-ai:registry=https://npm.pkg.github.com
> ```

## Usage

### Node.js

```js
import * as esbuild from "@spike-land-ai/esbuild-wasm";

await esbuild.initialize({});

const result = await esbuild.transform("const x: number = 1", {
  loader: "ts",
});

console.log(result.code); // "const x = 1;\n"
```

### Browser

```js
import * as esbuild from "@spike-land-ai/esbuild-wasm/browser";

await esbuild.initialize({
  wasmURL: "/path/to/esbuild.wasm",
});

const result = await esbuild.transform("let x: number = 1", {
  loader: "ts",
});

console.log(result.code);
```

## WASM Binary

The `esbuild.wasm` binary is auto-generated from the esbuild source at version
**0.27.3**. It is not compiled in this repository — it is vendored directly from
the upstream [esbuild](https://github.com/evanw/esbuild) release.

See `WASM_CHECKSUMS.md` for integrity verification instructions.

## Links

- [esbuild documentation](https://esbuild.github.io/api/)
- [esbuild GitHub](https://github.com/evanw/esbuild)
- [JavaScript API reference](https://esbuild.github.io/api/#js-specific-details)
