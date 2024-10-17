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

Modify your `settings.json` with the following setting `<USER>` to your user directory:
```json
"rust-analyzer.server.extraEnv": {
    "CARGO": "/home/<USER>/.cargo/bin/cargo",
    "RUSTC": "/home/<USER>/.cargo/bin/rustc",
},
```
Restart vscode-server for the changes to take effect.
