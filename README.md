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

Wrangler records the ordinary Worker route `luminism.net/*`, scoped to zone
`luminism.net`. It covers apex paths and query strings while retaining the
original GitHub Pages apex A values in DNS management. The apex records must be
proxied, the zone active, and its edge certificate ready before live verification.
Native Git publishing manages this route; no custom-domain DNS replacement is
requested by this configuration.

This Worker has no `main` script. Its static assets and generated `404.html`
provide a terminal 404 for missing paths with `not_found_handling: 404-page`.
It does not fetch the retained Pages origin. That origin can become reachable
again if the route is removed or bypassed, or proxying is disabled; inspect route
conflicts and fail mode before release. Apex routing does not cover `www`.

This child change remains local for coordinator review. See [NOTES](NOTES.md)
for the custom-domain conflict and remaining deployment, DNS, certificate, HTTPS,
and path checks. Preserve all original DNS/mail values and the previous Pages
deployment/source for recovery. Manual recovery must pause automatic builds and
wait for active builds, then verify recovery before re-enabling them.

Cloudflare documents [ordinary-route prerequisites](https://developers.cloudflare.com/workers/configuration/routing/routes/)
and [static-site 404 handling](https://developers.cloudflare.com/workers/static-assets/routing/static-site-generation/).

Wrangler logs and traces are enabled, but asset-only requests bypass Worker
execution. Use Cloudflare HTTP analytics for those requests.
