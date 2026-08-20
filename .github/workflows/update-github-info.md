---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions: read-all
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[mona] "
---

# Update GitHub Info

Keep Mona's GitHub Info page current with concise, practical updates for developers.

1. Read `notes/mona-notes.md` before making any changes.
2. Use the GitHub repository API tools to read repository guidance and any relevant reference files. Do not use terminal, CLI, or sandboxed commands for repository guidance or reference-file reads.
3. Web fetch `https://github.blog/latest/` and `https://github.blog/changelog/`.
4. Review the fetched material and select only useful, current items that fit Mona's editorial angle. Cite the source for every update that comes from the GitHub Blog or GitHub Changelog.
5. Update `site/content/github-info.md` with short, practical content. Preserve the existing structure and avoid unrelated edits.
6. Review the diff for accuracy, relevance, and unnecessary changes.
7. After making a meaningful update, use the `create-pull-request` safe output to open a draft pull request for Mona to review. Include a concise title and explain which GitHub sources informed the changes. Do not write directly to `main` and do not request a pull request when no meaningful update is needed.
