---
name: update-github-info
description: Refresh Mona's GitHub Info page with useful updates from the GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit: true
  web-fetch: {}
  github:
    mode: local
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
    draft: false
---

Read `notes/mona-notes.md` and the existing `site/content/github-info.md` before making any changes.

Use the web-fetch tool to read:

- https://github.blog/latest/
- https://github.blog/changelog/

Select only recent, relevant updates that provide practical GitHub guidance for Mona's readers. Keep the page concise and consistent with Mona's editorial notes. Ground every added claim in the fetched sources and include a direct source link for anything derived from the GitHub Blog or Changelog. Preserve useful existing content and edit only `site/content/github-info.md`.

If the sources do not support a useful, non-repetitive update, make no changes and report `noop`. Otherwise, prepare a pull request through the configured `create-pull-request` safe output for Mona to review. Include a concise summary and source links in the pull request description. Do not push changes directly or use any other write mechanism.
