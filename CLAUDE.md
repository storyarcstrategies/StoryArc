# CLAUDE.md — StoryArc Strategies

## Project overview

getstoryarc.com — a narrative strategy consultancy for crypto and fintech companies.

**Stack:** Astro 5 (static output) · Pure CSS (no framework) · Cloudflare Pages

**Deploy:** `git push origin main` → Cloudflare Pages auto-builds via `npm run build` → publishes `dist/`

## Development

```bash
npm run dev      # dev server at localhost:4321
npm run build    # production build → dist/
npm run preview  # preview production build locally
```

## Project structure

```
src/
  layouts/
    Base.astro        # HTML shell, nav, footer, meta
    BlogPost.astro    # Article layout with structured data
  pages/
    index.astro       # Homepage (/)
    portfolio.astro   # Portfolio (/portfolio)
    blog/
      index.astro     # Blog listing (/blog)
      [...slug].astro # Dynamic post routes (/blog/[slug])
  content/
    blog/             # Markdown blog posts go here
    config.ts         # Content collection schema
  styles/
    global.css        # All CSS — design tokens, components, layouts
public/
  favicon.png
  og-image.png
  logos/
  robots.txt
  _redirects         # Cloudflare: /articles → /blog
_truth/
  voice.md           # Canonical writing voice and style rules
  features.md        # Services, capabilities, client reference
  priorities.md      # Strategic content priorities
_legacy/             # Old static HTML (archived, not served)
```

## Writing a blog post

Create `src/content/blog/[slug].md` with this frontmatter:

```markdown
---
title: "Your Post Title"
description: "One sentence for meta description and card excerpt. Under 160 chars."
publishDate: 2026-06-08
category: Strategy
tags: [crypto, content-strategy]
status: published
---

Post body here in Markdown.
```

Set `status: draft` to write without publishing. Switch to `status: published` when ready. The post appears at `getstoryarc.com/blog/[slug]` automatically on next deploy.

## Design system

| Token     | Value   | Usage                              |
|-----------|---------|------------------------------------|
| `--bg`    | #0D0D0D | Page background                    |
| `--surface` | #161616 | Cards, form inputs               |
| `--text`  | #FFFFFF | Primary text                       |
| `--muted` | #888888 | Secondary text, labels             |
| `--accent`| #EF9F27 | CTAs, key numbers, highlights only |
| `--border`| #2A2A2A | Dividers, borders                  |

Font: Inter (Google Fonts). No gradients, no shadows. Sharp and minimal.

## Source of truth files

Reference these in any content generation or editing workflow:

- `_truth/voice.md` — tone, style rules, what to avoid
- `_truth/features.md` — services, clients, proof points
- `_truth/priorities.md` — strategic angles, target personas, metrics

## CRM

`crm.html` — standalone localStorage CRM, open directly in browser. No build step.

## Cloudflare Pages settings

- Build command: `npm run build`
- Build output directory: `dist`
- Node version: 18+
- Redirects: defined in `public/_redirects`
