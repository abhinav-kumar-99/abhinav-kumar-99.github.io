# GitHub Pages Deployment

The GitHub Actions workflow builds the Jekyll site and deploys its `_site` artifact to GitHub Pages when `main` changes or the workflow is manually dispatched.

Last updated: 2026-08-17

Related: [Project overview](../overview.md), [Repository README summary](../sources/summaries/readme.md)

## Entrypoint

`.github/workflows/jekyll.yml` is the production deployment entrypoint. It is triggered by pushes to `main` and by `workflow_dispatch`.

## Build Contract

1. The `Install Jekyll build tools` step installs ImageMagick (`convert`) for `jekyll-imagemagick` and Jupyter (`jupyter nbconvert`) for `jekyll-jupyter-notebook`.
2. `ruby/setup-ruby@v1` provisions Ruby 3.3 and installs gems through Bundler's cache-aware setup. The moving v1 major tag is intentional: the action's maintainers require it for newly supported Ruby versions on current runners.
3. `actions/configure-pages` provides the Pages base path used by `bundle exec jekyll build`.
4. `actions/upload-pages-artifact` packages the Jekyll output.
5. `actions/deploy-pages` deploys that artifact from the separate deploy job.

The Pages actions must use compatible maintained versions. The legacy artifact/deploy v2 generation is retired on GitHub.com and prevents a deployment before site content is evaluated.
