---
name: update-github-info
description: Refresh GitHub Info with practical updates from the official GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    draft: false
    allowed-files:
      - site/content/github-info.md
---

Read `notes/mona-notes.md` and `site/content/github-info.md` first. Follow Mona's editorial guidance and preserve the page's existing practical focus and style.

Use the web-fetch tool to read both:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Identify only recent, useful updates that help developers learn GitHub faster. Verify every detail against its source, link to the relevant Blog, Changelog, or Awesome Copilot workflow page, and keep summaries short and practical. Do not add speculative, redundant, or unverified information.

Update only `site/content/github-info.md`, retaining useful existing content and integrating any new findings where they fit. If neither source has a meaningful update for the page, leave the file unchanged.

When the page has changed, use the create-pull-request safe output to open a non-draft pull request for Mona's editorial review. Summarize the updates and include the source links in the pull request description; address Mona directly. Do not commit changes directly to the default branch, merge the pull request, or modify any other file.
