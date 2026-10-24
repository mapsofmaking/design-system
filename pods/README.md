# pods — what /srv/mom-pods mounts

The files solid-css-overlay's `overlay-template/overlay/README.md` lists
(`skin.css` from `../skins/kit/`, fonts, `welcome/index.html`,
`instance.json`), and the `compose.override.yml` that mounts them. In
`/srv/mom-pods/instance-template/.env`:

```sh
COMPOSE_FILE=compose.yml:/srv/mom-design-system/pods/compose.override.yml
```

Empty until the kit skin exists: the pods run the image's generic skin.
