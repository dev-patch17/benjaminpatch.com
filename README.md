# Benjamin Patch

Public website for benjaminpatch.com, built with
[Pelican](https://getpelican.com/) and [Bootstrap](https://getbootstrap.com/).

Code syntax highlighting provided by [highlight.js](https://highlightjs.org/).

## Pelican Site Updates

This project's Python environment is managed by
[uv](https://docs.astral.sh/uv/).

- `uv sync`: Sync the project's dependencies with the environment.
- `uv add`: Add a dependency to the project.
- `uv remove`: Remove a dependency from the project.
- `uv run`: Run a command in the project environment.

### Development

```bash
rm -rf output/*
uv run invoke regenerate
uv run invoke livereload
```

### Production

```bash
rm -rf output/*
make publish
```

Push the newly generated site to the `gh-pages` branch. GitHub Pages should
automatically update the production site within a few minutes.

## Updating Social Media Links

Social media icons appear in the author byline on all article pages and index pages. To update the social media links:

1. **Edit the SOCIAL configuration** in `pelicanconf.py`:
   ```python
   SOCIAL = (
       ("LinkedIn", "https://www.linkedin.com/in/your-profile/"),
       ("Bluesky", "https://bsky.app/profile/your-handle"),
   )
   ```

2. **Update the About page** in `content/pages/about.md` to match your new links:
   ```html
   <a href="https://www.linkedin.com/in/your-profile/" target="_blank" rel="noopener noreferrer">LinkedIn</a>
   ```

The social media icons (LinkedIn and Bluesky SVGs) are automatically rendered in the templates. To add new social platforms, edit the conditional logic in `themes/bootstrap/templates/article.html` and `themes/bootstrap/templates/index.html`.

## GitHub Master to Main Update

```bash
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

## Release Notes

### 2025.07.31

- Publish "Python Kickstart (part 3): Control Flow and Conditionals" article.
- Update article headings to use code formatting for Python keywords.
- Add social media links to author's byline.
- Configure Claude Code.

### 2025.07.09

- Publish "Python Kickstart (part 2)" article.

### 2025.05.21

- Correct a typo in "When Vibe Coding Fails."
- Move to `uv` as our Python package and project manager.

### 2025.05.13

- Publish "When Vibe Coding Fails: Python Kickstart (part 1)" article.
- Set Python version for pyenv.

### 2025.04.17

- Update to a Python 3.13.3 build.
- Update Bootstrap CSS to version 5.3.5.
- Add controllable meta descriptions for all pages.
- Refactor all templates to consistently use 2 spaces.

### 2025.03.03

- Update to Python 3.13.2 build.
- Correct and adjust content in "Python venv" article.

### 2025.02.14

- Publish article "DeepSeek-R1: The Promise and Peril..."

### 2025.02.04

- Update Bluesky links to [@benjaminpatch.com](https://bsky.app/profile/benjaminpatch.com).
- Improve styling of blockquotes.

### 2025.01.30

- Publish article "Simple Python Virtual Environments: Linux and Mac."
- Clean up presentation of information on index pages.
- Enable syntax highlighting of common coding languages with [highlight.js](https://highlightjs.org/).
- Load Bootstrap stylesheet from CDN.
- Create initial dependency declaration with `pip freeze`.

### 2024.12.18

- Evenly round corners on all sides of header and footer.
- Publish article "The Journey of Artificial Intelligence."

### 2024.12.11

- Rebuild as a blog using Pelican.
- Rename "master" git branch to "main."
