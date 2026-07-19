# Morgun Database Solutions (MDS) — website

A small, fast, static "face of the company" site. Plain HTML + CSS, no build step.

## Files
```
index.html          # the whole page (all sections)
styles.css          # styling + light/dark theming
assets/
  logo-mark.svg     # network-nodes "M" mark (scalable, theme-aware)
  favicon.svg       # browser-tab icon
```

## Preview locally
```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Editing
- **Text/content:** edit `index.html`. Sections marked `<!-- EDIT ME -->` are placeholder copy.
- **Contact email:** search `index.html` for `amorgun@morgunsolutions.com` and replace with a company address if you get one.
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
