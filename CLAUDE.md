# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

`roger-rabbit` is a small content repository, not an application. It's an experiment in recreating the Roger Rabbit-style toon-meets-live-action look using [Google Flow](https://labs.google/flow) (Google's AI filmmaking tool), with [La Linea](https://en.wikipedia.org/wiki/La_Linea_%28TV_series%29)'s minimalist line-drawn animation as a second style reference. There is no build system, package manager, source code, or test suite — the repo's content files are deployed as-is.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The live landing page (served at the site root). Explains the project goal and embeds the example video/image. Self-contained — no external CSS/JS deps, light/dark aware. |
| `README.md` | Repo homepage on GitHub. Explains the goal, links to the live site, and gives background on the source material (*Who Framed Roger Rabbit*). |
| `La_Linea.md` | Background reference on the La Linea animated series (second style reference for the project). |
| `man-typing-on-laptop-line.mp4`, `roger-rabbit-trials.png` | Example media generated for the project. Keep filenames kebab-case / web-safe (no spaces or commas) since they're served directly by GitHub Pages. |

## Deployment

`.github/workflows/static.yml` deploys the entire repository as static content to GitHub Pages on every push to `main` (or via manual `workflow_dispatch`). It uses `actions/upload-pages-artifact` with `path: '.'`, so the whole repo root is published verbatim — there is no build/compile step. Live at https://rifaterdemsahin.github.io/roger-rabbit/.

Important: this is the plain static-content workflow, not the Jekyll-based Pages build, so `.md` files are **not** rendered to HTML when served — visiting a `.md` URL on the live site returns raw markdown text. Because of this, `index.html` links to `README.md`/`La_Linea.md` point at their GitHub blob view (`github.com/.../blob/main/...`), not the Pages-hosted `.md` file, so they render properly.

To verify a deployment, check the Actions tab or the `github-pages` environment URL in the workflow run output.

## Working in this repo

- Content lives in root-level `.md` files; add new topic notes the same way, and cross-link them from `README.md`.
- Media files (images, video) are committed directly to the repo root alongside the notes/pages that reference them.
- Since the whole repo is published as-is, avoid committing files that shouldn't be publicly served.
- Keep `index.html` and `README.md` in sync when the project goal or file list changes — both explain the same goal to different audiences (site visitors vs. GitHub browsers).
