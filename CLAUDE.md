# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Jekyll static site deployed on GitHub Pages at `igor-pavlov.ru`. Personal consulting portfolio + multiple resume variants. No CI/CD — GitHub Pages auto-builds on every push to `master`.

## Local Development

```bash
bundle exec jekyll serve   # serves at localhost:4000
bundle exec jekyll build   # builds to _site/
```

**Note:** `Gemfile` and `Gemfile.lock` are gitignored. You need a local Gemfile to run the site. Minimal working Gemfile:
```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```

Ruby version: **3.4.4** (managed by asdf via `.tool-versions`).

## Architecture

- **Theme**: `jekyll-theme-minimal` — most styling comes from the gem, not this repo
- **`style.scss`** (root) — main stylesheet override, compiled into `_site/`
- **`_sass/`** — partials: `_variables.scss`, `_reset.scss`, `_highlights.scss`, `_svg-icons.scss`
- **`_site/`** — build output, **intentionally committed** to the repo
- **`_layouts/`** — `default.html` (main wrapper with header/footer), `page.html`, `post.html`

## Resume Pages

| File | Purpose |
|------|---------|
| `index.html` | Consulting landing page (English) |
| `resume.html` | One-page resume (Russian) |
| `employment-resume.html` | Leadership/EM resume (English) |
| `mindbox-engineering-manager-resume.html` | Mindbox-targeted EM resume |

Each resume page uses a different `body_class` for targeted CSS.

## Employment History Posts

`_posts/` stores employment entries **as structured data**, not blog posts. Each post has custom frontmatter:

```yaml
dates: "2022 — 2025"
employer: "Company Name"
position: "Job Title"
responsibilities:
  - "Item 1"
activities:
  - "Item 1"
```

`index.html` filters posts with `year >= 2017` to build the experience section.

## Content Language

- `index.html` — English
- `resume.html` — Russian
- All other resume variants — English (except where noted in frontmatter)

## Custom Domain

`CNAME` file points to `igor-pavlov.ru`. Do not delete or modify it.
