# Michael's Personal Website

See the website at [michael-n.com](https://michael-n.com/)! Theme adapted from [David Darnes](https://github.com/dngdial/garth).

## Overview

This repository is a small Jekyll site. Jekyll takes Markdown content, combines it with HTML layouts and reusable includes, compiles Sass into CSS, and outputs the final static site into `_site/`.

At a high level:

- `_config.yml` stores site-wide settings such as the title, navbar links, base URL, and Jekyll options.
- Root Markdown files like `index.md`, `blog.md`, `resume.md`, and `404.md` define top-level pages.
- `_posts/` contains blog posts.
- `page/` contains additional standalone pages.
- `_layouts/` defines the page types.
- `_includes/` contains reusable page fragments and shared scripts.
- `_data/` stores structured content that templates can loop over.
- `assets/` contains styles, images, the favicon, and other static files.

## How The Site Is Built

Jekyll renders each page in layers:

1. A Markdown file declares a layout in its front matter.
2. The layout wraps that page's content.
3. Shared includes provide repeated pieces like the header, footer, navigation, and post metadata.
4. `assets/styles.scss` is compiled into `assets/styles.css`.
5. The finished site is written to `_site/`.

Example:

- `index.md` uses the `home` layout.
- `_layouts/home.html` passes the homepage title and content into `_includes/page-frame.html`.
- `_includes/page-frame.html` adds the shared header, main content wrapper, and footer.
- `_layouts/default.html` provides the outer HTML document, loads styles, fonts, and shared scripts.

## Directory Guide

### Content

- `index.md`: homepage content.
- `blog.md`: writing index page.
- `resume.md`: resume page.
- `404.md`: not found page.
- `page/`: extra standalone pages.
- `_posts/`: blog posts named with the usual Jekyll format `YYYY-MM-DD-title.md`.

### Layouts

- `_layouts/default.html`: outer HTML shell for every page.
- `_layouts/home.html`: homepage layout.
- `_layouts/page.html`: general-purpose page layout.
- `_layouts/blog.html`: writing index layout that renders the intro text plus the post list.
- `_layouts/post.html`: individual blog post layout with MathJax and Giscus.

### Includes

- `_includes/page-frame.html`: shared page structure used by the main layouts.
- `_includes/site-header.html`: top header area.
- `_includes/site-nav.html`: navbar links from `_config.yml`.
- `_includes/site-footer.html`: footer content.
- `_includes/site-logo.html`: logo image rendering.
- `_includes/post-list.html`: loops through posts for the writing page.
- `_includes/post-meta.html`: date, categories, and reading time for posts.
- `_includes/publication-card.html`: reusable homepage publication card.
- `_includes/site-scripts.html`: small shared JavaScript, currently for publication gallery dot navigation.
- `_includes/mathjax.html`: MathJax setup for posts.
- `_includes/giscus.html`: comments embed for posts.

### Data

- `_data/publications.yml`: homepage publication card data. Each entry becomes one card on the homepage.

### Assets

- `assets/styles.scss`: main stylesheet entry point.
- `assets/images/`: images used throughout the site.
- `assets/slides/`: downloadable slide decks and PDFs.
- `assets/favicon.ico`: browser favicon.

## Common Editing Tasks

### Update homepage text

Edit `index.md`.

### Add, remove, or reorder homepage publication cards

Edit `_data/publications.yml`.

The homepage loops through that file and renders each entry with `_includes/publication-card.html`.

### Change the shared page structure

Edit `_includes/page-frame.html` if you want to change the common content wrapper used by the main layouts.

### Change the site header, nav, or footer

Edit these files:

- `_includes/site-header.html`
- `_includes/site-nav.html`
- `_includes/site-footer.html`

Navbar links themselves are configured in `_config.yml` under `navbar:`.

### Add a new blog post

Create a new file in `_posts/` named like:

```md
2026-04-07-my-post.md
```

with front matter like:

```yaml
---
layout: post
title: My Post Title
categories: [notes]
---
```

### Add a new standalone page

Add a Markdown file either at the repo root or inside `page/` with front matter such as:

```yaml
---
layout: page
title: My Page
permalink: /my-page/
---
```

### Change styles

Edit `assets/styles.scss`.

This file imports the theme styles and contains site-specific customizations.

## Local Development

Install Jekyll following the [official installation guide](https://jekyllrb.com/docs/installation/).

Then run:

```bash
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000` in your browser.

## Build Output

- `_site/` is generated output.
- You generally should not edit `_site/` by hand, because Jekyll rebuilds it from the source files in this repository.
