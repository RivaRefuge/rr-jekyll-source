# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the Astro static site for **Riva Refuge** (www.rivarefuge.org), a small secular non-profit. It is deployed to GitHub Pages via GitHub Actions on every push to `master`.

## Commands

```bash
npm install                 # Install dependencies
npm run dev                 # Serve locally at http://localhost:4321/
npm run build               # Build to dist/
npm run preview             # Preview the dist/ build locally
```

## Architecture

### File Structure

```
src/
  layouts/
    Layout.astro            # Main wrapper: head, nav, content column, footer
  components/
    Nav.astro               # Responsive Bootstrap navbar (active state via menuEntry prop)
    Footer.astro            # Footer: email, Facebook, tagline
    DonateButton.astro      # PayPal Donate SDK button
  assets/
    images/                 # All site images — processed to WebP at build time
  pages/                    # One .astro file per route
    index.astro
    404.astro
    campaigns/
      index.astro
      jadelle-family-planning-program/index.astro
      scholarship-program/index.astro
      matisi-food-medicine/index.astro
    our-history/index.astro
    our-vision/index.astro
    board-of-directors/index.astro
    contact-us/index.astro
    get-involved/index.astro
    thanks/index.astro
public/
  css/rr-custom.css         # Only local stylesheet
  CNAME                     # Custom domain: www.rivarefuge.org
  robots.txt
  favicon.ico / favicon.svg
_source-images/             # Working source files for images (not served)
```

### Layout Props

Every page passes props to `Layout.astro`:

```astro
<Layout title="Page Title" menuEntry="history" description="SEO description">
```

- `title` — page title; home page uses `"Riva Refuge"`, others use `"Page Title | Riva Refuge"`
- `menuEntry` — highlights the active nav item: `home`, `campaigns`, `ourvision`, `getinvolved`, `history`, `board`, `contact`
- `description` — meta description for SEO (falls back to site-wide default if omitted)

### Images

Images live in `src/assets/images/` and are imported at the top of each page:

```astro
---
import { Image } from 'astro:assets';
import hero from '../../assets/images/fp-hero.jpg';
---
<Image src={hero} alt="Description" />
```

- Astro converts images to WebP and infers dimensions automatically
- Hero/first images: add `width={670} loading="eager" fetchpriority="high"`
- All other images: no extra attributes needed (lazy loading is the default)

### Adding a New Page

1. Create `src/pages/<slug>/index.astro`
2. Import `Layout` and any images
3. Pass `title`, `menuEntry`, and `description` props to `Layout`
4. Add the route to `Nav.astro` if it should appear in navigation

### Styling

- Bootstrap 5.3.2 via CDN (in `Layout.astro`)
- Font Awesome 6.4.0 via cdnjs CDN (in `Layout.astro`)
- Custom styles in `public/css/rr-custom.css`

### Deployment

GitHub Actions workflow (`.github/workflows/jekyll-gh-pages.yml`) runs `npm ci && npm run build` and deploys `dist/` to GitHub Pages on every push to `master`.
