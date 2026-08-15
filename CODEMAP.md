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
- `index.html` — halaman utama; load `css/styles.css` + `css/v2.css`. Sejak 16 Agu 2026 bersuara PERUSAHAAN (leadership/team), bukan profil pribadi — jangan kembalikan framing "founder's career"
- `about.html` — halaman About/Team (16 Agu 2026): fakta legal (NIB/KBLI/PMDN), prinsip kerja, kartu leadership (Hafiz + Prista/partnership@ TANPA asosiasi klien). Person schema `#founder` jobTitle `["Founder","Director"]` harus sinkron dengan index
- `faq.html` — FAQ registrasi + FAQPage schema (teks pertanyaan schema WAJIB sama persis dengan heading terlihat)
- 4 halaman layanan `regulatory-advisory` / `digital-health-strategy` / `capacity-building` / `ai-data-governance` — pakai kelas bersama `.svc-*` di `css/v2.css`, nav `class="nav scrolled"` hardcoded
- `studio.html` — halaman "Product Studio" mandiri (noindex); CSS-nya INLINE (tidak pakai css/), edit terpisah
- `css/styles.css` — entry design system: hanya `@import` 6 file `css/tokens/*` (fonts, colors, typography, spacing, radii, base)
- `css/v2.css` — seluruh style situs v2 ("The Healthy Future") + kelas `.svc-*` halaman layanan; theming via atribut `<html data-mood data-motion data-hero>`
- `sitemap.xml` — 7 URL (semua kecuali studio); `assets/logo-smd-mark.png` + `assets/og-cover.png` — aset gambar

## Alur & "god file"
`index.html` → `styles.css` → `tokens/*` (nilai warna/font mengalir dari tokens, bukan hardcode di v2.css).
Ubah warna/font → edit `css/tokens/*`; ubah layout/section → edit `css/v2.css`; `studio.html` terpisah total.

## Jebakan
- **`git pull` DULU sebelum kerja apa pun** — repo ini juga diedit langsung via GitHub/sesi lain; clone lokal pernah kedapatan basi 4 commit + nyangkut di branch lama (Agu 2026). Cek juga `git status` — sesi lain bisa meninggalkan perubahan belum ter-commit; JANGAN ikut-push pekerjaan setengah jadi milik sesi lain.
- **Netlify menulis ulang link internal di HTML live** — `href="about.html"` di repo tampil live sebagai `href='/about'` (clean URL + kutip tunggal). Verifikasi terhadap HTML live harus grep bentuk clean-URL, bukan markup repo.
- Folder deploy di Downloads = DECOY BASI — satu-satunya sumber live adalah repo git ini (memory `smd-website-deploy-topology`).
- Lokasi clone lokal tidak lazim: `C:\Users\lukma\belajar\smd-website` (bukan di workspace Claude Code).
- README menyebut `tweaks-panel.jsx` yang SUDAH TIDAK ADA di repo — abaikan; README belum diperbarui.
- Branding wajib ikut skill `sehat-masa-depan-design`; jangan improvisasi warna di luar tokens.
