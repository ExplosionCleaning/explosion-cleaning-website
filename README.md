# Explosion Cleaning Service

Marketing website for **Explosion Cleaning Service**, a residential and commercial cleaning company serving San Diego County, CA. It is a fast, static, one-page landing site with services, pricing, reviews, a home decorating & styling offer, FAQ, service area map, and an instant cleaning estimate form.

**Live site:** https://explosioncleaningca.com

## Tech

- Plain HTML, no build step
- [Tailwind CSS](https://tailwindcss.com) via CDN
- [Phosphor Icons](https://phosphoricons.com) and Google Fonts (Playfair Display, Manrope, Alex Brush)
- [FormSubmit](https://formsubmit.co) for the estimate form (no backend)

## Project structure

| File | Purpose |
| --- | --- |
| `index.html` | The one-page site |
| `thank-you.html` | Page shown after the estimate form is submitted (`noindex`) |
| `404.html` | Custom not-found page (`noindex`) |
| `sitemap.xml`, `robots.txt` | Search engine files (the homepage is the only indexed page) |
| `favicon.ico`, `favicon-*.png`, `apple-touch-icon.png`, `android-chrome-*.png`, `site.webmanifest` | Favicon / app icons |
| `Media/` | Logo and photos |

## Run locally

No install needed. From the project folder:

```bash
python -m http.server 5500
```

Then open http://localhost:5500. Serve from the folder root: pages use root-absolute paths such as `/favicon.ico` and `/Media/...`.

## Estimate form

The form in `index.html` posts to FormSubmit at `https://formsubmit.co/explosioncleaningsd@gmail.com` and redirects to `https://explosioncleaningca.com/thank-you.html` (the `_next` hidden field).

The first time the form is submitted, FormSubmit emails a one-time activation link to that inbox. Click it once, otherwise submissions are not delivered.

## Deployment (Cloudflare Pages)

This is a static site with no build step.

1. In Cloudflare, go to **Workers & Pages > Create > Pages > Connect to Git** and select this repository.
2. Build settings:
   - **Framework preset:** None
   - **Build command:** leave empty
   - **Build output directory:** `/` (the repository root)
3. Deploy. Every push to `main` redeploys automatically.
4. Add the custom domain `explosioncleaningca.com` under **Custom domains**.

Notes:
- `404.html` in the root is served automatically by Cloudflare Pages for any missing URL.
- `thank-you.html` and `404.html` carry `noindex, nofollow`, and only the homepage is listed in `sitemap.xml`.

## Before / after launch checklist

- [ ] Activate FormSubmit (see above)
- [ ] Replace the `#` placeholder footer social links (the storefront icon is a placeholder for Google Business Profile)
- [ ] The logo (`Media/Explosion Cleaning Service Logo.png`) is about 5 MB. Compress it for faster page loads
