# prune_dependencies

Prune dependencies from Rust crates.

Inspect every crate in a directory and find any crates that are listed in a crate's `Cargo.toml` but
not actually used by the crate. Finds both normal dependencies and build/tesst dependencies.
