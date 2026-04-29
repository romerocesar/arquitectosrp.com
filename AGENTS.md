# Repository Guidelines

## Project Structure & Module Organization

This repository is a small bilingual static site built with Hugo and the Arcana theme via Hugo Modules.

- `hugo.yaml` contains site configuration, language settings, and disabled Hugo output kinds.
- `go.mod` and `go.sum` pin the Arcana Hugo Module dependency.
- `content/_index.en.md` and `content/_index.es.md` provide the English and Spanish home page content.
- `data/en/homepage.yml` and `data/es/homepage.yml` configure Arcana homepage sections.
- `static/CNAME` configures the custom GitHub Pages domain.

There is currently no dedicated test directory or application source tree.

## Build, Test, and Development Commands

- `hugo mod tidy` updates `go.mod` and `go.sum` after module import changes.
- `hugo server` starts a local development server with live reload. Use the URL printed by Hugo; English is at `/` and Spanish is at `/es/`.
- `hugo --gc --minify` creates a production build and removes unused generated files.
- `hugo` runs a normal local build without minification.

This project does not define `npm`, `make`, or custom test commands.

## Coding Style & Naming Conventions

Use two-space indentation in Hugo templates, YAML, Markdown front matter, and CSS blocks. Prefer theme configuration and data files over local template overrides.

Content files should follow the existing language suffix pattern: `_index.en.md`, `_index.es.md`. Keep translation keys and page parameters aligned across languages so both localized pages render the same layout.

For Arcana-specific styling, prefer `assets/sass/custom.scss` if custom styles are needed. Avoid editing downloaded module files.

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
