# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal site + blog for **Patrik Šíma** (Senior .NET & Azure consultant),
served at `patriksima.github.io`. It is a **Jekyll** site built on the **Beautiful Jekyll** theme
(by Dean Attali) — this repo is a fork of the theme, so most infrastructure files are upstream and
the actual owned content is a thin layer on top (see "What's yours vs the theme's" below).

Almost all reader-facing content is in **Czech** (`language: cs`, `timezone: Europe/Prague`).
GitHub Pages builds and deploys automatically on push to `master`. A GitHub Actions workflow
(`.github/workflows/ci.yml`) additionally validates on every push/PR with
`bundle exec jekyll build --future` (Ruby 3.2) — it's a build check only, not the deploy.

## Commands

```bash
bundle install                 # one-time: install Ruby gems
bundle exec jekyll serve       # local dev server with live reload at http://localhost:4000
bundle exec jekyll serve --drafts   # also render files in _drafts/
bundle exec jekyll serve --future   # also render future-dated posts (a common pattern here)
bundle exec jekyll build       # build static site into _site/ (gitignored)
```

Posts are sometimes committed with a publish date in the future; Jekyll silently skips them
without `--future`, so pass it when previewing an upcoming post locally.

There is no test/lint suite — this is content, not application code. Validation is visual via the
local server. Ruby + Bundler must be installed.

**Environment: Windows.** Run shell commands via PowerShell, not Bash/POSIX tools (no `awk`, `wc`,
`grep` one-liners). Use PowerShell cmdlets or the dedicated Grep/Glob/Read tools instead.

## Content model

- **Blog posts** live in `_posts/` and must be named `YYYY-MM-DD-slug.md`. The live URL is
  `/:year-:month-:day-:title/` (see `permalink` in `_config.yml`), so the date in the filename is
  part of the public URL — don't rename a published post's file.
- **Standalone pages** are top-level `.md`/`.html` files (e.g. `aboutme.md`, `cv.md`, `services.md`,
  `sluzby.md`, `hireme.md`, `bsc-spoluprace.md`). Anything not in `_posts` defaults to
  the `page` layout. `devlog.md` is not a content page — it's a `layout: null` redirect stub that
  sends `/devlog/` to the homepage; leave it in place so old links keep working. The navbar is hand-curated in `_config.yml` under `navbar-links` — adding a page
  file does NOT add it to the nav.
- Some pages exist as English/Czech pairs (e.g. `services.md` ↔ `sluzby.md`). Keep both in sync when
  editing service offerings.

### Post front matter convention

Follow the pattern of existing posts in `_posts/`, e.g.:

```yaml
---
layout: post                       # inherited as default; usually omit
title: "..."
subtitle: "..."
tags: [management, leadership, ...] # lowercase, drives /tags page
excerpt: "..."                     # shown on the feed page and in SEO
---
```

Czech long-form posts typically open with an **English summary** as a `>` blockquote immediately after
the front matter, often ending with a CTA link to `/services/` or `/sluzby/`, followed by a `---`
separator before the Czech body. Match this house style when adding or editing articles. `comments: true` and `social-share: true` are applied to all posts via `defaults`.

## What's yours vs the theme's

When making changes, edit the owned content; avoid touching theme internals unless intentionally
customizing the theme.

- **Owned content:** `_posts/`, the top-level page files listed above, `index.html` (custom hero
  landing with inline styles), `_config.yml`, `assets/img/`, `assets/pdf/`.
- **Upstream theme (change with care):** `_layouts/`, `_includes/`, `assets/css/beautifuljekyll*.css`,
  `_data/ui-text.yml`, `README.md`, `CHANGELOG.md`, `beautiful-jekyll-theme.gemspec`, `staticman.yml`,
  `404.html`, `feed.xml`, `tags.html`. The 19KB `README.md` is the theme's docs, not project docs.

## Site config notes (`_config.yml`)

- Comments: **Disqus** (`disqus: patriksima78`). Other comment backends are present but commented out.
- Analytics: Google `gtag` is active.
- Markdown is **kramdown with GFM input**; syntax highlighting via **rouge**.
- Plugins: `jekyll-paginate` (5/page), `jekyll-sitemap`, `jekyll-seo-tag`.
- `exclude:` keeps `README.md`, `CHANGELOG.md`, `Gemfile*`, `LICENSE`, `screenshot.png`, `docs/` out of
  the built site.
