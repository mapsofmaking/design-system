# backoffice — what /srv/mom-backoffice mounts

The backoffice runs from its image (`ghcr.io/nicolasdb/solid-backoffice`,
solid-kit ADR 011); `compose.override.yml` here mounts Maps of Making's part:

| Here | In the container | What |
|---|---|---|
| `instance.json` | `/instance.json` | sign in and sign up at pod.mapsofmaking.org; no upload limits (below) |
| `../skins/kit/skin.css` | `/skin.css` | the riso look, the same file as the pods |
| `../tokens/fonts/` | `/fonts/skin/` | its fonts |

`/srv/mom-backoffice/instance-template/.env` (git-ignored, no secrets):

```sh
INSTANCE_NAME=mom-backoffice
BACKOFFICE_VERSION=0.1.0
PUBLIC_URL=https://backoffice.mapsofmaking.org/
GATEWAY_NETWORK=proxy
COMPOSE_FILE=compose.yml:/srv/mom-design-system/backoffice/compose.override.yml
DESIGN_SYSTEM=/srv/mom-design-system
```

**No upload limits:** they are keyed by a pod's origin, and every pod here
is its own subdomain (`<name>.pod.mapsofmaking.org`), so no key could match
them all. Uploads over the gateway's 100 MB (`request_body max_size` in
vps-infra's `mom-pods.caddy`) get its 413, which the backoffice explains. A
wildcard key is a solid-backoffice change, not one here.

`instance.json`'s fields: solid-backoffice `src/instance.ts`. A field left
out keeps the image's default, which is pod.nicolasdb.eu's: set all three.
