# enzim-alacritty

Alacritty terminal engine fork used by enzUI Terminal. Based on upstream
**alacritty_terminal 0.26.0**, with upstream history, tests and licenses retained.
The crate name remains `alacritty_terminal`.

The fork exposes the written-cell bound of a row, reuses computed character
widths, and writes printable ASCII in runs. Its VTE dependency pins the matching
[enzim-vte fork](https://github.com/enz1m/enzim-vte) to an exact commit.

The full upstream workspace is retained for provenance and maintenance. This
fork is prepared for consuming the terminal library; enzUI Terminal is a
separate application.

## Build and test the library

```sh
cargo test --locked -p alacritty_terminal
cargo check --locked -p alacritty_terminal --no-default-features
```

See [fork changes and provenance](FORK.md) and the [upstream README](README.upstream.md).
Upstream components retain their [Apache-2.0](LICENSE-APACHE) and
[MIT](LICENSE-MIT) notices; `alacritty_terminal` is Apache-2.0.

Cargo package names and versions remain compatible with upstream. Consume the
library by Git source and pin the chosen commit in application manifests and
lockfiles; this fork is not a new crates.io package.
