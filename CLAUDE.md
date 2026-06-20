# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static Russian-language landing page for Yulia Hovich, a licensed Israeli tour guide. No build tools, no npm, no dependencies — just HTML, CSS, and vanilla JS.

**Live URL:** `https://hovichyulia.netlify.app/`

## Running Locally

Open `index.html` directly in a browser — no server needed. For a proper local server (needed to test NFC/vCard flows):

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## File Structure

- `index.html` — main landing page (all HTML + CSS + JS in a single file, ~1300 lines)
- `contact.html` — NFC business card page: one-tap save contact + WhatsApp button
- `accessibility.html` — Accessibility declaration (WCAG 2.0 AA / Israeli standard 5568), in RU/EN/HE
- `yulia-hovich.vcf` — vCard downloaded from `contact.html`
- `images/yulia.jpeg` — portrait used in both `index.html` and `contact.html`
- `Versions/` — archived older versions, not deployed

## Architecture of `index.html`

All CSS lives in a single `<style>` block, JS in a single `<script>` block at the bottom. Sections in order:

1. `<head>` — Schema.org JSON-LD (LocalBusiness + Person + FAQPage), Open Graph, Google Fonts preconnect
2. CSS custom properties at `:root` — color palette (`--primary: #1AA7B5`, `--accent: #E8B86D`), typography, shadows, breakpoints
3. HTML sections: `#hero` → `#about` → `#tours` → `#gallery` (comment `<!-- GALLERY -->`) → `#reviews` → `#faq` → `#contact` → `<footer>`
4. JS — IntersectionObserver for scroll animations, mobile nav toggle, gallery lightbox

## Contact Data — Update in Three Places

When changing contact info, update **all three** files:

| Field | Search for |
|---|---|
| WhatsApp number | `972506887446` |
| Email | `hovich.yulia@gmail.com` |
| Instagram handle | `gid.israel.yulia` |

Files affected: `index.html`, `contact.html`, `yulia-hovich.vcf`.

## Adding Gallery Photos

Find the `<!-- GALLERY -->` comment in `index.html`. Copy-paste template snippets from the comment block (normal / wide / tall variants). All image paths must be prefixed with `images/`.

## Design Tokens

Primary teal: `#1AA7B5` / `--primary`  
Gold accent: `#E8B86D` / `--accent`  
Fonts: Playfair Display (headings) + Inter (body)  
Mobile breakpoint: `768px`

## Deployment

Drag-and-drop the project folder to [app.netlify.com/drop](https://app.netlify.com/drop) — no config needed.
