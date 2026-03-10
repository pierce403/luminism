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
- Git push over HTTPS prompts for missing credentials; use `git push git@github.com:pierce403/luminism.git main`.
- Always run `source activate.sh` before serving or building to ensure dependencies are installed.
- Avoid editing `site/` directly; regenerate via `mkdocs build`.

## Rapport & Reflection
- Collaborator prefers concise responses and opted not to link AGENTS.md from docs.
- When adjusting prose, call out spelling and wording fixes explicitly; prior requests included quick spellchecks and direct commits.
- Copy guidance: favor “Luminism”/“Luminist” consistently, keep sections scannable (short paragraphs, subheads), and trim overly verbose passages like we did for the quadratic voting/funding page.
- When Git pushes prompt for credentials, use SSH remote: `git push git@github.com:pierce403/luminism.git main`.
