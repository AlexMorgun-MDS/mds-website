# Morgun Database Solutions (MDS) — website

A small, fast, static "face of the company" site. Plain HTML + CSS, no build step.

## Files
```
index.html          # the whole page (all sections)
styles.css          # styling + light/dark theming
assets/
  logo-mark.svg           # network-nodes "M" mark, adapts to theme (used in-page)
  logo-mark-black.svg     # mark only, black — for light backgrounds
  logo-mark-white.svg     # mark only, white — for dark backgrounds
  logo-lockup-black.svg   # mark + "MDS" wordmark, black — for light backgrounds
  logo-lockup-white.svg   # mark + "MDS" wordmark, white — for dark backgrounds
  favicon.svg             # browser-tab icon
  png/                    # transparent PNG exports at 512 / 1024 / 2048 px
```

### Which logo file to use
- **`logo-mark.svg`** inherits the surrounding text color, so it only works *inside* the styled site. Don't use it externally.
- **Mark only** (square) — avatars, favicons, app icons, social profile pictures, tight square spaces.
- **Lockup** (mark + "MDS", ~3.2:1) — email signatures, letterheads, slide decks, invoices, sponsor walls.
- **SVG vs PNG:** prefer **SVG** — it scales to any size with no quality loss. Use the **PNG** exports in `assets/png/` only where SVG isn't accepted (many email clients, LinkedIn, Word/PowerPoint). All PNGs have transparent backgrounds.
- Pick **black** for light backgrounds and **white** for dark ones. The white version is invisible on white — that's expected, not a broken file.

The lockup's "MDS" wordmark is Space Grotesk Bold **converted to vector outlines**, so it renders identically everywhere without the font being installed.

## Preview locally
```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Editing
- **Text/content:** edit `index.html`. Sections marked `<!-- EDIT ME -->` are placeholder copy.
- **Contact email:** it's set in `index.html` (currently `amorgun@morgunsolutions.com`) — search for it there to change it.
- **Colors/spacing:** edit the CSS variables at the top of `styles.css`.

## Deploy — GitHub Pages (free, current setup)
The site auto-deploys on every push to `main`.

1. Push to the `mds-website` repo on GitHub.
2. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / root**.
3. Add your custom domain in that same Pages screen (writes a `CNAME` file).

### Squarespace DNS (one-time, done in the Squarespace dashboard)
In **Squarespace → Domains → (your domain) → DNS Settings**, add:

**For a `www` subdomain (recommended):**
| Type  | Host | Value                          |
|-------|------|--------------------------------|
| CNAME | www  | `AlexMorgun-MDS.github.io`      |

**For the apex/root domain**, add four A records pointing to GitHub Pages:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
GitHub issues a free HTTPS certificate automatically once DNS resolves (can take up to ~24h, usually much faster).

## Alternative host — Cloudflare Pages (also free)
1. Create a free Cloudflare account → **Pages → Connect to Git** → pick this repo.
2. Build command: *(none)* · Output directory: `/`.
3. **Custom domains → Set up a domain**, then add the CNAME it gives you to Squarespace DNS.
