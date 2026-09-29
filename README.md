# Cubeship templates

This repository is the source of the templates listed at [cubeship.dev/templates](https://cubeship.dev/templates). Each directory is named with the template slug, such as `umami` or `uptime-kuma`, and contains `template.yaml`, `README.md` and a square `icon.png`. The `name` in `template.yaml` is the display name; the directory name is the stable identifier.

To add or change a template, open a pull request. CI validates every directory with Cubeship's current template validator. Once merged to `main`, the catalog reads the new commit within about five minutes. A broken commit leaves the previous catalog available.

Installed templates stay as they were. Changing a file here does not update an existing installation; change its apps directly on that Cubeship instance.

The `version: 1` field in `template.yaml` describes the file format, not a template release.
