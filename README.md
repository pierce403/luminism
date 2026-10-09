# Luminism

This repo hosts the Luminism whitepaper and knowledge base built with MkDocs + Material.

## Getting started
- `source activate.sh` to create/activate the virtual environment and install dependencies.
- `mkdocs serve` to run a local preview (or use `serve.sh`).
- `mkdocs build` to generate the static site (or use `build.sh`).

## Project layout
- `docs/`: Markdown source for the site.
- `mkdocs.yml`: Navigation and theme configuration.
- `site/`: Generated output from `mkdocs build` (do not edit directly).

## Cloudflare publishing

The `luminism` Worker is prepared to serve only `.cloudflare/site/` with
Workers Static Assets. The strict build uses a complete version-pinned Python
renderer and locally pinned Wrangler 4.145.0. Original `site/`, content, canonical
`https://luminism.net`, page paths, search, feeds where configured, and `docs/CNAME`
remain preserved for recovery. The isolated output avoids modifying tracked
legacy generated files. No robots policy was added or changed.

```bash
npm ci
npm run build
npm run deploy:check
npm run dev
```

Configure Cloudflare Workers Builds for `pierce403/luminism`, production `main`,
root `/`, build `npm run build`, deploy `npx wrangler deploy`, and included paths
`*`. Once connected, a validated commit pushed to `main` lets Cloudflare fetch,
build, and deploy. Cloudflare retains its deployment credential; no Cloudflare
secrets belong in GitHub. `.github/workflows/deploy.yml` now validates and saves a
build artifact only, with no Pages or Cloudflare deployment step.

Git connection, workers.dev serving, custom-domain attachment, and registrar
cutover require separate live verification. Initial Wrangler configuration has no
custom routes; attach only the exact intended domain after its zone is ready and
DNS preservation is verified. Keep the prior GitHub Pages deployment/source for
rollback. Manual recovery must pause automatic builds and wait for active builds;
verify recovery before re-enabling them.

Wrangler logs and traces are enabled, but asset-only requests bypass Worker
execution. Use Cloudflare HTTP analytics for those requests.
