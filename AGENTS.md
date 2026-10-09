# AGENTS

## 🔄 Self-Improvement Directive
- Update this file whenever you learn something useful: working commands, pitfalls, collaborator preferences, and content style notes.
- Capture both wins and missteps so future agents can repeat successes and avoid dead ends.
- Be specific: include exact commands, file paths, and examples rather than vague guidance.

## Project Overview
- Luminism knowledge base and whitepaper built with MkDocs + Material theme.
- Primary content lives in `docs/`; navigation is defined in `mkdocs.yml`.

## Build & Test Commands
- `source activate.sh` (creates/activates venv and installs deps)
- `mkdocs serve` (preview locally; also available via `serve.sh`)
- `mkdocs build` (static build; also available via `build.sh`)

## Project Structure
- `docs/`: Markdown source content.
- `mkdocs.yml`: site configuration and navigation.
- `site/`: generated output from `mkdocs build` (do not edit by hand).
- `requirements.txt`: Python dependencies (mkdocs-material).
- `activate.sh`, `serve.sh`, `build.sh`: helper scripts for env setup and build/serve.

## Coding Conventions
- Write in clear Markdown with a unifying, forward-looking Luminism tone focused on decentralizing power and balancing individual freedom with collective welfare.
- Use section headings that map to navigation; update `mkdocs.yml` when adding or moving pages.
- Prefer precise terminology (e.g., “Luminism”) and avoid unnecessary jargon.

## Agent Profile: Halima
- Role: Guides the creation and curation of this knowledge base.
- Principles: Adheres to the tenets of Luminism,decentralizing power, balancing individual freedom with collective welfare, and favoring transparent, verifiable systems.
- Interaction: Engages in friendly, good-faith debate on Luminism specifics; asks clarifying questions; surfaces trade-offs and edge cases.
- Curation stance: Prioritizes accuracy, cites sources when available, flags ambiguity, and keeps content cohesive with the broader Luminism narrative.

## Known Issues & Tips
- Use the existing authenticated GitHub CLI/HTTPS remote for Git operations; verify `gh auth status` if authentication fails.
- Always run `source activate.sh` before serving or building to ensure dependencies are installed.
- Avoid editing `site/` directly; regenerate via `mkdocs build`.

## Rapport & Reflection
- Collaborator prefers concise responses and opted not to link AGENTS.md from docs.
- When adjusting prose, call out spelling and wording fixes explicitly; prior requests included quick spellchecks and direct commits.
- Copy guidance: favor “Luminism”/“Luminist” consistently, keep sections scannable (short paragraphs, subheads), and trim overly verbose passages like we did for the quadratic voting/funding page.
- Keep the existing HTTPS remote and resolve GitHub CLI authentication rather than changing transport during deployment work.

## Cloudflare migration lessons (2026-10-09)

- Worker `luminism` publishes only `.cloudflare/site/`, leaving legacy `site/` untouched. Use `npm ci`, `npm run build`, and `npm run deploy:check`; strict MkDocs uses the baseline renderer versions in `requirements.lock`.
- Native Git settings: `pierce403/luminism`, production `main`, root `/`, build `npm run build`, deploy `npx wrangler deploy`, paths `*`. GitHub Actions validates only; credentials stay in Cloudflare, with no GitHub Cloudflare secrets.
- Wrangler records the ordinary route `luminism.net/*` with `zone_name: luminism.net`. Retain the original apex A values and all mail/TXT/unrelated records; proxying the apex must send traffic through Cloudflare. The coordinator owns the reviewed push and live changes. Verify the active zone, edge certificate, exact native build, HTTPS, paths, and any separate `www` behavior.
- Keep this configuration without `main` or `run_worker_first`: generated root `404.html` and `not_found_handling: 404-page` produce terminal missing-page responses. There is no application fetch of the Pages origin. Route bypass/removal, proxy disablement, or a changed fail mode can expose the retained origin and require review.
- Preserve canonical URL, existing public paths and standalone HTML, search, feeds, robots behavior, unrelated DNS/mail records, and prior Pages recovery source. Asset-only requests do not emit Worker invocation logs.
- Do not overlap manual and native Git deployment. Pause automatic builds and wait before deliberate recovery; verify before re-enabling them.

- Compatibility date is `2026-10-07`, the newest date supported by the bundled workerd in pinned Wrangler 4.145.0. A `2026-10-09` local runtime refused startup; this asset-only configuration uses the supported date so development and validation exercise the configured runtime. Review compatibility changes before advancing it with a future Wrangler update.
