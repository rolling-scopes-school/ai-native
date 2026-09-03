# EXT-110: Revive CI on GitHub Actions

> CI revival | Both tracks | Free-form
>
> Rules and route: [README.md](../README.md)

The repository still contains `.gitlab-ci.yml` from its previous hosting setup. GitHub does not run that pipeline, so Pull Requests currently have no automated build or test checks.

Review the old pipeline and recreate the relevant build and test jobs with GitHub Actions. Do not port Docker publishing jobs because this pilot has no registry.

## Definition of done

- [ ] Summarize every old GitLab job in the Pull Request description and state what was ported or removed, with the reason
- [ ] Add `.github/workflows/ci.yml`
- [ ] Run the workflow on every Pull Request and on pushes to `main`
- [ ] Backend CI restores dependencies, builds the backend, and runs unit tests
- [ ] Frontend CI installs dependencies and builds the frontend
- [ ] The workflow is green on this task's Pull Request
- [ ] Remove `.gitlab-ci.yml`
