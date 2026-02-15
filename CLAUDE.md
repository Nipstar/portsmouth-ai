# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Marketing website for **Andover AI Automation** — an AI automation agency based in Andover, Hampshire, UK. The site targets local small businesses looking for AI voice agents, chatbots, and workflow automation.

**Live domain:** aiautomationandover.co.uk (note: the repo folder says "portsmouth" but the site is for Andover)

## Tech Stack & Build

- **Zero build step.** No frameworks, no bundler, no package manager, no dependencies.
- Single `index.html` (~2250 lines) containing all HTML, CSS (inline `<style>`), and JS (inline `<script>`).
- Vanilla JS only — no libraries.
- Google Fonts loaded via `<link>` (Sora for headings, DM Sans for body text).
- To develop: open `index.html` in a browser. Any static file server works (e.g. `python3 -m http.server`).

## Architecture

### index.html Structure

The file is organised in this order:

1. **`<head>`** — meta tags, Open Graph, JSON-LD structured data (LocalBusiness, Organization, FAQPage), CSS custom properties in `:root`, all CSS
2. **`<body>` HTML sections** (each with a distinct `id`): `hero`, `pain-points`, `services`, `demo`, `how-it-works`, `industries`, `why-us`, `faq`, `contact`
3. **About micro-section** — geo/LLM-optimised blurb after the main content
4. **Footer** — with links to `privacy-policy.html` and `terms.html`
5. **Cal.com embed script** — lazy-loaded via IntersectionObserver
6. **Main JS IIFE** — mobile nav toggle, scroll-reveal animations, waveform bar generation, FAQ accordion (single-open), animated stat counters, contact form submission

### CSS Design System

All colours and fonts are defined as CSS custom properties in `:root` (line ~157). The theme is dark with blue/cyan accents:
- `--bg-primary: #0a0f1c`, `--accent-primary: #3b82f6`, `--accent-secondary: #06b6d4`
- CTA colour: `--accent-cta: #10b981` (green)
- Sections are commented with `/* ── SECTION NAME ── */` markers

### JavaScript Features

All JS lives at the bottom of `index.html` in two `<script>` blocks:
- **Cal.com loader** (~line 2036): lazy-loads the booking widget when the embed container scrolls into view
- **Main JS** (~line 2068): IIFE containing mobile nav, IntersectionObserver-based scroll reveal (`.reveal` → `.visible`), waveform animation bars, FAQ accordion, counter animation with ease-out cubic, and contact form POST

### Contact Form

The form POSTs JSON to an **n8n webhook** endpoint (line ~2229). Fields: name, email, phone, business, message, source, page_url. Includes a honeypot field (`website`) for spam filtering.

### Other Pages

- `privacy-policy.html` and `terms.html` — standalone pages with duplicated CSS (same design system, self-contained)

## SEO Considerations

- Semantic HTML5 with proper heading hierarchy
- Three JSON-LD blocks in `<head>`: LocalBusiness, Organization, FAQPage
- Open Graph + Twitter Card meta tags on every page
- `robots.txt` allows all crawlers; `sitemap.xml` lists the homepage
- Target keywords are woven into copy — preserve keyword density when editing text
- The about micro-section before the footer is specifically optimised for LLM/GEO visibility

## Key Conventions

- All CSS and JS are inline — there are no external `.css` or `.js` files
- CSS sections are delimited by `/* ── SECTION NAME ── */` comment blocks
- HTML sections are delimited by `<!-- ═══ SECTION NAME ═══ -->` comment blocks
- The `.reveal` class + IntersectionObserver pattern is used for scroll animations — add `class="reveal"` to any new element that should animate in
- Responsive breakpoints are handled via `@media` queries within the single `<style>` block
