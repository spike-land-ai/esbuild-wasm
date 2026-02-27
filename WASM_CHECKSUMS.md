# WASM Binary Checksums

These checksums are used to verify the integrity of the esbuild WASM binary.

## esbuild.wasm

Generated from: [esbuild](https://github.com/evanw/esbuild)

To verify:
```bash
shasum -a 256 esbuild.wasm
```

Note: The checksum should be verified when updating the WASM binary.
Update this file after each binary update.
