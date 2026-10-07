The audit needs a Rust toolchain and two small tools to demangle and list symbols. Each step is a condition, checked from the repo the bot will work in.

1. **Rust is installed.** Confirm with `cargo --version`. If absent, the user should install rustup from rustup.rs and run `rustup default stable`.

2. **rustfilt is installed** (demangles v0 symbols for the diff). Confirm with `rustfilt --version`. If absent: `cargo install rustfilt`.

3. **A symbol lister is available.** Confirm with `which nm` or, on Windows, `where llvm-nm`. If neither exists, install llvm-tools via `rustup component add llvm-tools` (its `llvm-nm` is auto-detected on PATH, or at `$(rustc --print sysroot)/lib/rustlib/<target-triple>/bin/`).

4. **The rust-symbol-audit tool is available** (the local audit runner). Confirm by checking whether `.github/workflows/pr-audit.yml` exists in the repo, or whether `rust-symbol-audit` is on PATH. If neither, the bot can still review changes by reading Cargo.lock and the crate sources directly — tell the user that, and offer the GitHub Action setup if they want the automated lane: copy the workflow from github.com/Booyaka101/rust-symbol-audit/blob/main/examples/pr-audit.yml.
