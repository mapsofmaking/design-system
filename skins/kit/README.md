# skins/kit — Maps of Making on solid-kit's slots

`skin.css` (to write) maps `../../tokens/` onto the slots solid-kit's
`src/styles/core.css` declares, for every image built on the kit: the pod
server's pages (solid-css-overlay) and the backoffice. Check it with
solid-kit's `npm run audit -- --skin <this folder>/skin.css`.

Never map a `state-*` token or `green` onto a slot: they mean how alive a
space is, and nothing in the kit's pages means that.
