# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal site for Jason Pan (paxaq), founder of T-Menu. Hosted on GitHub Pages. Jekyll builds `index.md` against the `jekyll-theme-cayman` theme; a standalone HTML blog post and a plain-text résumé sit alongside it as independently-served files.

The site is intentionally a **taste portrait, not a portfolio**, presented as a Homebrew-flavored fake terminal that streams its content in like an agent. Hero (window chrome + title bar) → streamed sections: whoami, Currently, brew list (skills), Writing, Tastes, Off-hours, contact. No project cards, no education timeline, no résumé CTA. If asked to "add a project list" or similar, push back and confirm — that direction was deliberately retired.

## Development Commands

- **Local preview**: `bundle exec jekyll serve` (after `gem install jekyll bundler`). There is no `Gemfile` checked in — `bundle init && bundle add jekyll jekyll-theme-cayman` first if you need one.
- **Deploy**: push to `main`. GitHub Pages builds and publishes automatically; there is no CI config.
- **No build step for the blog post or résumé**: `source-map-leak-blog.html` and `resume.txt` are served as-is.

## Architecture

The site is intentionally tiny but mixes two rendering paths — knowing which one you're touching matters:

1. **Jekyll-rendered home page** (`index.md` + `assets/css/style.scss`)
   - `index.md` is *not* prose Markdown: it's a fake-terminal layout (`.screen` → `.terminal` → `.titlebar` + `.body`) plus an inline `<script>` that drives the streaming animation. There is no Jekyll front matter; Cayman's default layout still wraps everything.
   - **The Cayman theme is hidden, not extended.** `style.scss` `display: none`s `.page-header` and `.site-footer` and zeroes out `.main-content`. The `@import "jekyll-theme-cayman";` line is kept to satisfy the build, but nothing from the theme is visible. Don't rely on Cayman's typography or layout primitives — they're suppressed.
   - **Streaming animation contract.** The script in `index.md` reads from a `script` array of `[kind, text]` tuples (`comment` / `blank` / `cmd` / `header` / `out`). `typeCmd` chars-out commands with jitter; `out` lines append HTML and advance with a brief delay. Adding a new section = appending more entries to that array. The `skip` button flips `skipped = true` to fast-forward; `prefers-reduced-motion: reduce` sets the same flag at start.
   - **Token CSS classes** are the contract between the script's HTML strings and `style.scss`: `.usr .host .path .dollar .cmd .arrow-h` (`==>`) `.arrow` (`→`) `.amber .ok .dim .comment .link .cursor`. Rename one without the other and the colors silently fall back to plain text.
   - **`<noscript>` fallback** in `index.md` exists so JS-disabled visitors and crawlers see the contact/writing links as plain HTML. Keep it synced with the script content when adding important links.

2. **Standalone HTML blog post** (`source-map-leak-blog.html`)
   - Self-contained: inline `<style>`, its own design tokens (dark theme, `--accent: #ff6b35`), its own Google Fonts import. It does **not** use the Cayman theme or `style.scss`.
   - Edit styles inside the file's `<style>` block; do not try to share CSS with the home page.

3. **Static assets** (`assets/`)
   - `avatar.png` is no longer referenced — the terminal page has no avatar. Still on disk.
   - `pyheadshotsclick.png`, `pp-headshots-starter1.png`, `khaostreetfood-website.png`, `UOgameinfos.png` are leftovers from the retired portfolio section. Still served (anyone with the URL can hit them) but not linked.
   - `resume.txt` is no longer linked from `index.md`. Still on disk and served as-is.

## Conventions

- External links use `target="_blank" rel="noopener"` (or `noopener noreferrer`) — preserve when adding new links.
- All streaming animation must respect `prefers-reduced-motion: reduce` (handled by the `reduceMotion` check at the top of the script — don't add new motion without honoring it).
- The terminal's color palette is defined as SCSS variables (`$bg, $fg, $green, $yellow, $amber, $cyan, $pink, $orange, $dim, $comment`) at the top of `style.scss`. Pick from these instead of introducing new hex values; the Homebrew/Gruvbox warm-dark feel depends on them staying coherent.
