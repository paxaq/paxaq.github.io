# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal site for Jason Pan (paxaq), founder of T-Menu. Hosted on GitHub Pages. Jekyll builds `index.md` against the `jekyll-theme-cayman` theme; a standalone HTML blog post and a plain-text résumé sit alongside it as independently-served files.

The site is intentionally a **taste portrait, not a portfolio**: hero → Currently (T-Menu) → What I reach for → Tastes → Off-hours. No project cards, no education timeline, no résumé CTA. If asked to "add a project list" or similar, push back and confirm — that direction was deliberately retired.

## Development Commands

- **Local preview**: `bundle exec jekyll serve` (after `gem install jekyll bundler`). There is no `Gemfile` checked in — `bundle init && bundle add jekyll jekyll-theme-cayman` first if you need one.
- **Deploy**: push to `main`. GitHub Pages builds and publishes automatically; there is no CI config.
- **No build step for the blog post or résumé**: `source-map-leak-blog.html` and `resume.txt` are served as-is.

## Architecture

The site is intentionally tiny but mixes two rendering paths — knowing which one you're touching matters:

1. **Jekyll-rendered home page** (`index.md` + `assets/css/style.scss`)
   - `index.md` is *not* prose Markdown: it's a hand-authored HTML structure (hero, `.section-card` articles, `.highlight-list`, `.skill-badges`) wrapped in `.page-wrapper`. The `---` front matter is implicit via the theme; the ghost CTA jumps to the `#vibe` anchor inside this file.
   - `assets/css/style.scss` `@import`s `jekyll-theme-cayman` and then overrides it heavily — gradient body background, glassmorphic cards, pill buttons, floating orbs. The Cayman look is essentially replaced; treat the imported theme as a reset, not a visual baseline.
   - Section classes (`section-card`, `section-card.accent`, `highlight-list`, `skill-badges`) are the contract between `index.md` and the SCSS — renaming one without the other will silently break layout.
   - The SCSS still carries unused rules for `.project-card`, `.project-list`, `.timeline`, `.skills-table`, `.education-table` from the prior portfolio layout. Leave them in place unless you're doing an intentional CSS sweep — they're dormant, not broken.

2. **Standalone HTML blog post** (`source-map-leak-blog.html`)
   - Self-contained: inline `<style>`, its own design tokens (dark theme, `--accent: #ff6b35`), its own Google Fonts import. It does **not** use the Cayman theme or `style.scss`.
   - Edit styles inside the file's `<style>` block; do not try to share CSS with the portfolio page.

3. **Static assets** (`assets/`)
   - `avatar.png` is the only image referenced by the current `index.md`.
   - `pyheadshotsclick.png`, `pp-headshots-starter1.png`, `khaostreetfood-website.png`, `UOgameinfos.png` are leftovers from the retired portfolio section. They're still served (anyone with the URL can hit them) but not linked from any page.
   - `resume.txt` is no longer linked from `index.md` (the "Download Résumé" CTA was removed when the user stopped job-hunting). The file is still on disk and served as-is.

## Conventions

- External links in `index.md` use `target="_blank" rel="noopener noreferrer"` — preserve this when adding links.
- Project screenshots use `loading="lazy"` and meaningful `alt` text.
- A `@media (prefers-reduced-motion: reduce)` block at the bottom of `style.scss` neutralizes transitions; new animations should respect it.
