# Likewater — corporate site + EverRecall Anki Migration Help

This repository hosts two generated static sites side by side, published via GitHub Pages:

- **`/`, `/ja/`, `/en/`, `/everrecall/`, `/privacy/`, `/terms/`, `/support/`** — the Likewater
  corporate site (company name, app list, privacy policy, terms of service, contact). Source:
  `web/build-site.mjs` in the private `Hippocampus` repository.
- **`/anki-migration/<lang>/`** — the "Moving from Anki" help guide for EverRecall, in 10
  languages. Source: `Hippocampus/Resources/Help/anki-migration/<lang>.md` and
  `web/build.mjs`, both in the private `Hippocampus` repository.
- **`/privacy.html`, `/terms.html`** — flat, English-only copies of the privacy policy /
  terms of service. These exist because EverRecall's bundled `LegalLinks.json` fallback
  already points at these exact flat URLs; they are generated from the same content as
  `/en/privacy/` and `/en/terms/`.

**Source of truth**: this repository does not contain any manuscript. It only holds the
generated HTML/CSS output. Do not edit the HTML files directly — they are overwritten on
every deploy. Deploys automatically via a GitHub Actions workflow in the `Hippocampus`
repo that pushes the freshly built `web/dist/` here on every relevant change.

## Custom domain: `likewater.works`

The site is served at `https://likewater.works/` (registered 2026-09-29 at Cloudflare; DNS
A/AAAA records point at GitHub Pages, `www` is a CNAME to `ssokajimass-web.github.io`).
The `CNAME` file in this repository is **generated on every deploy** by
`web/build-site.mjs` (`CONFIG.customDomain`), because the deploy replaces this repository's
contents wholesale. Do not add it by hand. `likewater.app` was never registered and is not used.

Every link on the site is relative, so it works identically from
`https://ssokajimass-web.github.io/everrecall-help/` (which GitHub redirects to the custom
domain) and from `https://likewater.works/`.
