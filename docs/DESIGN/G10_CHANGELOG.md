# G10 Changelog: Header Branding Fix

**Date:** 2026-02-10
**Scope:** Replace nav logo with hexagonal SSOT + improve wordmark visibility

---

## Changes

### Logo Icon (SVG)
- **Before:** Fingerprint+key icon (arcs + circle + rectangles) from old `logo-compact.svg` pattern. viewBox 0 0 120 120.
- **After:** Three concentric hexagons + key shaft + key teeth + center dot from SSOT `logo-main.svg`. viewBox cropped to 53 56 94 88 (icon bounds) for optimal rendering.
- Gradient IDs namespaced to `navGrad1`/`navGrad2` (avoid collision with page SVGs).
- 3-stop gradient matches SSOT exactly: #00A6FB -> #00D4FF -> #0084D4.

### Icon Sizing
- **Before:** 32x32px
- **After:** 36x36px (combined with cropped viewBox, visible geometry is ~40% larger)

### Wordmark
- **Before:** font-size 18px, letter-spacing 0.5px
- **After:** font-size 20px, letter-spacing 0.08em (~1.6px at 20px)
- font-weight and gradient text unchanged (700, --q-gradient)

### Not Changed
- Nav height (64px), nav layout, nav links, CTA button
- All page content below the header
- Contact email (jcano@cainmani.com, 5 instances)
- All other CSS tokens and colors
- Responsive breakpoints and mobile behavior

---

## QA Results

| Test | Result |
|------|--------|
| `/workspace` leakage in index.html | 0 matches (PASS) |
| Forbidden phrasing in index.html | 0 matches (PASS) |
| mailto CTA present | 5 instances (PASS) |
| Old gradient ID `ng` removed | 0 references (PASS) |
| New gradient IDs unique | navGrad1/navGrad2 only (PASS) |
| File size | 780 lines, unchanged (PASS) |
| All hex colors from tokens or SSOT SVG | Verified (PASS) |

---

## Source Traceability

See `G10_LOGO_SOURCE.md` for SVG selection rationale, SHA-256 checksum, and alternatives considered.

---

*No content changes. Header branding only.*
