# EXT-110 — Revive CI on GitHub Actions

> CI Revival · both tracks · free-form
> Rules: [ASSIGNMENT.md](../README.md) · Route: [PRODUCT.md](../PRODUCT.md)

The repository contains `.gitlab-ci.yml` — a CI pipeline from the platform the project used to live on. On GitHub it is dead weight: GitHub never executes it, so pull requests get no builds and no test runs. Figure out what the old pipeline did, and bring CI back to life on GitHub Actions. The docker-publish jobs are not needed (there is no registry to push to) — port only what earns its keep.

**Definition of Done:**
- [ ] PR description summarizes what the old GitLab pipeline did, job by job, and what was ported vs dropped (and why)
- [ ] `.github/workflows/ci.yml` exists and runs on every pull request and on pushes to `main`
- [ ] Backend job: restore, build, and run unit tests
- [ ] Frontend job: install and build
- [ ] The workflow is green on this task's own PR
- [ ] `.gitlab-ci.yml` is removed — dead config confuses the next reader
