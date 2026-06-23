---
name: resume-update
description: Update resume content across all resume pages and employment posts. Use when adding a new job, updating skills, or syncing content between resume variants.
disable-model-invocation: true
---

# Resume Update Workflow

This site has multiple resume pages that often need to stay in sync:

| File | Language | Audience |
|------|---------|---------|
| `index.html` | English | Consulting clients |
| `resume.html` | Russian | RU job market |
| `employment-resume.html` | English | EM/leadership roles |
| `mindbox-engineering-manager-resume.html` | English | Mindbox-specific |

## Employment Data Source

Employment history lives in `_posts/` as structured YAML posts. Each entry is the **single source of truth** for that job. When editing employment history, update the post first, then check if resume pages pull from it via Liquid or have hard-coded duplicates.

## Steps for a Resume Update

1. **Identify what changed**: new role, new skill, updated outcome, language switch
2. **Update the `_posts/` entry** if it affects an employment record
3. **Check `index.html`** — uses `site.posts` Liquid loop (year >= 2017)
4. **Update `resume.html`** if the change is relevant for the Russian version
5. **Update `employment-resume.html`** and `mindbox-engineering-manager-resume.html` if content is hard-coded there
6. **Verify `_site/` is up to date** — run `bundle exec jekyll build` if testing locally; GitHub Pages rebuilds automatically on push

## Arguments: $ARGUMENTS

If arguments are provided, use them to understand what specifically needs to be updated.
