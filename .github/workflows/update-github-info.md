---
name: update-github-info
description: Refresh the GitHub Info page with concise, practical updates from official GitHub sources.
model: gpt-5.6
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Keep Mona's GitHub Info page current with concise, practical guidance for developers.

## Instructions

1. Read `notes/mona-notes.md` and `site/content/github-info.md` using the repository tools before making any changes.
2. Use web-fetch to read both official sources:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
3. Select only recent updates and useful workflows that help developers and fit Mona's editorial angle.
4. Update only `site/content/github-info.md`. Keep summaries short and practical, and include the official source for every blog, changelog, or Awesome Copilot update.
5. Review the resulting diff for accuracy, clarity, and unnecessary changes.
6. Use the `create_pull_request` safe output to open one draft pull request containing the update for Mona to review. Do not push directly to the default branch.
