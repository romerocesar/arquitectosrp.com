# Repository Guidelines

## Project Structure & Module Organization

This repository is a small bilingual static site built with Hugo.

- `hugo.yaml` contains site configuration, language settings, and disabled Hugo output kinds.
- `content/_index.en.md` and `content/_index.es.md` provide the English and Spanish home page content.
- `layouts/_default/baseof.html` defines the shared HTML frame.
- `layouts/index.html` renders the home page and language switcher.
- `static/css/site.css` contains site styles served as a static asset.
- `static/CNAME` configures the custom GitHub Pages domain.

There is currently no dedicated test directory or application source tree.

## Build, Test, and Development Commands

- `hugo server` starts a local development server with live reload. Use the URL printed by Hugo; English is at `/` and Spanish is at `/es/`.
- `hugo --gc --minify` creates a production build and removes unused generated files.
- `hugo` runs a normal local build without minification.

This project does not define `npm`, `make`, or custom test commands.

## Coding Style & Naming Conventions

Use two-space indentation in Hugo templates, YAML, Markdown front matter, and CSS blocks. Keep Hugo templates simple and prefer existing partial-free structure unless reuse becomes necessary.

Content files should follow the existing language suffix pattern: `_index.en.md`, `_index.es.md`. Keep translation keys and page parameters aligned across languages so both localized pages render the same layout.

CSS uses custom properties in `:root`, semantic class names such as `.language-nav` and `.notice`, and responsive rules near the bottom of `static/css/site.css`. Add styles in the same file unless the stylesheet becomes difficult to scan.

## Testing Guidelines

There is no automated test suite. Validate changes by running:

```sh
hugo --gc --minify
```

For visual or content changes, also run `hugo server` and manually check both `/` and `/es/`. Confirm that the language switcher works, copy appears in the intended language, and the page remains usable on narrow screens.

## Commit & Pull Request Guidelines

The current history uses short, imperative commit subjects, for example `initial site under construction`. Keep commit messages concise and focused on one change.

Pull requests should include a brief description, note whether both languages were updated, and mention the Hugo build result. Include screenshots for visible layout or styling changes, especially responsive changes.

## Deployment Notes

The site is intended for GitHub Pages. Repository settings should use **Pages > Build and deployment > Source: GitHub Actions**. Pushes to `main` deploy through the Hugo workflow referenced in the README.
