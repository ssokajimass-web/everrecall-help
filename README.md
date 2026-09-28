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

## Activating the `likewater.app` custom domain

Once the `likewater.app` domain is registered, do the following in **one commit** to this
repository:

1. Create a file named `CNAME` at the repository root containing exactly one line:
   `likewater.app`
2. In this repository's Settings → Pages, set the custom domain to `likewater.app` and wait
   for DNS verification, then enable "Enforce HTTPS".
3. In the private `Hippocampus` repo, update `CONFIG.baseURL` in `web/build-site.mjs` from
   `https://ssokajimass-web.github.io/everrecall-help` to `https://likewater.app` (this only
   affects OGP/canonical tags — all internal links are relative, so nothing else needs to
   change), then push to `main` so the next deploy regenerates the site with the new
   canonical URLs.

No other file needs to change — every link on the site is relative, so it keeps working
identically whether it's served from `https://ssokajimass-web.github.io/everrecall-help/`
or from `https://likewater.app/`.
