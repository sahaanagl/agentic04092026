---
name: Weekly Report Status
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:

permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write

engine: copilot

safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

Review the repository activity for the previous seven days and summarize it in a concise weekly status issue.

## Objective

Analyze recent repository activity and create one new issue with a short report covering:

- commits made in the last 7 days
- issues opened, closed, or updated during the same period
- pull requests opened, merged, or updated during the same period

If there is no activity at all, clearly state that no commits, issues, or pull requests were found in the last seven days.

## Instructions

1. Determine the report window as the previous 7 days relative to the current date.
2. Gather repository activity using the GitHub API or repository data available to the workflow.
3. Summarize the results in a brief, readable format with headings such as:
   - Commits
   - Issues
   - Pull requests
4. If a category has no activity, include a clear note like: "No activity in the last 7 days."
5. If the repository had overall no activity during the period, state that explicitly.
6. Create a new issue using the configured safe output and keep the content concise and factual.
7. Do not create more than one issue for this workflow run.

## Output requirements

- Write a short report suitable for an issue body.
- Include only the relevant activity from the previous seven days.
- Keep language clear and concise.
- Make no assumptions beyond the repository data.
- If there are no results, say so plainly.
