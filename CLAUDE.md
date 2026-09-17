# CLAUDE.md – ryszard-twardy.github.io

## Purpose
Static portfolio site for the GitHub Pages user site. No build step, no framework, no CDN of any kind: fonts and icons are self-hosted under `assets/` (DSGVO). Pages: `index.html` (landing), `about/`, `datenschutz/`, later `kupferkanne/` (case study).

## Design contract
- Stratus brand system, adapted from stratusstudio.eu. The tracked pages are the reference.
- `tokens.css` holds the design tokens and is the single source of truth; `styles.css` consumes them.
- Fonts: Montserrat 300/700/900 (headings, wordmark), Lato 400/700 (body), IBM Plex Mono 400 (stack lines, landing only); woff2 from `assets/fonts/` (Fontsource latin subsets), never Google Fonts. `font-display: optional` on every face, and each page preloads every face it uses (no layout shift from the swap race).
- One accent, `--accent` red rgb(249,9,9), for squares, underlines, rules and the CTA button. Never copper and red together.
- No gradients, no entrance animations, no numbered 01/02 labels. Uppercase only where Stratus uses it: h1, hero subtitle, tile h3. Tiles sit on `--neutral`; no shadow beyond the hover state.
- Brand assets are never altered: no crop, recolour, glyph or aspect change; proportional downscaling only.

## Content contract
- Every figure on the site must be traceable to the source project's public docs.
- Missing data stays a placeholder in brackets; never invent numbers, names, or CLI output.
- Contact email is r.twardy@proton.me and appears nowhere else. No Impressum; `datenschutz/` carries a short privacy note (GitHub Pages hosting, server logs, no cookies, no tracking). A home address never enters the repo.

## Git rules
- `git add` is path-scoped only, never `-A`.
- Commit and push are gated separately; wait for an explicit "go" for each.
- Conventional Commits, ASCII-only subjects, en-dash (U+2013) only; em-dash (U+2014) is prohibited.
- No `Co-authored-by` trailers.
- Write the message to `.scratch/commit_msg.txt` and apply it with `git commit -F .scratch/commit_msg.txt`.

## Paths
- `.scratch/` is local-only and gitignored.
- `.venv/` (uv, Python 3.12, playwright + pillow) is local-only and gitignored.

## Skills
- Before every commit that touches HTML or CSS: run the `.claude/skills/web-design-guidelines` review and take `.claude/skills/webapp-testing` screenshots (1280 px and 390 px) into `.scratch/qc/`. `.scratch/qa.py` is the executable form: profiles `stratus` (landing), `stratus-about`, `stratus-privacy`; `--cls-runs 5` (every fresh load CLS 0); `--chrome index.html about/index.html datenschutz/index.html` (header and footer identical across pages).
