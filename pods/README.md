# pods — what /srv/mom-pods mounts

`compose.override.yml` mounts `../skins/kit/skin.css` and `../tokens/fonts/`
over the image's generic "pod" skin. In
`/srv/mom-pods/instance-template/.env`:

```sh
COMPOSE_FILE=compose.yml:/srv/mom-design-system/pods/compose.override.yml
DESIGN_SYSTEM=/srv/mom-design-system
```

Not here yet: `welcome/index.html` (Maps of Making's own welcome page) and
`instance.json` (more reserved pod names), each with its line in the
override. The files solid-css-overlay lets an instance replace:
`overlay-template/overlay/README.md` there.
