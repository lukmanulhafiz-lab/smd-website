# PT Sehat Masa Depan — Website

Static marketing site for **sehatmasadepan.com**. Pure HTML + CSS — no build step, no framework, no dependencies to install.

## Structure

```
index.html          Main page (hero, sections, inquiry form, GA4)
studio.html         Product Studio subpage — standalone, CSS inlined (noindex)
css/styles.css      Design-system entry point: @imports css/tokens/*
css/tokens/         Fonts, colors, typography, spacing, radii, base
css/v2.css          Site styles v2 ("The Healthy Future"): dark hero + light body,
                    themed via <html data-mood data-motion data-hero>
assets/             Logo
CNAME               Custom domain (sehatmasadepan.com) — do not remove
CODEMAP.md          Repo map for AI-assisted work — keep in sync with structure
```

Colors and fonts flow from `css/tokens/*` — change values there, not inline in `v2.css`.

## Deploy

GitHub Pages, source: `main` branch root. Push to `main` → Pages rebuilds (~1 min).
The domain is fronted by Cloudflare with clean URLs: `studio.html` is served at `/studio` (both resolve — not a bug).

## Notes

- **Fonts** load from the Google Fonts CDN (`css/tokens/fonts.css`: Plus Jakarta Sans, JetBrains Mono); `studio.html` loads its own. Icons on `index.html` load Lucide from unpkg. Both need internet at page load; the site still renders without them.
- **Inquiry form** (`#inquiryForm`) opens a pre-filled email to `halo@sehatmasadepan.com`. To wire a real backend, replace its submit handler near the bottom of `index.html`.
- **Analytics**: GA4 (`G-6TJ0G8SN38`) on `index.html` only.
- **Contact details** (phone, email, WhatsApp `628111441992`) live in `index.html` — update there if they change.
