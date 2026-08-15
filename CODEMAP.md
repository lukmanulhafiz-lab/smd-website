# CODEMAP — smd-website
> Dibuat 2026-08-09 · basis commit 37bf309 · regenerate: skill codemap

## Tujuan repo
Situs marketing statis PT Sehat Masa Depan (sehatmasadepan.com). MURNI HTML+CSS —
tanpa build step, tanpa framework, tanpa dependency (bukan Next.js, apa pun kata deskripsi lama).

## Entry point & perintah
- Tidak ada build/server: buka `index.html` langsung, atau preview via browser pane.
- Deploy = push ke `main` → **Netlify** (auto-deploy dari repo `lukmanulhafiz-lab/smd-website`) → Cloudflare di depannya.
  ⚠️ **Bukan GitHub Pages** — dikoreksi 9 Agu 2026 setelah verifikasi: header respons live memuat `X-Nf-Request-Id`,
  apex A = `75.2.60.5` (IP Netlify), dan `www` CNAME ke `musical-faloodeh-529eec.netlify.app`.
  **Clean URL (`/faq` → `faq.html`) berasal dari Netlify**, bukan Cloudflare. Kalau deploy bermasalah, cek dashboard Netlify.
- `CNAME` berisi `sehatmasadepan.com` — JANGAN dihapus/diubah, custom domain mati kalau hilang.

## File penting & perannya
- `index.html` (434 baris) — halaman utama; load `css/styles.css` + `css/v2.css`
- `studio.html` (505 baris) — halaman "Product Studio" mandiri; CSS-nya INLINE (tidak pakai css/), edit terpisah
- `css/styles.css` — entry design system: hanya `@import` 6 file `css/tokens/*` (fonts, colors, typography, spacing, radii, base)
- `css/v2.css` (421 baris) — seluruh style situs v2 ("The Healthy Future"): hero gelap + body terang; theming via atribut `<html data-mood data-motion data-hero>`
- `assets/logo-smd-mark.png` — satu-satunya aset gambar

## Alur & "god file"
`index.html` → `styles.css` → `tokens/*` (nilai warna/font mengalir dari tokens, bukan hardcode di v2.css).
Ubah warna/font → edit `css/tokens/*`; ubah layout/section → edit `css/v2.css`; `studio.html` terpisah total.

## Jebakan
- **`git pull` DULU sebelum kerja apa pun** — repo ini juga diedit langsung via GitHub/sesi lain; clone lokal pernah kedapatan basi 4 commit + nyangkut di branch lama (Agu 2026).
- Folder deploy di Downloads = DECOY BASI — satu-satunya sumber live adalah repo git ini (memory `smd-website-deploy-topology`).
- Lokasi clone lokal tidak lazim: `C:\Users\lukma\belajar\smd-website` (bukan di workspace Claude Code).
- README menyebut `tweaks-panel.jsx` yang SUDAH TIDAK ADA di repo — abaikan; README belum diperbarui.
- Branding wajib ikut skill `sehat-masa-depan-design`; jangan improvisasi warna di luar tokens.
