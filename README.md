# Reusable Workflows

Set of reusable workflows, as proposed in [this video](https://www.youtube.com/watch?v=lRypYtmbKMs).

## Add project to issues

[This reusable workflos](https://github.com/gabrielbdornas/reusable-workflows/blob/main/.github/workflows/add_project_to_issue.yml) was created to automate the process of vinculate [a project to a new issue](https://github.com/actions/add-to-project).

The following configurations must be done in the repo that will call this reusable workflow:

- GitHub secrets
  - PROJECT_URL; and
  - GITHUB_TOKEN, as explained [here](https://github.com/actions/add-to-project#inputs).

- Create the file `.github/workflow/add_project_to_issue.yml` with the content below:

```
# This uses a reusable workflow
name: Reusable Workflow to add a project to issues

on:
  workflow_dispatch:

jobs:
  do-it:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: gabrielbdornas/reusable-workflows/.github/workflows/add_project_to_issue.yml@main
        with:
            project-url: ${{ secrets.PROJECT_URL }}
            github-token: ${{ secrets.GITHUB_TOKEN }
```
