# dailton.com — Animation Design

**Date**: 2026-07-01
**Status**: Approved (conversationally, in-session)

## Purpose

Add a modern, mobile-first animation layer to the portfolio page. Must
keep the page light: no libraries, total page under ~6 KB excluding font.

## Effects

1. **Aurora gradient drift** (CSS only, all devices)
   - Two large pre-blurred radial-gradient blobs (blue + warm peach)
     fixed behind the content, drifting slowly via transform-only
     keyframes (GPU-friendly; no `filter: blur`).
   - A subtle fixed grain overlay (inline SVG feTurbulence data URI) so
     the gradients read analog, not screensaver.

2. **Breathing name** (CSS only, all devices)
   - Switch Inter to its variable axis (`wght 100..900`).
   - Each letter of "Dailton Rabelo" wrapped in a `<span>` (hardcoded,
     no JS) with a staggered `animation-delay` via `--i` custom property.
   - A weight wave ripples through the letters on a slow loop
     (700 → 400 → 700 per letter).
   - Accessibility: `aria-label="Dailton Rabelo"` on the h1, spans
     hidden from the accessibility tree.

3. **Cursor-proximity type** (tiny JS, desktop enhancement only)
   - Gated on `(hover: hover) and (pointer: fine) and
     (prefers-reduced-motion: no-preference)`.
   - On pointermove, letter weight scales 700 → 900 by distance to
     cursor; the CSS breathing loop is disabled once the pointer takes
     over. Touch devices never run this code.

## Motion accessibility

`@media (prefers-reduced-motion: reduce)` disables all animations.

## Out of scope

WebGL/three.js, scroll effects, scramble-on-load, magnetic links.

## Testing

- Playwright screenshots at 1280px and 375px; confirm blobs and layout.
- Console clean.
- Verify live at https://dailton.com after push.
