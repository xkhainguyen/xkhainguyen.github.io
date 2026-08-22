# CLAUDE.md

Guidance for Claude Code working in this repository.

## What this is

Khai Nguyen's personal academic website, https://xkhainguyen.github.io — hand-written
**static HTML/CSS**, no build step, no framework. (It was previously the al-folio Jekyll
theme; that scaffolding was removed on 2026-08-22 in favor of a minimal static site in the
Jon Barron / younghyopark.me style.)

## Structure

- `index.html` — homepage: bio header + photo, collapsible news feed, research statement,
  featured open-source callout, and publications (conference + journal + workshop papers in
  one date-sorted list).
- `projects.html` — projects grouped into lab / competitions & misc / online courses / class,
  with GitHub star badges for public repos. A project links to its subpage if one exists,
  otherwise to its GitHub repo.
- `projects/*.html` — per-project detail subpages (converted from the old writeups). Each uses
  the shared header (`.crumbs`, `.proj-head` with `.kicker`/`.proj-title`/`.proj-sub`/`.reslinks`),
  a `.prose` body, and a `.backlink` footer. Paths inside subpages are prefixed with `../`.
  Pages with LaTeX load MathJax from a CDN.
- `stylesheet.css` — the single stylesheet (Lato font, `#1772d0` links / `#f09228` hover,
  thumbnail/figure/abstract/oss-card styles, mobile `@media (max-width:600px)` rules).
- `images/` — thumbnails, favicon, profile photo. `files/` — linked PDFs. `media/` —
  self-contained assets for the project subpages.
- `.nojekyll` — tells GitHub Pages to serve the files as-is (no Jekyll build).

## Content model

Content lives directly in the HTML (there are no data files or collections). To add a paper,
news item, or project, edit `index.html` / `projects.html` directly, or add a new
`projects/<slug>.html` and link it from `projects.html`.

## Conventions

- Thumbnails use `object-fit: contain` so diagrams are never cropped.
- Publications are one list, sorted newest to oldest; own-name is bolded via `<strong>`.
- Keep the outer wrapper responsive: `<table ... style="width:100%; max-width:800px">`.
- Add `loading="lazy"` to new `<img>` thumbnails.
- No em dashes in prose.

## Deploy

GitHub Pages serves the `master` branch root statically (`.nojekyll`). There is no CI:
edit, commit, and `git push origin master`; Pages redeploys automatically. Preview locally
with `python3 -m http.server` in the repo root.
