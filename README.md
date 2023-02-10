# Reusable Workflows

Set of reusable workflows, as proposed in these YouTube videos:

- [GitHub Actions Reusable Workflows FULL TUTORIAL with Examples: Templates on Steroids](https://www.youtube.com/watch?v=lRypYtmbKMs)
- [GitHub Actions - Calling Reusable Workflows](https://www.youtube.com/watch?v=2dxmvDL1gP8)

When a reusable workfows is created its documentation must be added below and the secrets must be well designed to avoid ["invalid secret, is not defined in the referenced workflow"](https://github.com/orgs/community/discussions/26749).

## Add project to issues

[This reusable workflos](https://github.com/gabrielbdornas/reusable-workflows/blob/main/.github/workflows/add_project_to_issue.yml) was created to automate the process of vinculate [a project to a new issue](https://github.com/actions/add-to-project).

The following configurations must be done in the repo that will call this reusable workflow:

- GitHub secrets as explained [here](https://github.com/actions/add-to-project#inputs):
  - PROJECT_URL; and
  - GITHUB_TOKEN.

- Create the file `.github/workflow/add_project_to_issue.yml` with the content below:

```
# This uses a reusable workflow
name: Reusable Workflow to add a project to issues

on:
  issues:
    types: [opened]

jobs:
  do-it:
    uses: gabrielbdornas/reusable-workflows/.github/workflows/add_project_to_issue.yml@main
    secrets:
        PROJECT_URL: ${{ secrets.PROJECT_URL }}
        GH_TOKEN: ${{ secrets.GH_TOKEN }}
```
