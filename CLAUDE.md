# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the Jekyll static site for **Riva Refuge** (www.rivarefuge.org), a small secular non-profit. It is deployed to GitHub Pages via GitHub Actions on every push to `master`.

## Commands

```bash
export PATH="/usr/local/opt/ruby@3.2/bin:$PATH"  # Required — macOS system Ruby is too old
bundle install              # Install Ruby dependencies
bundle exec jekyll serve    # Serve locally at http://localhost:4000
bundle exec jekyll build    # Build to _site/
```

No Makefile or package.json — this is a pure Jekyll/Ruby project. Requires Homebrew Ruby 3.2+ (`brew install ruby@3.2`); the macOS system Ruby (2.6) is incompatible with current gems.

## Architecture

### Template Hierarchy

```
_layouts/default.html       # Main wrapper (centered col-md-6 content)
├── _includes/head.html
├── _includes/header.html
│   └── _includes/navigation.html
├── _layouts/page.html      # Used by most content pages
└── _includes/footer.html
```

`_layouts/donation.html` is an alternate layout used for donation-specific pages, with `_includes/headdonation.html` instead of the standard head.

### Custom Liquid Tag

`_plugins/markdown.rb` registers a `{% markdown <filename> %}` tag that loads a file from `_includes/`, runs it through Liquid, then converts it with Kramdown. This allows markdown includes that support template variables (unlike the standard `{% include %}` tag).

### Content Includes

- `_includes/mission.html` — Mission statement, included on the home page and campaigns index
- `_includes/campaigns.md` — Campaign listing (rendered via the custom `{% markdown %}` tag)
- `_includes/donate.html` — Embedded donation form (PayPal legacy button)

### Campaigns

Three campaign sub-pages live under `/campaigns/`:
- `jadelle-family-planning-program/`
- `scholarship-program/`
- `matisi-food-medicine/`

### Plugins

- `_plugins/sitemap_generator.rb` — Generates `/sitemap.xml`
- `_plugins/markdown.rb` — Custom `{% markdown %}` Liquid tag

### Styling

- Bootstrap 5.3.2 via CDN (`_includes/head.html`)
- Font Awesome 6.4.0 via cdnjs CDN (`_includes/head.html`)
- Custom styles in `css/rr-custom.css` (the only local stylesheet)

### Deployment

GitHub Actions workflow (`.github/workflows/jekyll-gh-pages.yml`) builds and deploys to GitHub Pages on every push to `master`. The custom domain `www.rivarefuge.org` is set via the `CNAME` file.
