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
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: false
---

# Update GitHub Info

Refresh the GitHub Info page of Mona's website with recent GitHub news and open a pull request for Mona to review.

## Instructions

1. Read `notes/mona-notes.md` and follow its guidance on tone, length, sourcing, and publishing.
2. Fetch https://github.blog/latest/ with web fetch.
3. Fetch https://github.blog/changelog/ with web fetch.
4. Fetch https://awesome-copilot.github.com/workflows/ with web fetch.
5. Update `site/content/github-info.md` with a short, practical summary of the most relevant recent updates. Name the source (GitHub Blog, GitHub Changelog, or Awesome Copilot workflows) for each item and keep the existing structure of the file.
6. Open a pull request with the change so Mona can review it. Never write directly to `main`.

If nothing new or relevant is found, make no changes and do not open a pull request.
