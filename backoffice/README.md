# backoffice — what /srv/mom-backoffice mounts

Once solid-backoffice ships as an image (solid-kit ADR 011): `instance.json`
here, `../skins/kit/skin.css` at `/skin.css`, and `../tokens/fonts/` at
`/fonts/skin/` (the skin's font urls, `../fonts/skin/<file>`, resolve there
from `/skin.css`), with the `compose.override.yml` that mounts them.
