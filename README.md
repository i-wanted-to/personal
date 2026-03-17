# Personal repository

The primary goal in this repository is to maximize enjoyment by minimizing complexity.

To achieve this goal, there are some strict rules. This repository contains:

- A single programming language throughout (including builds, deployment, utilities, and "scripts")

- A single workspace containing all projects, ensuring IDE operations take effect across the entire codebase at once (e.g. renaming symbols, finding all references, etc.)

- No libraries or source authored by 3rd parties

- No dependencies on any libraries or source outside this repository except the Rust standard library

- No use of any tools, shell commands, or paths outside this repository except for the current stable version of Rust

- No internet use when building

- No nesting of projects, ensuring every crate can be found in the same place

- No custom commands, setup steps, or specific ordering required to build/run any project. From a fresh clone of the repo, and at any time after:
  - Each project is run with just `cargo run`
  - Each project is built with just `cargo build`
  - Each project is cross-compiled with just `cargo build --target [architecture]`

This repository's programming language is Rust, and has some language-specific rules:

- No procedural macros

- No use of Cargo "features", ensuring each crate is referenced the same way

- No `unsafe` code, conditional compilation, or invocation of platform APIs except:
  - The `wasm` crate may invoke browser APIs
  - The `socket` crate may invoke host OS APIs until non-blocking sockets are exposed via the Rust standard library

- No disabling/ignoring of any compiler warnings

- No linter warnings generated from clippy, with the following settings:
  - Aggressive enforcement
    - Global mode: `pedantic`
  - No use of the `as` operator to convert values (outside the `cast` crate, see below)
    - Global deny: `as_conversions`
  - No requirement for public documentation:
    - Global allow: `missing_safety_doc`
    - Global allow: `missing_errors_doc`
    - Global allow: `missing_panics_doc`
  - The `cast` crate may disable data conversion warnings for type casting, allowing the following on specific lines:
    - `as_conversions`
    - `cast_sign_loss`
    - `cast_possible_wrap`
    - `cast_possible_truncation`
    
Together, these rules allow me to work in a single language for any task, on any development machine that supports Rust, using a single IDE instance that inspects, builds, and updates the entire codebase at once.

This simplcity also speeds up development. The consistent code style makes it easy to move around the codebase, and the simple build structure makes builds acceptably fast.

