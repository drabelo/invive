# Invive — Agency Landing Page Design Spec
**Date:** 2026-06-28  
**Status:** Approved

---

## Overview

A single-page brochure site for **Invive**, Dailton Rabelo's freelance web agency. The site's sole job is to convert a visiting small business owner into a contact. It signals professionalism, surfaces pricing upfront, removes friction, and drives directly to email contact — no booking tools, no forms, no fluff.

**Target audience:** Small business owners (restaurants, salons, gyms, contractors, lawyers, startups) with no site or an outdated one.  
**Primary CTA:** Email contact — one click, no intermediary.  
**Tech:** Single `index.html`, zero build tools, hosted on GitHub Pages.

---

## Brand & Visual Direction

- **Name:** Invive
- **Tone:** Dark, confident, boutique digital studio — the professional counterpoint to warm client sites
- **Background:** Near-black (`#0D0D0F`)
- **Accent:** Electric teal/indigo (`#4FFFD4` or similar — to be finalised in build)
- **Typography:** Sharp, modern sans-serif for body (e.g. `Inter`); geometric display face for headlines (e.g. `DM Sans` bold or `Syne`)
- **Feel:** Less warm agency, more precision studio — signals "you're hiring a pro"

---

## Page Sections

### 1. Nav
- Logo: `Invive` wordmark (text, no icon)
- Links: Work · Pricing · About · Contact
- Sticky, transparent → frosted glass on scroll
- Single CTA button: `Get in Touch` → scrolls to contact

### 2. Hero
- Full-viewport, dark background
- Headline (large, display type): *"Your business deserves a site that works as hard as you do."*
- Subline: Fast turnaround. Fixed pricing. No jargon.
- Two CTAs: `See Pricing` (primary) · `View Work` (secondary/ghost)
- Ambient background texture or subtle gradient — no photography

### 3. Pricing (Services)
- Section title: "Simple, transparent pricing"
- Three cards: Starter / Pro / Premium
- Prices visible on the card — no "contact for pricing"

| Tier | Price | Inclusions |
|---|---|---|
| Starter | $799 | 1-page site, 5 sections, 1 revision, GitHub Pages hosting |
| Pro | $1,499 | Multi-page site, contact form, SEO basics, 3 revisions, analytics |
| Premium | $2,499 | Everything in Pro + copywriting, logo touchup, priority support |

- Pro card visually highlighted as "Most Popular"
- Each card ends with `Get Started →` link → scrolls to contact

### 4. How It Works
- Section title: "From idea to live site in 2 weeks"
- Three steps, horizontal layout:
  1. **Chat** — We talk through your business and goals (30 min call)
  2. **We Build** — You get a preview link within 7 days
  3. **You Launch** — One final round of changes, then it goes live
- No icons needed — numbered steps, clean typography

### 5. Work (Portfolio)
- Section title: "Selected Work"
- Single card: Maha Juice Marlborough
  - Screenshot / visual preview
  - Short descriptor: "Juice bar brochure site — Marlborough, MA"
  - Tag: `Brochure Site`
- Minimal framing — no apology for having one piece, just let it breathe
- Placeholder space for future projects (hidden until populated)

### 6. About
- 2–3 sentences max
- "Invive is run by Dailton Rabelo, a software engineer based in Massachusetts. I build fast, clean websites for real businesses — no templates, no bloat, just work that looks good and loads fast."
- No photo required at launch

### 7. Contact
- Section title: "Let's build something"
- Email address: `dailtonrabelo@gmail.com` — large, styled as a link
- Supporting line: "Most sites are live within 2 weeks. Reach out and let's talk."
- No form — direct `mailto:` link only

### 8. Footer
- Logo + tagline: "Fast sites for real businesses."
- Copyright line
- Link to GitHub (optional)

---

## Interactions & Behaviour

- Sticky nav transitions to frosted glass on scroll (same pattern as Maha Juice)
- Scroll-reveal on section entry (same IntersectionObserver pattern, with 1.2s fallback)
- Pricing cards: hover lift + accent border reveal
- "Most Popular" badge on Pro card
- All CTAs scroll to contact section smoothly

---

## Out of Scope (launch)

- Contact form (email only for now)
- Blog or case study pages
- CMS or editable content
- Monthly retainer pricing (add later)
- Client testimonials (add when available)
- Custom domain (can be added post-launch)

---

## Success Criteria

- A small business owner lands on the page and knows within 10 seconds: what Invive does, what it costs, and how to reach out
- Site is live on GitHub Pages
- Loads fast, looks sharp on mobile and desktop
