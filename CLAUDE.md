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
- **CSS customization**: Edit `assets/css/style.scss` - uses SCSS with Cayman theme imports
- **Image management**: Add project screenshots to `assets/` directory

## Architecture

- **Static Site Generator**: Jekyll
- **Theme**: jekyll-theme-cayman (GitHub-provided theme) with custom SCSS overrides
- **Content**: Markdown files with custom HTML structure for portfolio layout
- **Styling**: Custom CSS classes for tables, project lists, and responsive layout
- **Hosting**: GitHub Pages (automatic deployment on git push)

## File Structure

- `_config.yml`: Contains site configuration and theme selection
- `index.md`: Main homepage content in Markdown format with custom HTML structure
- `assets/css/style.scss`: Custom SCSS styles that extend the Cayman theme
- `assets/avatar.png`: Profile avatar image
- `assets/*.png`: Project screenshot images

## Workflow

1. Edit Markdown files locally
2. Commit and push to GitHub
3. GitHub Pages automatically builds and deploys the site
4. No local build process required for basic content changes

## CSS Patterns

- Container layout with `.container`, `.avatar-container`, `.header-container`, `.content-container`
- Custom table styles with `.skills-table` and `.education-table` classes
- Project list styling with `.project-list` and bordered list items
- Responsive design with max-width containers and centered elements