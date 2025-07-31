# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static blog website for benjaminpatch.com built with Pelican (Python static site generator) and Bootstrap. The site focuses on AI ethics, fundamentals, and practical programming guides.

## Architecture

- **Static Site Generator**: Pelican (Python-based)
- **Theme**: Custom Bootstrap theme located in `themes/bootstrap/`
- **Content**: Markdown files in `content/posts/` organized by category directories
- **Configuration**: `pelicanconf.py` (development) and `publishconf.py` (production)
- **Task Runner**: Invoke (Python) with tasks defined in `tasks.py`
- **Package Management**: uv (Python package manager)
- **Deployment**: GitHub Pages via `gh-pages` branch

## Development Commands

### Environment Setup
```bash
uv sync                    # Sync project dependencies
```

### Development Workflow
```bash
rm -rf output/*           # Clean output directory
uv run invoke regenerate  # Build site with auto-regeneration
uv run invoke livereload  # Build site with live reload server
```

### Build Commands
```bash
uv run invoke build       # Build site once
uv run invoke rebuild     # Build with delete switch
uv run invoke serve       # Serve built site at localhost:8000
uv run invoke preview     # Build production version
```

### Production Deployment
```bash
rm -rf output/*           # Clean output directory
make publish              # Build production site
```

After building, push the generated site to the `gh-pages` branch for GitHub Pages deployment.

### Alternative Make Commands
```bash
make html                 # Generate site
make clean                # Remove generated files
make serve                # Serve site at localhost:8000
make devserver            # Serve with auto-regeneration
make github               # Deploy to GitHub Pages
```

## Project Structure

- `content/`: Source content (Markdown files)
  - `posts/`: Blog articles organized by category folders
  - `pages/`: Static pages like About
  - `images/`: Images used in content
  - `extra/`: Static assets (favicons, robots.txt, etc.)
- `themes/bootstrap/`: Custom Bootstrap theme
  - `templates/`: Jinja2 templates
  - `static/`: Theme CSS and JS files
- `output/`: Generated static site (created during build)
- `pelicanconf.py`: Development configuration
- `publishconf.py`: Production configuration overrides
- `tasks.py`: Invoke task definitions
- `pyproject.toml`: Python project configuration with dependencies

## Content Management

- Articles use Pelican's metadata format in Markdown
- URL structure: `/posts/{YYYY}/{Mon}/{DD}/{slug}/`
- Static assets from `content/extra/` are copied to site root
- Images should be placed in `content/images/`
- Custom Bootstrap theme with CDN-hosted CSS/JS for performance

## Key Pelican Settings

- Theme location: `themes/bootstrap`
- Articles path: `content/posts/`
- Output path: `output/`
- Timezone: America/Los_Angeles
- Site includes Google Analytics (production only)
- Sitemap generation enabled via pelican-sitemap plugin