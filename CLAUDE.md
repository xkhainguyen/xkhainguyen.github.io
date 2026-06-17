# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Khai Nguyen's personal academic website, built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme and deployed to GitHub Pages at https://xkhainguyen.github.io. Most work here is content editing (news, projects, publications, CV) rather than theme development. The al-folio upstream docs (`INSTALL.md`, `CUSTOMIZE.md`, `FAQ.md`, `README.md`) are authoritative for theme mechanics.

## Commands

Local development is easiest via Docker (avoids the Ruby/Bundler/ImageMagick toolchain):

```bash
docker compose up          # builds + serves with live reload at http://localhost:8080
                           # watches _config.yml and restarts Jekyll on change (see bin/entry_point.sh)
docker compose pull        # update to latest prebuilt image before `up`
```

Native build (requires Ruby 3.2.x, Bundler, ImageMagick, Node, Python/Jupyter):

```bash
bundle install
bundle exec jekyll serve   # serve locally with watch
bundle exec jekyll build   # one-off build into _site/ (cibuild runs exactly this)
```

Formatting / hooks:

```bash
npx prettier --write .     # prettier + @shopify/prettier-plugin-liquid for .html/.liquid
pre-commit run --all-files # trailing-whitespace, end-of-file-fixer, check-yaml, large-files
```

There is no test suite. CI (`.github/workflows/deploy.yml`) builds on every push/PR to `master`/`main`, runs `purgecss` to strip unused CSS, and on non-PR pushes deploys `_site/` to the `gh-pages` branch. Editing content and pushing to `master` is the normal release path; `bin/deploy` is a manual alternative.

## Content model

Content lives in Jekyll collections, each a directory of Markdown files with YAML front matter. Adding content means adding a file, not editing a central list.

- `_news/` — short homepage announcements. Filename convention `YYMM_slug.md`. Front matter `layout: post`, `date:`, `inline: true`. Body is one or two sentences, often with links. These render newest-first on the About page.
- `_projects/` — project cards. Front matter `category:` groups them on `_pages/projects.md` (e.g. `lab`, `class`, `online`, `misc`); `importance:` orders within a category; `img:` is the card thumbnail. Filename prefixes (`class_`, `onl_`/`online_`, `misc_`) mirror the category.
- `_bibliography/papers.bib`, `preprints.bib`, `reports.bib` — BibTeX sources rendered by **jekyll-scholar** into the publications page. The author's own name is bolded via the `scholar.last_name`/`first_name` lists in `_config.yml`. Custom BibTeX fields drive rich rendering: `abbr`, `selected`, `preview` (image), `pdf`, `code`, `website`, `award`, `additional_info`, plus `bibtex_show`. Keep these field names; `filtered_bibtex_keywords` in `_config.yml` hides them from the printed citation. Citation counts are fetched at build time by the Google Scholar / Inspire-HEP plugins.
- `_pages/` — top-level pages (`about.md` is the homepage). Navbar entries and dropdowns are defined by page front matter, not a separate menu file.
- `_data/` — structured data: `cv.yml` (drives the CV page when present), `coauthors.yml` (links coauthor names in the bibliography), `repositories.yml` (GitHub repos/users for the repositories page), `venues.yml` (publication venue styling).

## Key configuration

- `_config.yml` is the single control surface for site-wide behavior: profile/social handles, navbar/footer, jekyll-scholar (`scholar:` block), pagination, and feature toggles. After editing it, Jekyll must restart (Docker entry point does this automatically; a native `jekyll serve` needs a manual restart).
- `_plugins/*.rb` are local Ruby plugins beyond the gems in the `Gemfile`. Notably `google-scholar-citations.rb` and `inspirehep-citations.rb` (fetch citation counts), `hide-custom-bibtex.rb` (strips internal bib fields), and `cache-bust.rb`. Network-fetching plugins can slow or fail builds when offline.
- `assets/` holds images, the SCSS in `_sass/`, and per-project image folders (e.g. `assets/rex_lab/`). `img:` paths in front matter are relative to the repo root (`assets/...`).

## Conventions

- Match the existing front matter shape when adding to a collection; copy an adjacent file as a template rather than writing front matter from scratch.
- Dates in `_news` front matter include a timezone offset (e.g. `2026-05-01 07:59:00-0400`) and gate visibility (future dates may not render in production).
- This repo tracks upstream al-folio; prefer overriding via `_config.yml`, `_data/`, and content files over editing `_layouts/`/`_includes/` so future theme updates merge cleanly.
