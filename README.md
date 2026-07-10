# Amal Imangulov — personal site

My little corner of the internet: a single-page personal homepage with an
about section, links to my daily puzzle games, interview-prep resources, and
other projects. Dark/light theme, no build step, no backend.

**Live:** https://imangulova.github.io/

## What's here

- `index.html` — the entire site: one self-contained file (inline CSS + JS),
  dark/light theme toggle. Sections: **About**, **Daily Games**,
  **Interview Preparation**, **Projects**.
- `cv.md` — CV in Markdown (source of truth).
- `cv.pdf` — exported CV for download.

## How it's built

Plain static HTML/CSS/JS — a single `index.html` with everything inline, in the
same dark/light visual style as my other projects (chvb-stats, tatarchgk). No
framework, no build tooling, nothing leaves the browser.

## Run locally

Just open the file — no build, no dependencies:

```bash
open index.html          # macOS
# or serve it:
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

This is my **root GitHub Pages site**: repo `ImangulovA/ImangulovA.github.io`,
served at `imangulova.github.io`. Push to `main` and Pages publishes it.
**Settings → Pages → Source = Deploy from a branch → `main` / root.**

See [../plan.md](../plan.md) for the broader plan (custom domain, future quiz
site).
