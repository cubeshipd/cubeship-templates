# Cubeship templates — compatibility archive

Templates are now maintained in [cubeshipd/cubeship/templates](https://github.com/cubeshipd/cubeship/tree/master/templates).
Open new contributions and dependency updates there.

This repository retains historical manifests and build contexts for existing
Cubeship installations and the frozen `/api/v1` catalog. Its contents and Git
history must remain available: old daemons fetch manifests here, and installed
source-built apps may need these commits for future redeploys.

`_catalog/snapshot.json` is the last legacy publication. Do not regenerate it
with the new monorepo generator. The active catalog is published independently
from the main Cubeship repository and served at `https://cubeship.dev/api/v2`.

Archive this repository only after the new site and daemon have been deployed
and both API versions verified. Do not delete it or rewrite its history.
