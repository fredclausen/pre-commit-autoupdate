# vrslev/pre-commit-autoupdate

GitHub action to autoupdate pre-commit hooks in pre-commit config.

## Usage

Here's example workflow that runs `pre-commit autoupdate` and creates a PR:

```yaml
name: Autoupdate pre-commit hooks

on:
  schedule:
    - cron: 0 7 * * 1

jobs:
  pre-commit-autoupdate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: vrslev/pre-commit-autoupdate@v1.0.0
      - uses: peter-evans/create-pull-request@v3
        with:
          branch: pre-commit-autoupdate
          title: "chore(deps): Update pre-commit hooks"
          commit-message: "chore(deps): Update pre-commit hooks"
          body: Update pre-commit hooks
          labels: dependencies,github_actions
          delete-branch: True
```

You can also specify extra arguments:

<!-- prettier-ignore -->
```yaml
      - uses: vrslev/pre-commit-autoupdate@v1.0.0
        with:
          extra-args: --freeze
```
