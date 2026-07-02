# dailton.com — Personal Portfolio Design

**Date**: 2026-07-01
**Status**: Approved pending user review

## Purpose

Replace the Invive landing page in this repo with a minimal personal
portfolio for Dailton Rabelo. The site deploys unchanged via GitHub Pages
to https://dailton.com.

## What it is

A single-page, minimal-light "business card" site. One `index.html`, no
build step, no JavaScript, no external assets beyond (at most) one Google
Font.

## Content — the entire page

- **Dailton Rabelo** — large heading, the focal point
- Subtitle: *Senior Software Engineer at Garner Health · New York*
- Three links:
  - Email: `contact@dailton.com`
  - GitHub: https://github.com/drabelo
  - LinkedIn: https://www.linkedin.com/in/drab-a2208562/

## Layout

**Centered card**: all content vertically and horizontally centered in the
viewport. Stacks naturally on mobile with no breakpoint gymnastics.

## Style

- Off-white background, near-black text
- One quiet accent color, used only on link hover/underline
- One clean typeface (Inter or system stack); total page weight under ~5 KB
  excluding the font
- No JavaScript

## Head / metadata

- `<title>`: "Dailton Rabelo — Senior Software Engineer"
- Meta description for SEO
- Open Graph tags (title, description, url) so shared links preview well

## Repo changes

1. `git pull` first — GitHub committed a `CNAME` file (dailton.com) to the
   repo when the custom domain was set; keep it.
2. Replace `index.html` entirely with the new page.
3. Remove old Invive design docs from `docs/superpowers/` working tree
   (history preserved in git).

## Out of scope

Projects/experience sections, resume PDF, analytics, dark mode, any
tooling or framework.

## Testing

- Open the page locally in a browser; check desktop and narrow (mobile)
  widths.
- Verify all three links resolve correctly.
- After push, confirm https://dailton.com serves the new page.
