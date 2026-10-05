---
name: update-github-info
description: Refresh the GitHub Info page with concise, practical updates from official GitHub sources.
model: gpt-4.1
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

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:

- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Use web fetch for the GitHub Blog, GitHub Changelog, and Awesome Copilot
workflows URLs. When consulting repository guidance or reference files, use
GitHub repository API tools rather than terminal, CLI, or sandboxed commands.

Update `site/content/github-info.md` with concise, practical updates for
readers, and include source context whenever content comes from the GitHub Blog
or GitHub Changelog. Keep changes limited to that file.

Open a pull request for Mona to review. Use a pull request title that mentions
Mona or GitHub Info. Do not write directly to `main`; rely on
`safe-outputs` with `create-pull-request`.
