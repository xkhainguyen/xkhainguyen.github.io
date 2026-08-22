# Static Minimal Website Redesign

Date: 2026-08-22
Branch: `redesign-minimal`

## Goal

Replace the al-folio Jekyll site with a hand-written, static, minimal
HTML site matching the aesthetic of https://younghyopark.me (the Jon
Barron academic template idiom): single column, Lato font, black text
on white, blue links with orange hover, generous whitespace.

## Decisions (locked)

- **Stack:** pure static HTML/CSS. No Jekyll, no Gemfile, no plugins, no build step.
- **Aesthetic target:** younghyopark.me.
- **Markup:** table-based layout (exact template idiom), not flexbox.
- **Content:** migrate everything now (10 papers, ~24 news items, projects).
- **Pages:** `index.html` (home) + `projects.html` (second tab).

## File layout

```
index.html          # home: bio header + photo, news, research, publications
projects.html       # projects tab: grouped project cards
stylesheet.css      # adapted from younghyopark's stylesheet.css
images/             # profile.jpg + paper previews + project thumbs
.nojekyll           # tell GitHub Pages to serve files as-is
```

Assets migrate from the existing `assets/` tree (paper previews live in
`assets/img/publication_preview/` in al-folio; project thumbs in
`assets/`). Only referenced images get copied into `images/`.

## index.html structure

Single outer `<table>`, one column, matching younghyopark:

1. **Bio header** — two-cell row: left `td.bio-text` (name in `<name>`,
   one-paragraph bio adapted from current `about.md`, then a
   `p.bio-links` row of inline text links: email / cv / github / google
   scholar / linkedin / x, plus a **projects** link to `projects.html`),
   right `td.bio-photo` (profile photo).
2. **News** — `heading` "news", then `.news-wrap > .news-list` of
   `p.news-item` (date in `.news-date` + text), collapsed to ~5 items
   with a "show more" toggle (`news-toggle` + `news.js` inline script).
   Migrated from `_news/*.md`, newest first.
3. **Research** — `heading` "research", 2 short paragraphs from current
   about page.
4. **Publications** — `heading` "publications", inner `<table>` with one
   `<tr>` per paper: left cell `.one/.two` hover-swap thumbnail (falls
   back to a single `<img>` when no hover variant), right cell
   `<papertitle>`, authors (own name bolded via `<strong>`), venue +
   year, links (paper/arxiv/pdf/website/code/video/poster/slides), and
   awards/notes rendered as a `.paper-note` with hover tooltip
   (`.paper-tooltip`) mirroring younghyopark's award badges.

Papers, reverse-chronological, from `papers.bib` + `preprints.bib`:

| Year | Key | Venue | Preview |
|------|-----|-------|---------|
| 2026 | td-grpc | IROS | (none → placeholder) |
| 2026 | conic-tinympc | ICRA | tinympc_cone.png |
| 2026 | cheapthrills | preprint | (none) |
| 2025 | swami2025deqmpc | CoRL | deqmpc.png |
| 2025 | le2025mtp | TMLR | (none) |
| 2024 | tinympc | ICRA | tiny_mpc.png |
| 2023 | khai2022formation | IJRNC | khai2022formation.gif |
| 2021 | nam2021arl | ICISN | icisn21.png |
| 2021 | khai2020output | MCA | mca_voltage.png |
| 2021 | khai2021thesis | BS Thesis | bachelor_thesis.png |

Own-name bolding: match `Khai Nguyen`, `Nguyen*, Khai`, `Nguyen, Khai`,
`Nguyen, X. K.`, `Nguyen, Xuan Khai` variants. Preserve `*` equal-contribution marks.

## projects.html structure

Same bio-less compact header (name + nav links back to home). Projects
grouped by the existing categories, in this order: **lab** (5),
**misc** (5), **online** (6), **class** (12). Each project a row with
thumbnail + title + description, same `.one` thumbnail treatment.
Content migrated from `_projects/*.md` (front-matter `title`,
`description`, `img`, body).

## CSS

Copy younghyopark's `stylesheet.css` verbatim as the base (it is a
public static asset in the Jon Barron template lineage), then trim
anything unused. Keep: Lato `@font-face` block (loaded from
fonts.gstatic.com), link colors, `name`/`heading`/`papertitle` tags,
`.one/.two` hover thumbnails, news collapse styles, paper tooltip,
mobile `@media` rules. This keeps the visual match exact.

## Retiring Jekyll (deferred to merge time, flagged here)

The al-folio scaffolding (`_config.yml`, `Gemfile`, `_plugins/`,
`_layouts/`, `_includes/`, `_sass/`, collections) is NOT deleted during
implementation, so the branch stays diffable and reversible. Two calls
to make before/at merge:

- **(a) Archive vs delete** the al-folio files. Recommendation: move
  them under `legacy/` in a follow-up commit, or delete once the static
  site is confirmed live.
- **(b) GitHub Pages source.** Current deploy is a GitHub Actions
  workflow building Jekyll to `gh-pages`. For static, switch Pages to
  serve `master` root directly (Settings → Pages → Deploy from branch,
  `master` / root) and drop `.github/workflows/deploy.yml`, OR keep a
  trivial workflow that publishes the root. `.nojekyll` is added
  regardless so Pages does not attempt a Jekyll build.

Deployment cleanup is a separate step after the static site is reviewed
locally; it does not block building the pages.

## Non-goals (YAGNI)

- No blog, no CV page (CV stays a linked PDF), no repositories page, no
  teaching/talks sections on the page (not requested; can add later).
- No citation-count fetching, no dark mode, no JS framework.
- No responsive image generation pipeline; use images as-is.

## Testing / verification

No test suite (static site). Verification is visual:
- Serve locally: `python3 -m http.server` in repo root, open
  `index.html` and `projects.html`.
- Check: all links resolve, all `images/` referenced files exist (grep
  `src=`/`href=` against `ls images/`), news toggle works, mobile
  layout at 375px width, own-name bolding correct on every paper.
- Confirm no external requests except Google Fonts.
