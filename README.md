# Maps of Making — design system

Maps of Making's look, in one place: the riso zine laid over a map. Every
Maps of Making surface takes its look from here: the map, the landing, the
pods, the backoffice, and whatever comes next. Nothing else is a source.
Decided 2026-10-24 (solid-kit ADR 011).

| Path | What | Who reads it |
|---|---|---|
| `tokens/` | the tokens (`tokens.json`, `tokens.css`), the component styles (`components.css`), fonts, logos, in Maps of Making's own names (`paper`, `ink`, `rule`, `state-*`) | the map, the landing: they import them |
| `tokens/workbench.css`, `workbench.md` | the Workbench: hex view, step panel, HexRow toolbar, TilePicto, WordChip, Copyable, Finder (`wb-`/`hx-`/`fd-`), and the rules they follow | the home app ([mom-home](https://github.com/mapsofmaking/mom-home)), which pins a commit of this repo |
| `skins/kit/skin.css` | the same look mapped onto solid-kit's slots (`--surface`, `--text-*`, `--border`, `--accent`, ...) | every image built on solid-kit: the pods (solid-css-overlay), the backoffice |
| `pods/` | what the pod server mounts: welcome page, `instance.json`, `compose.override.yml` | `/srv/mom-pods` |
| `backoffice/` | what the backoffice mounts: `instance.json`, `compose.override.yml` | `/srv/mom-backoffice` |

## The rules

- **Change a value here first.** The map, the claude.ai design system
  ("Maps of Making") and the skin follow. A value changed in the map's own CSS
  is drift, and the next sync overwrites it.
- **State colour is protected meaning.** The `state-*` tokens and `green` say
  how alive a space is: never decoration, branding or emphasis, and never
  mapped onto a kit slot. The README of the claude.ai design system holds the
  full principles; they move here with the first sync.
- **The kit's slot set is the contract** with the images. `skins/kit/skin.css`
  fills the **complete** set in every theme it offers and passes solid-kit's
  `npm run audit -- --skin skins/kit/skin.css`. A missing slot shows as the
  kit's default look, not as an error.
- **No secrets, no instance values that are secret.** What a function mounts
  from here is public: this repo is.

## On the VPS

One checkout, beside the functions that use it:

```sh
git clone https://github.com/mapsofmaking/design-system /srv/mom-design-system
```

Each function points its compose at its folder here, in its own git-ignored
`.env` (the folder's README says which lines). **A change of look** is a commit
here, then `git pull` in `/srv/mom-design-system` and `docker compose up -d`
in each function's folder. No image is rebuilt.

## Where it came from

`tokens/` was taken on 2026-10-24 from the claude.ai design system "Maps of
Making", itself extracted on 2026-10-13 from the live map
(`nicolasdb/maps_of_making@mom-demo`: `web/maps-of-making.html`, `web/app.js`
LADDER, `web/genjson/`). From now on the direction is the other way: the map
imports `tokens/tokens.css`.

## Not here yet

- Maps of Making's own welcome page and words for the pods (`pods/welcome/`).
- Bernard's illustrations stay in the map's repo (`web/mothersands/`) until a
  second surface uses them.
- Special Elite's licence file (Apache 2.0, Google Fonts) beside its woff2.
