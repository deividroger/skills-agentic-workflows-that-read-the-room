---
name: update-github-info
description: Updates the GitHub Info page from the GitHub Blog and Changelog and opens a pull request for Mona to review.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
timeout-minutes: 15
---

# Update GitHub Info

Update the GitHub Info page with recent news from GitHub, then open a pull request for Mona to review.

## Instructions

1. Read `notes/mona-notes.md` and follow its guidance on tone, length, and sourcing.
2. Fetch https://github.blog/latest/ with web fetch.
3. Fetch https://github.blog/changelog/ with web fetch.
4. Update `site/content/github-info.md` with short, practical summaries of the most relevant new items. Name the source (GitHub Blog or GitHub Changelog) and link to each item.
5. Do not change any other file.
6. Open a pull request with your changes using the `create-pull-request` safe output so Mona can review them. Never write directly to `main`.

If there is nothing new worth adding, make no changes and do not open a pull request.
