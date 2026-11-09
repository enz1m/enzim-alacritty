# Fork provenance

- Upstream: [alacritty/alacritty](https://github.com/alacritty/alacritty).
- Base: `94e7c8874e526b1e67b349d9ba30ddf81669119e`
  (Alacritty 0.17.0; terminal library 0.26.0).
- Original library archive SHA-256:
  `bda177466b9524d59f1b12f0dd30b68696788e9992a7e959021c4a0ed96fcf59`.
- Branch: `enzim`.
- Terminal library license: Apache-2.0, including local modifications.

Upstream ancestry, workspace components and attribution are unchanged.
Functional changes are separate commits. Documentation, repository metadata and
the VTE source pin are maintained separately.

## Local changes

1. `Row::occupied()` exposes the written-cell bound so retained rows can avoid
   scanning unwritten cells. Consumers must still preserve non-default trailing
   backgrounds; the bound alone does not describe visible background fill.
2. `Term::input_width()` accepts a precomputed width. Ordinary character input
   delegates to the same implementation.
3. `Term::input_ascii()` writes printable ASCII in row-sized runs. Insert mode,
   non-ASCII character sets and overlapping wide characters use character input.
   Cursor, wrapping and scrolling behavior are preserved.

The bulk-input commit includes a deterministic comparison against per-character
input through wrapping, scrolling, insert mode, character sets and wide glyphs.
Upstream unit tests and reference recordings remain in the fork.

## Dependency source

The terminal library pins enzim-vte at `f5f7428ba191d725eccfb2341ec129cfa89b722c`.
The dependency uses the public GitHub source; no local checkout is required.

## Maintenance

Keep package identity `alacritty_terminal` and upstream license notices. Compare
local patches when updating, and remove them when upstream provides equivalent
behavior and consumers have migrated. Keep the VTE source pin aligned with the
bulk-input API. No app-private build limits or credentials belong in this fork.
