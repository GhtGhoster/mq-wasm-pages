# Macroquad build template for WASM with support for GitHub Pages

This repository serves as a template for projects based on the Rust
[`macroquad`](https://github.com/not-fl3/macroquad) crate.
Its intention is making WASM building, WASM bindings generation,
and readying the repository for GitHub Pages as painless as possible.

## Instructions and dependencies:

All scripts listed below are compatible with default Windows installation of
PowerShell (v6+ not required) as well as bash for Linux (scripts are polyglot)

(The bash portion of the polyglot scripts is untested, use with caution
and please report back with results or a pull request)

#### [`rename.ps1`](rename.ps1)
This script changes the internal name of the project in the files
[`src\main.rs`](src\main.rs),
[`Cargo.toml`](Cargo.toml), and
[`index.html`](index.html)
to match the name of the repository, and allows `cargo` to work correctly.

(This is only necessary to run once after a repository was first created with the
[`mq-wasm-pages`](https://github.com/GhtGhoster/mq-wasm-pages) template.) 

#### [`setup.ps1`](setup.ps1)
This script installs `wasm-bindgen-cli`, `basic-http-server`
and adds `wasm32-unknown-unknown` to possible compilation targets.

(This is only necessary to run once on a single computer as the effects
of this script are global.)

#### [`build.ps1`](build.ps1)
This script builds the project for the `wasm32-unknown-unknown` target in
`--release` mode, generates WASM bindings, and patches the generated JavaScript
file. It also moves the relevant files to their appropriate directories
in preparation for running the project on a local server or on GitHub Pages.

#### [`run.ps1`](run.ps1)
This script hosts the built project on a local `basic-http-server`
server and opens a browser at its location.

(One does not need to restart the server after building the project again,
reloading the webpage in the browser is sufficent.)

(This is necessary over just opening the [`index.html`](index.html)
file in your browser so that the required resources load properly.)

## License

Licensed under either of

- Apache License, Version 2.0
  ([LICENSE-APACHE](LICENSE-APACHE) or https://www.apache.org/licenses/LICENSE-2.0)
- MIT license
  ([LICENSE-MIT](LICENSE-MIT) or https://opensource.org/licenses/MIT)

at your option.

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
