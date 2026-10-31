# skins/kit — Maps of Making on solid-kit's slots

`skin.css` (to write) maps `../../tokens/` onto the slots solid-kit's
`src/styles/core.css` declares, for every image built on the kit: the pod
server's pages (solid-css-overlay) and the backoffice. Check it with
solid-kit's `npm run audit -- --skin <this folder>/skin.css`.

Never map a `state-*` token or `green` onto a slot: they mean how alive a
space is, and nothing in the kit's pages means that.

Fonts: `../../tokens/fonts/`, mounted by each image at `fonts/skin/` beside
its styles (overlay: `/.well-known/css/fonts/skin/`, backoffice:
`/fonts/skin/`).

Open: the kit's theme button offers Dark; the skin repeats paper there
(riso paper only). Mapping Depth instead, or hiding the button on a
one-theme skin, is a later choice.

Open: focus. The design system's focus ring is cobalt (`accent-2`, 2026-10-31),
but the kit draws focus with `--accent`, the same slot as links and primary
actions, which this skin sets to ink. Kit screens keep an ink ring until
solid-kit offers a focus slot of its own (ADR 011: ask for a slot, don't
override a component).
