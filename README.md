# PT Sehat Masa Depan — Website

Static marketing site. No build step, no dependencies to install — just static files.

## Structure

```
index.html          Main page
css/styles.css      Design-system tokens (fonts, colors, type, spacing) — bundled
css/v2.css          Site styles (hero, sections, tweaks theming)
tweaks-panel.jsx    Optional in-page controls (mood / motion / hero style)
assets/             Logo
```

## Deploy

### GitHub Pages
1. Push these files to the repo root (or a `/docs` folder).
2. Repo → Settings → Pages → Source: `main` branch, root (or `/docs`).
3. Live at `https://<user>.github.io/<repo>/`.

The included `.nojekyll` file tells Pages to serve the files as-is.

### Any static host (Netlify, Vercel, Cloudflare Pages, S3)
Upload the folder as-is. `index.html` is the entry point.

## Notes
- Fonts load from Google Fonts; React/Babel (for the tweaks panel) load from unpkg CDN. Both need internet access at page load. The site renders fully without them if a CDN is blocked — the tweaks panel simply won't appear.
- The inquiry form opens a pre-filled email to `halo@sehatmasadepan.com`. To wire a real backend/email service, replace the `#inquiryForm` submit handler near the bottom of `index.html`.
- Contact: update phone, email, and WhatsApp number (`628111441992`) in `index.html` if they change.
