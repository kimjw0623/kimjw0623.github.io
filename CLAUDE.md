# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is an al-folio Jekyll-based academic website/blog template. The site is built with Jekyll and uses GitHub Pages for deployment.

## Common Development Commands

### Local Development

```bash
# Using Docker (recommended)
docker compose pull
docker compose up

# For slim Docker image (<100MB)
docker compose -f docker-compose-slim.yml up

# Build with Docker
docker compose up --build

# The site will be available at http://localhost:8088
```

### Ruby Dependencies

The site uses Jekyll and various Jekyll plugins managed through Bundler. Key gems are specified in the Gemfile including:

- jekyll-scholar (for publications/bibliography)
- jekyll-imagemagick (for responsive images)
- jekyll-jupyter-notebook (for Jupyter notebook integration)

## High-Level Architecture

### Directory Structure and Purpose

- **\_pages/**: Contains all the main pages (about, publications, projects, etc.). Each page has a `nav:` property that controls if it appears in the navigation bar.
- **\_posts/**: Blog posts in Markdown format with YAML front matter
- **\_projects/**: Individual project entries displayed on the projects page
- **\_bibliography/**: Contains `papers.bib` for academic publications managed by jekyll-scholar
- **\_config.yml**: Main site configuration including theme settings, plugin configurations, and site metadata
- **\_includes/**: Reusable liquid templates (header.liquid manages the navigation bar)
- **\_layouts/**: Page layout templates
- **\_sass/**: SCSS stylesheets for theming and styling

### Key Configuration Points

1. **Navigation**: Pages appear in the top navigation bar when their front matter includes `nav: true`. The order is controlled by `nav_order`.

2. **Publications**: Managed through BibTeX in `_bibliography/papers.bib`. The jekyll-scholar plugin processes these into formatted citations.

3. **Collections**: The site uses Jekyll collections for news, projects, and books. These are configured in `_config.yml`.

4. **Theming**: Dark/light mode is supported. Theme colors are customizable in `_sass/_themes.scss`.

### Deployment

The site uses GitHub Actions for automated deployment:

1. Changes pushed to main branch trigger the build action
2. Site is built and deployed to gh-pages branch
3. GitHub Pages serves the site from gh-pages

For manual deployment or non-GitHub hosting, the site can be built with `jekyll build` and the `_site` directory can be deployed to any static hosting service.

## Important Notes

- When modifying navigation, edit the `nav:` property in page front matter
- For new blog posts, add markdown files to `_posts/` with format `YYYY-MM-DD-title.md`
- Publications require updating `_bibliography/papers.bib`
- The site supports MathJax for equations, Mermaid for diagrams, and code syntax highlighting
