# OpenS2P website

Static, dependency-free landing site for opens2p.org. Auto-detects each visitor's
browser language (9 languages) and lets them switch manually. No build step —
just HTML/CSS/vanilla JS.

## Files

- `index.html` — page structure and content (English strings; live text is swapped by `i18n.js`)
- `style.css` — styling (brand colors, layout, RTL support for Arabic)
- `i18n.js` — translations for en/es/fr/de/pt/zh/ja/hi/ar + language detection & switcher
- `CNAME` — points GitHub Pages at `opens2p.org`

## Deploy

DNS is already set up (Namecheap A/CNAME records + GitHub Pages custom domain). To publish
a change, just commit and push to `main`:

```
git add .
git commit -m "Update site"
git push
```

GitHub Pages rebuilds automatically within a minute or two. Hard-refresh the browser
(Cmd+Shift+R) if you don't see changes right away — browsers cache aggressively.

## Editing content

All visible text lives in two places:
1. English fallback text is inline in `index.html` (each element also has a `data-i18n="key"` attribute).
2. `i18n.js` has one JS object per language keyed by the same `data-i18n` keys.

To change copy: edit the English text in `index.html` for the fallback, **and** update the
matching key in the `en` block of `i18n.js` (they should stay identical) plus any other
languages you want updated. If you add a new `data-i18n` key to the HTML, add it to every
language object in `i18n.js` or that string will silently stay in English for other locales.

## Known placeholders to fill in before promoting the site

- **Contact form**: connected — posts to `https://formspree.io/f/mykqaqpw` (Formspree
  account under `opens2p@gmail.com`). Submissions forward to that inbox automatically.
- **Analytics**: connected — GoatCounter, dashboard at `opens2p.goatcounter.com` (visits,
  referrers, countries).
- Sponsor button points to `https://github.com/sponsors/opens2p` — GitHub Sponsors
  application in progress; link will 404 until the account is approved.
- `CONTRIBUTING.md` is linked from the Contribute section — lives in the `OpenS2P` code
  repo (`github.com/opens2p/OpenS2P`), confirmed working.
- LinkedIn footer link points to `linkedin.com/company/opens2p` — create the Company Page
  first (see `linkedin_content.md`) or the link will 404 until then.
