# Copilot Instructions

## Architecture
- This is a small, static Jekyll 4 personal site, with no application framework or JavaScript runtime.
- `index.md` is the only page and uses the `default` layout; page content is Markdown plus inline HTML (`<br>`, `<b>`).
- `_layouts/default.html` defines the complete document shell: metadata, normalized and custom CSS, header, `<main>`, and footer.
- `_config.yml` supplies site-wide `title`, `description`, and `repository`; `_config.yml` title is rendered in the layout and footer.
- The site has no collections, posts, plugins, data files, Sass pipeline, or custom Ruby code.

## Key files
- Edit visible copy and external links in `index.md`; retain the YAML front matter and `layout: default`.
- Keep shared HTML structure in `_layouts/default.html`, not duplicated in page files.
- Make global visual changes in `assets/css/style.css`; it currently uses plain CSS with a flex-column body and centered, flex-growing `main`.
- `assets/css/normalize.css` is vendored Normalize.css v8.0.1 and should not be hand-modified casually.
- Deployment metadata belongs in `_config.yml` and `.github/workflows/jekyll.yml`, not in page code.

## Jekyll conventions
- Use Jekyll/Liquid filters for generated paths, especially `relative_url`, as in `_layouts/default.html`.
- Preserve the front-matter delimiter format (`---`) and Liquid tags such as `{{ content }}` and `{% if page.title %}`.
- Keep external page links explicit with `target="_blank"` and `rel="noopener noreferrer"`, matching `index.md`.
- Use existing HTML only when Markdown cannot express the needed formatting.

## Local workflow
- Dependencies are managed by Bundler and declared in `Gemfile`; `Gemfile.lock` pins Jekyll 4.4.1 and Bundler 4.0.20.
- Run `bundle install` once, then `bundle exec jekyll serve` for a local preview.
- Run `bundle exec jekyll build` to verify output in `_site/`; `_site/` is generated and gitignored.
- There is no test suite or lint configuration in the repository; validate builds and inspect the rendered page locally.

## Deployment
- `.github/workflows/jekyll.yml` deploys to GitHub Pages on pushes to `main` or manual `workflow_dispatch` runs.
- The workflow uses Ruby 4.0.7 and `bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"` with `JEKYLL_ENV=production`.
- Generated assets and base URLs must remain compatible with Jekyll's `relative_url` filter and the Pages base path.
