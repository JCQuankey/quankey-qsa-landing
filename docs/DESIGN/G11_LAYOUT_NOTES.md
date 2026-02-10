# G11 Layout Notes

**Date:** 2026-02-10
**Scope:** Widen container to reduce "boxed" feel on desktop

---

## Problem

G9/G10 used `max-width: 1200px` for both `.container` and `.nav-inner`. On a 1440px viewport, this leaves 120px dark gutter on each side, making content feel like a narrow column inside the full-bleed dark background.

## Solution: CSS Layout Tokens

Added to `:root`:
```css
--page-max: 1320px;
--page-pad: 32px;
```

Applied to:
- `.container { max-width: var(--page-max); padding: 0 var(--page-pad); }`
- `.nav-inner { max-width: var(--page-max); }`
- `nav { padding: 0 var(--page-pad); }`

## Why 1320px (not 1400+)

- At 1440px viewport: 60px gutter each side (vs 120px before). Content is wider but not edge-to-edge.
- Text readability preserved: all prose blocks already have max-width constraints:
  - `.hero h1`: 720px
  - `.hero-sub`: 600px
  - `.section-intro`: 680px
  - `.cta-section p`: 520px
- Card grids and terminal block benefit most from the extra 120px.
- Going wider (1400+) would make card grids too spread on large screens.

## Responsive Behavior

| Breakpoint | Container behavior |
|------------|-------------------|
| > 1320px | Content at 1320px, centered with even gutters |
| 769-1320px | Content fills viewport minus 32px padding each side |
| <= 768px | Padding reduces to 20px (unchanged from G9) |

## No overflow risk

- Card grid uses `repeat(auto-fit, minmax(280px, 1fr))` -- adapts to available width
- Two-col grid switches to single column at 768px
- Terminal block has `overflow-x: auto`
- All clamp() values handle the range
