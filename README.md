# blacfli.github.io

Personal academic site of **Michael Evan Santoso** — PhD student at Ritsumeikan University,
Japan (Computational Creativity, NLP, topic modeling). Minimalist style inspired by
[alarithuhde.com](https://alarithuhde.com/). Plain HTML + CSS, no build step — GitHub Pages
serves the `main` branch root directly at **https://blacfli.github.io/**.

## Pages

| File                | Section      |
|---------------------|--------------|
| `index.html`        | About (home) |
| `cv.html`           | CV           |
| `research.html`     | Research     |
| `publications.html` | Publications |
| `contact.html`      | Contact      |
| `404.html`          | Not found    |

## Optional touch-ups

The site is fully populated (CV achievements come from the official Ritsumeikan researcher
profile). A few minor items to confirm if you wish:

- **Best Paper Award** (2025) — the profile didn't name the venue (likely ICOMIT 2025).
- **Certification** issuer for "Machine Learning with Python…" wasn't named (likely edX / MITx).
- Recurring **Saionji Memorial** awards/scholarships were consolidated into single CV lines.
- The music paper links to your ResearchGate profile; a specific publication URL or a hosted PDF
  in `assets/papers/` would make it a direct download.

Public databases (ORCID, LinkedIn) currently list only your 2019–2023 Bachelor's, not your
PhD — you may want to update those so they match your record.

## Editing

- **Headshot** — your photo lives at `assets/img/headshot.jpeg` (800×800, square). To change it,
  replace that file (square images crop best); the homepage `<img>` already points to it.
- **Publications** — duplicate an `<li class="pub">` block in `publications.html` to add a paper.
- **Paper PDFs** — drop downloadable PDFs in `assets/papers/` (see its README) and link them
  in `publications.html`; a commented template sits next to each entry's DOI. The ICACS 2025
  paper already links the ACM open-access PDF directly.
- **Colors** — edit the CSS custom properties at the top of `assets/css/style.css`
  (`--accent`, `--bg`, `--text`, …); a `prefers-color-scheme: dark` block mirrors them.
- **CV PDF** — `cv.html` prints itself to PDF in the browser. To serve a real file instead,
  drop it at `assets/cv/cv.pdf` and point the button's `href` there.

> The site header/footer is repeated in each `.html` file (no includes without a build tool).
> When you change the nav, update all pages.

## Preview locally

```bash
python3 -m http.server 8000
# open http://localhost:8000/
```

## Deploy

Commit and push to `main`; GitHub Pages republishes within ~1 minute. If Pages isn't on yet:
repo **Settings → Pages → Build and deployment → Deploy from a branch → `main` / root**.
