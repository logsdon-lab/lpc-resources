# `Rust`
`Rust` is a statically typed programming language known for its type/concurrency safety guarantees derived from its borrow checker.

## Setup
### Toolchain
To install the [`Rust`](https://www.rust-lang.org/tools/install) toolchain.

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

This installs Rust for your user.

### `rust-analyzer`
The de-facto LSP for rust.

First, install the extension in vscode.
* If this doesn't work, you must install the extension from the source. See https://github.com/rust-lang/rust-analyzer/issues/11558#issuecomment-2067916633.

Modify your `settings.json` with the following setting `<USER>` to your user directory:
```json
"rust-analyzer.server.extraEnv": {
    "CARGO": "${userHome}/.cargo/bin/cargo",
    "RUSTC": "${userHome}/.cargo/bin/rustc",
},
```
Restart vscode-server for the changes to take effect.
