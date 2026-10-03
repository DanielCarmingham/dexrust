# dex-cli has moved to dexrust

This package is retired. Install [`dexrust`](https://crates.io/crates/dexrust)
instead:

```bash
cargo install dexrust
```

`dex-cli` 0.1.3 is a temporary compatibility release for existing users. It
delegates to `dexrust` 0.2.0 and still installs the former `dex` and `dexrs`
binary names. New scripts and installations should use `dexrust`; the `dex`
compatibility binary is also included in that package.
