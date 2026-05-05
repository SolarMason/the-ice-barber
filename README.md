# The Ice Barber LLC — Website

Family-owned shaved ice serving Northeast Pennsylvania.

📞 **(570) 291-7911** · ✉️ **theicebarber@gmail.com** · 🌐 **theicebarber.com**

---

## Pages

| Page | Purpose |
|---|---|
| `index.html` | Homepage — hero, flavors, events, booking form, about |
| `venues.html` | NEPA venue directory — 400+ parks, fire halls, lodges, civic spaces (free public resource) |
| `media.html` | Marketing kit — printable PDFs (business card, flyer, door hanger, postcard, rack card, tear-off, sales sheet, poster) with live previews |

All three share the same nav, footer, color palette, and iOS-glassmorphism styling.

---

## 🚀 Deploying — drag-and-drop to GitHub

This zip is ready to drop into a GitHub repo. There are two paths.

### Path A — Brand-new repo (first time)

1. Go to **github.com/new**.
2. Name the repo (e.g. `theicebarber-site`). Make it **public** (required for free GitHub Pages).
3. **Don't** initialize with a README — leave it empty.
4. On the empty repo page, click **uploading an existing file**.
5. Unzip this file on your computer.
6. Drag **everything inside the unzipped folder** (not the folder itself — the contents) into the GitHub upload area. Make sure hidden files (`.github/`, `.nojekyll`) come along.
7. Commit directly to `main`.
8. **Settings → Pages → Build and deployment → Source:** *GitHub Actions*.
9. Wait ~30 seconds. The included workflow (`.github/workflows/deploy.yml`) will build and publish. Site goes live at `https://<username>.github.io/<repo>/`.

### Path B — Updating an existing repo

1. Unzip this file on your computer.
2. On the repo's main page, click **Add file → Upload files**.
3. Drag **everything from inside the unzipped folder** into the upload area. GitHub will replace the existing files with the same names.
4. Important: drag the contents, not the parent folder. Hidden files (`.github/`, `.nojekyll`) must be included or the workflow won't run.
5. Commit to `main`. The Action redeploys automatically (~30 seconds).

> **Tip**: if hidden files don't show in your file manager, on macOS press `⌘ + Shift + .` in Finder; on Windows enable "Show hidden files" in File Explorer's View menu.

### Custom domain (theicebarber.com)

1. **Settings → Pages → Custom domain:** enter `theicebarber.com`, click **Save**.
2. At your DNS provider, add either:
   - Apex (`@`) `A` records pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **and/or** a `www` `CNAME` pointing to `<username>.github.io`
3. Wait for DNS propagation (a few minutes to a few hours), then enable **Enforce HTTPS** in the Pages settings.

GitHub will create a `CNAME` file in the repo automatically when you set the custom domain — you don't need to add one manually.

---

## File map

```
index.html              ← homepage
venues.html             ← NEPA venue directory
media.html              ← marketing kit page

manifest.json           ← PWA manifest (installable home-screen app)
sw.js                   ← service worker (offline support, cache version v2)

icon-32.png             ← browser favicon
icon-180.png            ← Apple touch icon
icon-192.png            ← Android / PWA icon
icon-512.png            ← high-res PWA icon
icon-1024.png           ← master / app store icon
og-card.png · og-card.jpg ← 1200×630 social share card

media/                  ← downloadable marketing PDFs
  01-business-card.pdf
  02-flyer.pdf
  03-door-hanger.pdf
  04-postcard.pdf
  05-rack-card.pdf
  06-tearoff-flyer.pdf
  07-event-sales-sheet.pdf
  08-poster.pdf
  icebarber-marketing-kit.zip   ← all 8 PDFs bundled
  thumbs/               ← page-1 JPEG previews shown on the media page
    01-business-card.jpg
    02-flyer.jpg
    03-door-hanger.jpg
    04-postcard.jpg
    05-rack-card.jpg
    06-tearoff-flyer.jpg
    07-event-sales-sheet.jpg
    08-poster.jpg

.github/workflows/deploy.yml  ← auto-deploys on push to main
.nojekyll                     ← tells GitHub Pages to skip Jekyll preprocessing
```

---

## Updating content

- **Edit text/colors/layout**: open the relevant `.html` file in any editor; CSS, JS, and embedded logo are all inline. Save and push.
- **Replace a marketing PDF**: drop the new file into `media/` keeping the same filename. The thumbnail in `media/thumbs/` will look stale until you regenerate it (see below).
- **Add or remove a venue** on `venues.html`: each venue is a `<details class="venue">` block — duplicate one and edit fields.
- **Bust the service worker cache**: bump the `CACHE = 'icebarber-v2'` line in `sw.js` to `v3`, etc. Returning visitors will fetch fresh assets on next load.

### Regenerating PDF thumbnails (optional)

If you replace a PDF and want a new preview, on a machine with `poppler-utils` installed:

```bash
cd media
pdftoppm -r 100 -jpeg -jpegopt quality=85 -f 1 -l 1 -singlefile \
  02-flyer.pdf thumbs/02-flyer
```

The thumbnails on the media page automatically pick up the new file once you push.

---

## Tech notes

- **No build step**: pure HTML/CSS/JS, all assets relative paths. Works behind any static host.
- **PWA**: installable on iOS/Android home screens; offline support via `sw.js`.
- **iOS-Safari form layout**: the `#book` form uses explicit grid breakpoints to avoid Safari's auto-shrinking inputs on small screens.
- **Accessibility**: nav has `aria-label`, every image has `alt`, decorative SVGs use `aria-hidden`. Color-contrast tested for WCAG AA.
- **SEO**: each page has its own `<title>`, meta description, canonical URL, and Open Graph tags. Schema.org `LocalBusiness` JSON-LD on the homepage.

---

Built for Noel — family-owned, NEPA-proud.
