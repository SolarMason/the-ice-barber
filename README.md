# The Ice Barber LLC — Website

Family-owned shaved ice serving Northeast Pennsylvania. Single-file PWA with offline support, iOS glassmorphism design, and event-intel contact form.

📞 **(570) 251-1996** · ✉️ **theicebarber@gmail.com**

---

## Deploy to GitHub Pages (drag & drop)

1. Create a new repo on GitHub (e.g. `theicebarber-site`).
2. Click **Add file → Upload files** and drag everything from this zip into the repo root.
3. Commit to `main`.
4. **Settings → Pages → Build and deployment**:
   - **Source:** *Deploy from a branch* (or *GitHub Actions* if using the included workflow)
   - **Branch:** `main` / `(root)`
5. Wait ~30 seconds. Site goes live at `https://<username>.github.io/<repo>/`.

### Custom domain (theicebarber.com)
- **Settings → Pages → Custom domain:** enter `theicebarber.com`, save.
- At your DNS provider, add either:
  - `A` records pointing apex `@` to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  - **or** `CNAME` from `www` → `<username>.github.io`
- Enable **Enforce HTTPS** once GitHub provisions the cert.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | Single-file site (logo embedded, no external assets needed) |
| `manifest.json` | PWA manifest — installable home-screen app |
| `sw.js` | Service worker — offline caching |
| `og-card.png` / `.jpg` | 1200×630 share card for Facebook/iMessage/Twitter |
| `icon-32.png` | Browser favicon |
| `icon-180.png` | Apple touch icon |
| `icon-192.png` / `icon-512.png` | PWA + Android icons |
| `icon-1024.png` | App store / high-res master |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |
| `.github/workflows/deploy.yml` | Optional: auto-deploy on push (uses GitHub Actions) |

## Updating the site

Edit `index.html` directly — everything is in that one file (CSS, JS, embedded logo). Push to `main` and Pages redeploys.

If you change the domain, update these in `index.html`:
- `<link rel="canonical" href="...">`
- `<meta property="og:url" ...>` and `og:image`
- The Schema.org `@id` and `url` fields in the JSON-LD block
