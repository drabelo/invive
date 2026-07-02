# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The marketing/landing page site for **Invive**, a one-person freelance web agency run by Dailton Rabelo. It is a single self-contained `index.html` — no build tools, no package manager, no frameworks, no dependencies beyond two Google Fonts (`Syne` for display type, `Inter` for body text). All CSS is in a `<style>` block and all JS is in a `<script>` block at the bottom of the same file.

Deployed via GitHub Pages, served at the custom domain in `CNAME` (`dailton.com`).

## Working in this repo

- There is nothing to install, build, lint, or test — open `index.html` directly in a browser to preview changes.
- Since there's no build step, view the change by opening the file (`open index.html` on macOS) or via a local static server if `file://` behavior (e.g. fonts, IntersectionObserver) needs checking against `https://`.
- Keep everything in the single `index.html` file — do not split out separate `.css`/`.js` files unless explicitly asked; that would break the "zero build tools" constraint the site was designed around.
- The contact CTA must always be a plain `mailto:dailtonrabelo@gmail.com` link — there is intentionally no contact form.

## Structure of `index.html`

The page is one long scroll of `<section>` elements, each independently styled and self-contained, sharing a small set of common building blocks defined once near the top of `<style>`:

- `:root` CSS custom properties — colors (`--bg`, `--teal`, `--muted`, etc.), radii, shadows. Change the palette here, not by editing individual rules.
- `.container` / `.section` — shared width and vertical-padding wrappers used by every section.
- `.btn` + variants (`.btn-primary`, `.btn-outline`, `.btn-ghost`, `.btn-surface`) — the button system reused across nav, hero, pricing, and about/contact CTAs.
- `.reveal` / `.reveal-delay-*` — scroll-in animation classes. Applied to elements via an `IntersectionObserver` in the trailing `<script>`, with a 1.2s `setTimeout` fallback so content isn't stuck hidden if the observer never fires (e.g. no-JS edge cases).
- `.section-eyebrow` / `.section-title` / `.section-sub` — shared heading pattern reused by every content section (pricing, how-it-works, work, about, contact).

Sections in DOM order: `#nav` (sticky, frosted-glass on scroll via `.scrolled` class) → `#hero` → `#pricing` (three tier cards, `.featured` marks the highlighted "Pro" card) → `#how-it-works` (3-step numbered grid) → `#work` (portfolio cards) → `#about` → `#contact` → `footer`.

Because every section reuses the same tokens and button/heading classes, adding a new section means matching the existing pattern (eyebrow + title + sub, wrapped in `.container.section`) rather than inventing new primitives.

## Design reference docs

`docs/superpowers/specs/2026-06-28-invive-landing-design.md` is the approved design spec (brand direction, section-by-section content, out-of-scope items). `docs/superpowers/plans/2026-06-28-invive-landing.md` is the task-by-task implementation plan used to originally build the page. Consult these before making content or structural changes to understand original intent — e.g. the "Out of Scope" list in the spec (no contact form, no blog, no CMS, no client testimonials yet) still reflects deliberate decisions, not gaps.
