# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`blacfli.github.io` — the personal academic portfolio of **Michael Evan Santoso** (PhD student,
Ritsumeikan University; Computational Creativity / NLP). It is a **GitHub Pages user site**:
hand-written static HTML + CSS with **no build step, no framework, and no Jekyll** (a `.nojekyll`
file forces GitHub Pages to serve files as-is). The `main` branch root is served directly at
https://blacfli.github.io/.

## Commands

There is no build, lint, or test tooling — it's plain static files.

- **Preview locally:** `python3 -m http.server 8000` (from repo root), then open
  `http://localhost:8000/`.
- **"Test" (manual verification):** serve locally, then check pages load and links resolve, e.g.
  `curl -s -o /dev/null -w '%{http_code}' http://localhost:8000/cv.html`. Click through the nav and
  a bad URL (to hit `404.html`); resize to confirm mobile reflow.
- **Deploy:** commit and push to `main`; GitHub Pages republishes in ~1 minute. (If Pages is off:
  repo Settings → Pages → Deploy from a branch → `main` / root.)

## Architecture & conventions

- **Pages are standalone documents.** Each `*.html` (`index` = About, `cv`, `research`,
  `publications`, `contact`, plus `404`) is a complete HTML file. The shared chrome — header,
  `<nav class="site-nav">`, footer, and the inline year script — is **duplicated in every page**;
  there is no templating or includes. **When changing the nav, site title, or footer, edit all
  HTML files.** The active page is marked with `aria-current="page"` on its nav link. `404.html`
  uses root-absolute paths (`/cv.html`) since it can be served from any URL; other pages use
  relative paths.
- **One stylesheet drives everything:** `assets/css/style.css`. The color palette lives in CSS
  custom properties under `:root` (accent is teal `--accent: #2f6f6a`), and a
  `prefers-color-scheme: dark` block mirrors those tokens — retune the theme in one place.
  Page-specific rules are **class-scoped** so they don't leak: `.cv` (CV page), `.pub-*`
  (publications), `.links`/`.intro` (About), etc.
- **CV page (`cv.html`)** is a full inline résumé under `<main class="wrap cv">` (no download/print
  button — the page itself is the CV). All its styles are scoped under `.cv` / `.cv-*`.
- **`contact.html` shares `.btn` and `.cv-actions`** for its email button — do not delete those CSS
  rules when editing CV styles.

## Content integrity (important)

All bio, publication, and achievement content is **real and source-verified — do not fabricate,
infer, or pad** entries (e.g. invent a DOI, venue, or co-author). Canonical sources:

- Ritsumeikan researcher profile (achievements/awards/presentations/teaching):
  `https://gyoseki.ritsumei.ac.jp/ritgshp/KgApp/k03/resid/S009105?lang=en`
- Google Scholar `zKkCr3cAAAAJ` · ORCID `0000-0002-5002-0275` · DBLP `369/6828` ·
  OpenAlex `A5093936494` · Semantic Scholar `2320587361`. Publications were cross-verified across
  Semantic Scholar / DBLP / OpenAlex.

Retrieval gotchas: **Google Scholar and ResearchGate are bot-walled** (CAPTCHA / Cloudflare 403) —
use the bibliographic DBs/APIs instead. The gyoseki profile truncates each section to ~5 rows;
fetch complete lists with raw `curl` (browser User-Agent) by following the `k05` "Display All"
expander URLs (e.g. `/ritgshp/KgApp/k05/resid/S009105/<id>`). The base profile URL works without
the `sessionId` query param.

## Paper PDFs

Self-hosted downloadable PDFs go in `assets/papers/` (see `assets/papers/README.md` for the
expected filenames). Each `publications.html` entry has a commented PDF-link template beside its
DOI; the ICOMIT 2025 music paper has no DOI and links to ResearchGate.
