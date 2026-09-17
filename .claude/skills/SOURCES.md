# Vendored project-local skills

Both folders below are verbatim copies from their upstream repositories (shallow clone on 2026-09-03, only the skill folder copied). They are excluded from this repo's authored-file conventions (EN-only, en-dash only, no U+2014): upstream text is kept unmodified to preserve provenance. Do not edit them in place; re-vendor from upstream instead.

| Skill folder | Upstream repo | Upstream path | Commit | License |
|---|---|---|---|---|
| `web-design-guidelines/` | https://github.com/vercel-labs/agent-skills | `skills/web-design-guidelines/` | `063bee94c3f4df8453406c830b0a7df0f2860278` | MIT (README.md "License" section; the repo ships no LICENSE file) |
| `webapp-testing/` | https://github.com/anthropics/skills | `skills/webapp-testing/` | `53048666b05b4799081517d00e09e0a2dd688678` | Apache-2.0 (`webapp-testing/LICENSE.txt`, copied with the skill) |

Notes
- `web-design-guidelines` fetches its rule set at review time from `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md`. This is a tooling request made by the agent during review, not something the published site loads.
- `webapp-testing` expects Python Playwright. In this repo it runs from `.venv/` (uv, Python 3.12, `playwright` + `pillow`, Chromium only).
- Not installed on purpose: `ui-ux-pro-max`.
