---
name: update-github-info
description: Draft practical GitHub Info website updates from official GitHub sources for Mona to review.
intent: Keep Mona's GitHub Info website current with useful, source-backed guidance for developers.
on:
  workflow_dispatch:
  schedule:
    - cron: "17 9 * * *"
permissions:
  contents: read
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before
drafting any changes. Use web-fetch to read:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update only `site/content/github-info.md` with concise, practical guidance for
developers. Include clear source context for updates based on the GitHub Blog
or GitHub Changelog, and follow Mona's editorial notes. Do not invent details
or make changes when the sources do not support a useful update.

Open a draft pull request for Mona to review, with a title mentioning Mona or
GitHub Info. Use the configured `safe-outputs` `create-pull-request`; do not
write directly to `main` or use another mechanism to create or push changes.
If there is no well-supported update, or no file change is needed, use `noop`
with a brief reason instead of opening a pull request.
