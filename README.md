# GitHub Labeler Starter Setup

This starter setup automates GitHub label management using the crazy-max [GitHub Labeler GitHub Action (v5+)](https://github.com/crazy-max/ghaction-github-labeler) that allows developers to manage and organize their GitHub labels. It GitHub Action to manage labels on GitHub (create/rename/update/delete) as code.

It helps if you are working on a fresh repository or one where you did not change any of the initial labels but you can also use it on existing repositories.

GitHub Labels are declared as code in `.github/labels.yml` and synchronized by the GitHub Actions workflow in `.github/workflows/labeler.yml`.

## Key Files
- `.github/labels.yml` — Single source of truth for labels. Fields: `name`, `description`, `color` (lowercase hex with leading `#`), optional `from_name` for renames. Keep two‑space indentation and double‑quoted strings.
- Labels are organized into categories with prefixes: `priority:`, `status:`, and `type:` (e.g., `"priority: urgent"`), plus special labels like `github_actions`.
- `.github/workflows/labeler.yml` — "Manage labels" workflow. Manually triggered via `workflow_dispatch`. Uses `crazy-max/ghaction-github-labeler@v5` with `yaml-file: .github/labels.yml` and `exclude` rules for `help*` and `*issue`.

## Deployment
- Add `.github/labels.yml` and `.github/workflows/labeler.yml` to your repository.
- Add/modify labels in `.github/labels.yml`. This Starter adds new labels and changes the "standard" labels in your repository to match the configuration in this file.
- Optionally validate the YAML: `yamllint .github/labels.yml`. Note that the GitHub Action automatically lints the YAML file during execution.
- On GitHub, visit the "Actions" tab and select the "Manage labels" workflow.
- Manually trigger the workflow using the "Run workflow" button and select the branch you want to apply it to (recommended to run on `main` branch).
- The workflow will run and synchronize your repository's labels with the configuration in `.github/labels.yml`.

## Label Categories

### Priority Labels
- `priority: urgent` — Critical work or bug that is holding up other things
- `priority: high` — Important features or user-visible bugs that should be done soon
- `priority: medium` — Should be done but isn't prioritised ahead of others
- `priority: low` — Not important and unlikely to be done unless it becomes important

### Status Labels
- `status: blocked` — Blocked by another issue or external requirement
- `status: bot` — Assigned to a bot
- `status: duplicate` — Indicates similar issues, pull requests, or discussions
- `status: cooking` — WIP changes that are being actively worked on
- `status: good first issue` — A good issue for first-time contributors
- `status: help wanted` — Help requested for an issue or pull request
- `status: invalid` — This doesn't seem right
- `status: wontfix` — This will not be worked on
- `status: on hold` — Other issues are taking priority

### Type Labels
- `type: bug` — Something isn't working
- `type: ci & build` — Related to build or continuous integration files and scripts
- `type: dependencies` — Referring to or updating a dependency file
- `type: 3rd party` — Regarding a 3rd party API/script/package/dependency
- `type: a11y` — Accessibility-related issues or improvements
- `type: i18n` — Internationalization-related issues or improvements
- `type: documentation` — Improvements or additions to documentation
- `type: enhancement` — New enhancement or improvement
- `type: feature` — New feature request
- `type: repo prompt` — New feature request
- `type: question` — Further information is requested or needed

### Special Labels
- `github_actions` — Pull requests that update GitHub Actions code or configuration

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
