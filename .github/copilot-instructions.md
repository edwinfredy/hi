# Copilot Instructions

## Architecture
- This is a small, static React personal site built with Vite and deployed to GitHub Pages.
- `index.html` provides the document shell and page metadata; `src/main.jsx` mounts the React app.
- `src/App.jsx` contains the complete page content and shared semantic structure.
- `assets/css/style.css` contains global styles and `assets/css/normalize.css` is vendored Normalize.css v8.0.1.
- Keep external page links explicit with `target="_blank"` and `rel="noopener noreferrer"`.

## Local workflow
- Dependencies are managed with npm and declared in `package.json`.
- Run `npm install` once, then `npm run dev` for a local preview.
- Run `npm run build` to verify the production output in `dist/`; `dist/` and `node_modules/` are generated and gitignored.

## Deployment
- `.github/workflows/deploy.yml` builds and deploys the Vite output to GitHub Pages on pushes to `main` or manual `workflow_dispatch` runs.
- The site is served from the custom domain `edwinfredy.com`, so Vite's root base path is appropriate.
