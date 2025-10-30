# GitHub Labeler Starter Setup

This starter setup automates GitHub label management using the crazy-max [GitHub Labeler GitHub Action (v5+)](https://github.com/crazy-max/ghaction-github-labeler) that allows developers to manage and organize their GitHub labels. It GitHub Action to manage labels on GitHub (create/rename/update/delete) as code.

It helps if you are working on a fresh repository or one where you did not change any of the initial labels but you can also use it on existing repositories.

GitHub Labels are declared as code in `.github/labels.yml` and synchronized by the GitHub Actions workflow in `.github/workflows/labeler.yml`.

## Key Files
- `.github/labels.yml` — Single source of truth for labels. Fields: `name`, `description`, `color` (lowercase hex with leading `#`), optional `from_name` for renames. Keep two‑space indentation and double‑quoted strings.
- Even though it is not required by the system, this Starter uses categories that follow prefix `priority:`, `status:`, and `type:` naming (e.g., `"priority: urgent"`).
- `.github/workflows/labeler.yml` — "Manage labels" workflow. Triggers on changes to label config (PR dry‑run, push applies). Uses `crazy-max/ghaction-github-labeler@v5` with `yaml-file: .github/labels.yml` and `exclude` rules for `help*` and `*issue`.

## Deployment
- Add `.github/labels.yml` and `.github/workflows/labeler.yml` to your repository.
- Add/modify labels in `.github/labels.yml`. This Starter adds new labels and changes the "standard" labels in your repository to match the configuration in this file.
- Optionally validate the YAML: `yamllint .github/labels.yml`. Note that the GitHub Action automatically lints the YAML file during execution.
- On GitHub, visit the "Actions" tab and select the "Manage labels" workflow.
- Manually trigger the workflow using the "Run workflow" button and optionally select the branch you want to apply it to (with the expectation that it will eventually be in `main` branch).
- The workflow will run and synchronize your repository's labels with the configuration in `.github/labels.yml`.

## Disabling the Workflow after Setup
To disable the GitHub Actions workflow after setting up your labels, you can either:
- On GitHub, visit the "Actions" tab and select the "Manage labels" workflow and click on the "Disable workflow" menu item in the extras menu pulldown.
- Or, delete the `.github/workflows/labeler.yml` and `.github/labels.yml` files from your repository.

## Original GitHub Labels
- Reference defaults: [ghaction-github-labeler/samples/original.yml](https://github.com/crazy-max/ghaction-github-labeler/blob/master/samples/original.yml)

## Support

This software is provided as is and I am not implementing or accepting any support requests or contributions. Please be aware that I may or may not respond to any issue or address any issues.

> If you want to ask a question, I assume that you have read the following 2 files: [GitHub Labeler GitHub Action README.md](https://github.com/crazy-max/ghaction-github-labeler/blob/master/README.md) and this repository's [Documentation](https://github.com/DavidSchargel/github-labeler-starter/README.md).

If you then still feel the need to ask a question and need clarification, I recommend the following:

- Do a search in the GitHub Labeler GitHub Action [Open Issues](https://github.com/crazy-max/ghaction-github-labeler/issues?utf8=%E2%9C%93&q=) to see if the issue or feature request has already been filed for the software that drives this Starter.
- Do a search in this Starter's [Open Issues](https://github.com/DavidSchargel/github-labeler-starter/issues?utf8=%E2%9C%93&q=) to see if the issue has been added.
- If it pertains to the GitHub Labeler GitHub Action, create an [Issue](https://github.com/crazy-max/ghaction-github-labeler/issues/new/choose) on that repository.
- If the issue pertains to this Starter, open an [Issue](https://github.com/DavidSchargel/github-labeler-starter/issues/new).
- Provide as much context as you can about what you're running into.

## License
- [MIT](https://choosealicense.com/licenses/mit/)

## Authors
- [@crazy-max](https://www.github.com/crazy-max)
- [@DavidSchargel](https://www.github.com/DavidSchargel)
