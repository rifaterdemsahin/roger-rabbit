# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

`roger-rabbit` is a small content repository, not an application. It holds Markdown notes and media assets (images, video) about animation-related topics (Roger Rabbit, La Linea). There is no build system, package manager, source code, or test suite — the repo's content files are deployed as-is.

## Deployment

`.github/workflows/static.yml` deploys the entire repository as static content to GitHub Pages on every push to `main` (or via manual `workflow_dispatch`). It uses `actions/upload-pages-artifact` with `path: '.'`, so the whole repo root is published verbatim — there is no build/compile step.

To verify a deployment, check the Actions tab or the `github-pages` environment URL in the workflow run output.

## Working in this repo

- Content lives in root-level `.md` files (e.g. `README.md`, `La_Linea.md`); add new topic notes the same way.
- Media files (images, video) are committed directly to the repo root alongside the notes that reference them.
- Since the whole repo is published as-is, avoid committing files that shouldn't be publicly served.
