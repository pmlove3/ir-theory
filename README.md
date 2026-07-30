# Academic Profile Website

A [Quarto](https://quarto.org)-based academic profile website for an International Relations scholar, built to execute R code (via `knitr`) in pages and blog posts.

## Structure

- `index.qmd` — homepage / bio (About page)
- `research.qmd` — research agenda and publications
- `teaching.qmd` — courses taught
- `cv.qmd` — CV summary and PDF download (drop your CV at `files/cv.pdf`)
- `blog/` — Quarto blog listing (`blog/index.qmd`) and posts (`blog/posts/<slug>/index.qmd`)
- `_quarto.yml` — site configuration (navbar, theme, etc.)

## Customizing

Search the `.qmd` files for bracketed placeholders (e.g. `[Your Name]`, `[Institution]`) and replace them with your details. Update the email/GitHub/Scholar/LinkedIn links in `_quarto.yml` and `index.qmd`, and swap `profile.svg` for a real photo (update the `image:` field in `index.qmd` accordingly).

## Local development

Requires [Quarto](https://quarto.org/docs/get-started/) and [R](https://www.r-project.org/) with the `rmarkdown` and `knitr` packages installed:

```sh
install.packages(c("rmarkdown", "knitr"))
```

Preview the site locally:

```sh
quarto preview
```

Render the site to `_site/`:

```sh
quarto render
```

## Deployment

`.github/workflows/publish.yml` renders the site with R/knitr and publishes it to the `gh-pages` branch on every push to `master`. Enable GitHub Pages for this repository with the source set to the `gh-pages` branch (Settings → Pages) after the first workflow run.
