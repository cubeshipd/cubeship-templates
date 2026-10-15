# Cubeship templates

This repository is the source of the templates listed at [cubeship.dev/templates](https://cubeship.dev/templates). Each directory is named with the template slug, such as `umami` or `uptime-kuma`, and contains `template.yaml`, `README.md` and a square `icon.png`. The `name` in `template.yaml` is the display name; the directory name is the stable identifier.

To add or change a template, open a pull request. CI validates every directory with Cubeship's current template validator. Once merged to `main`, the catalog reads the new commit within about five minutes. A broken commit leaves the previous catalog available.

Renovate checks image tags in `template.yaml` and base images in each template's Dockerfiles, opening pull requests for updates. Source-built apps use this repository with `ref: main:<directory>`; the installer pins that ref to the cataloged commit. Managed database versions stay tied to the versions Cubeship supports.

Installed templates stay as they were. Changing a file here does not update an existing installation; change its apps directly on that Cubeship instance.

The `version: 1` field in `template.yaml` describes the file format, not a template release.

## Publishing the catalog

On pushes to `main`, the workflow runs Cubeship's `core/tools/templatecatalog`
against this committed tree. All folders must validate before it commits
`_catalog/snapshot.json`. The snapshot records the source commit and includes
normalized manifests, source YAML, READMEs and sanitized PNG icons.

cubeship.dev reads that publication on demand (once per minute), keeps its last
valid copy during failures, and serves the public API. Template changes do not
require a site deployment. A publication-only commit does not retrigger the job.
The workflow needs permission to push its generated commit to `main`; if branch
rules reject it, the old catalog remains live until publication succeeds.

To generate locally from a Cubeship checkout:

```sh
make catalog TEMPLATES_DIR=../cubeship-templates
```

The generator reads committed files; commit template edits before publishing.
To validate uncommitted files, run the existing `templatecheck` tool instead.
