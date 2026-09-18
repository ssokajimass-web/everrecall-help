# EverRecall — Anki Migration Help

Generated static site for the "Moving from Anki" help guide, available in 10 languages.

- **Source of truth**: this repository does not contain the manuscript. The Markdown source
  (`Hippocampus/Resources/Help/anki-migration/<lang>.md`) and the build script (`web/build.mjs`)
  live in the private `Hippocampus` repository.
- **This repository** only holds the generated HTML/CSS output, published via GitHub Pages.
- Deploys automatically via a GitHub Actions workflow in the `Hippocampus` repo that pushes
  the freshly built `web/dist/` here on every change to the manuscript.

Do not edit the HTML files directly — they are overwritten on every deploy.
