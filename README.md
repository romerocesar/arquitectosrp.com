# arquitectosrp.com

Simple bilingual static site built with [Hugo](https://gohugo.io/) and deployed with GitHub Pages.

## Local development

```sh
hugo server
```

Then open the local URL printed by Hugo. English is available at `/` and Spanish at `/es/`.

## Production build

```sh
hugo --gc --minify
```

## GitHub Pages

This repo includes a GitHub Actions workflow at `.github/workflows/hugo.yml`.

In the repository settings, set **Pages > Build and deployment > Source** to **GitHub Actions**. Pushes to `main` will then build and deploy the site.
