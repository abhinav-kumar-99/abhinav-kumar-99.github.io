# Maintenance Log

Chronological record of durable repository maintenance findings.

## [2026-08-17] initialize | Website deployment documentation

Touched files: `docs/wiki/index.md`, `docs/wiki/overview.md`, `docs/wiki/workflows/github-pages.md`, `docs/wiki/sources/summaries/readme.md`.

Initialized repository wiki from `_config.yml`, `Gemfile`, `README.md`, and `.github/workflows/jekyll.yml`. Recorded the GitHub Pages build-and-deploy contract and the retired legacy Pages action generation found in the workflow.

## [2026-08-17] debug | Ruby setup action compatibility

Touched files: `.github/workflows/jekyll.yml`, `docs/wiki/workflows/github-pages.md`.

The GitHub Actions log archive `logs_86893887983.zip` showed that the pinned `ruby/setup-ruby` commit rejected Ruby 3.3 on `ubuntu-24.04`. Updated the action to its maintained `@v1` reference, as the action documentation and its own failure message require for current Ruby version support.
