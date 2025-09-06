# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a GitHub Pages website using Jekyll with the Cayman theme. The site consists of:
- `_config.yml`: Jekyll configuration with theme setting
- `index.md`: Main content page in Markdown format

## Development Commands

Since this is a GitHub Pages site, development is primarily done through:
- **Local testing**: Install Jekyll locally with `gem install jekyll bundler` and run `bundle exec jekyll serve`
- **Deployment**: Push changes to GitHub - GitHub Pages automatically builds and deploys
- **Content editing**: Edit Markdown files directly

## Architecture

- **Static Site Generator**: Jekyll
- **Theme**: jekyll-theme-cayman (GitHub-provided theme)
- **Content**: Markdown files that get converted to HTML
- **Hosting**: GitHub Pages (automatic deployment on git push)

## File Structure

- `_config.yml`: Contains site configuration and theme selection
- `index.md`: Main homepage content in Markdown format
- No custom CSS/JS - uses theme's default styling

## Workflow

1. Edit Markdown files locally
2. Commit and push to GitHub
3. GitHub Pages automatically builds and deploys the site
4. No local build process required for basic content changes