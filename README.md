# stickler.docs

Documentation for [`gomatic/stickler`](https://github.com/gomatic/stickler) — a standalone Go linter that enforces the gomatic Go Code Quality Standards (structural/layout conformance plus the bespoke rules off-the-shelf linters don't cover). The source repository carries only a minimal `README.md`; everything else lives here. Follows [`nicerobot/template.docs`](https://github.com/nicerobot/template.docs).

## Layout

| Path | Purpose |
|------|---------|
| [`content/`](content/) | Public-facing documentation — Markdown for this self-contained [Hugo](https://gohugo.io) site, rendered by GitHub Pages **if** the repository is made public and Pages is enabled. |
| [`.github/workflows/pages.yml.disabled`](.github/workflows/pages.yml.disabled) | The GitHub Pages build workflow, **disabled** by its `.disabled` suffix (GitHub Actions only runs `*.yml`). |
| [`Makefile`](Makefile) | Local preview and build of the site. Run `make` for help. |

## Going public

When the repository is made public:

1. Enable Pages: **Settings → Pages → Source: GitHub Actions**.
2. Activate the workflow: `git mv .github/workflows/pages.yml.disabled .github/workflows/pages.yml`
3. Push. The site builds from the repository root.
