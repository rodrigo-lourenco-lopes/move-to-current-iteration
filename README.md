# Move to next iteration

Automatically move issues and pull requests to the next iteration of your [GitHub project](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects) with this [Github Action](https://github.com/features/actions).

## Example

```yml
on:
  schedule:
    # Runs "at 05:00, only on Monday" (see https://crontab.guru)
    - cron: '0 5 * * 1'

jobs:
  move-to-next-iteration:
    name: Move to next iteration
    runs-on: ubuntu-latest

    steps:
    - uses: blombard/move-to-next-iteration@master
      with:
        owner: OrgName
        number: 1
        token: ${{ secrets.PROJECT_PAT }}
        iteration-field: Iteration
        new-iteration: current
        statuses: Todo,In Progress,In Review
```

## Inputs
#### owner
The account name of the GitHub organization.

#### number
Project number as you see it in the URL of the project.

#### token
Personal access token or an OAuth token. the `project` scope is required.

#### iteration-field
The name of your iteration field.

#### new-iteration
Should be `current` or `next`.

#### statuses
Statuses of the issues to move to the next iteration.

⚠️ _Don't put an empty string after a comma unless the status starts with an empty string._ ⚠️

## Sources

This action was made possible thanks to https://github.com/gr2m/github-project.
