# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file static HTML marketing website for **Wood&Craft**, a handcrafted furniture and woodworking business based in Bangkok, Thailand. The entire site lives in one file: `woodcraft-modern (1).html`.

## Architecture

**No build tools, no framework, no package manager.** Everything is self-contained in a single HTML file:

- **CSS**: Embedded in a `<style>` block (lines 8–1058) with CSS custom properties defining the design system
- **HTML**: Semantic sections — nav, hero, marquee, categories, gallery, story, process, testimonials, contact form, footer
- **JS**: Vanilla JavaScript at the bottom of `<body>` (lines 1443–1495) — no imports, no modules

To preview the site, open the HTML file directly in a browser. There is no dev server, build step, or local dependency to install.

## Design System

All colors and spacing are defined as CSS custom properties on `:root`:

```css
--bg, --bg-elevated, --bg-card, --surface   /* dark background layers */
--gold, --gold-light, --gold-dim            /* primary accent color #C8A45C */
--cream, --cream-dim, --cream-muted         /* text colors */
--warm-gray, --border, --border-hover
```

Fonts: `Cormorant Garamond` (serif headings/quotes) and `Outfit` (sans-serif body), loaded from Google Fonts.

## JavaScript Behaviors

Four behaviors, all vanilla JS, no libraries:

1. **Cursor glow** — radial gradient that follows mouse (desktop only, `pointer: fine` media query)
2. **Navbar shrink** — adds `.scrolled` class after 80px scroll
3. **Mobile menu** — toggles `.open` on `#navLinks`
4. **Scroll reveal** — `IntersectionObserver` adds `.visible` to `.reveal` elements; uses `.reveal-delay-1` through `.reveal-delay-4` for staggered timing
5. **Contact form** — `handleSubmit()` shows a fake success state for 3 seconds, then resets

## Images

All images are Unsplash CDN URLs embedded directly in the HTML. No local image assets exist.

## Responsive Breakpoints

- `≤ 1024px` — tablet layout adjustments
- `≤ 768px` — mobile: nav collapses to hamburger, single-column grids
- `≤ 480px` — small mobile: further text/layout reductions
