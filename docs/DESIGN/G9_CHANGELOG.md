# G9 Changelog: High-Security Landing Redesign

**Date:** 2026-02-10
**Scope:** Full visual redesign of index.html + design documentation

---

## Changes

### Layout
- Container widened from 960px to 1200px (full-bleed sections, no more "narrow sheet")
- Added fixed nav with logo, section links, and CTA button
- Added skip-to-content link for accessibility

### Visual Theme
- Switched from light (white bg) to full dark theme (#0A1628)
- Cards use glass-morphism: semi-transparent navy bg + backdrop-filter blur + blue border glow
- Added hexagonal SVG background pattern at 3.5% opacity (CSS-only, inline SVG data URI)
- Section dividers changed from alternating white/gray to subtle blue border lines
- Score cards reworked as "instrument readouts" with gradient top bar and monospace values

### Typography
- Section labels now use JetBrains Mono, uppercase, primary blue
- H1 uses clamp() for fluid sizing (32px-52px)
- Gradient text applied to key H1 phrase ("TLS crypto posture")

### Iconography
- Removed all emojis (0 found in final output)
- Added 11 custom SVG icons inside hexagonal frames (.hex-icon + .hex-frame)
- Hero badge uses mini hexagon SVG marker
- Bullet markers changed from circles to hexagonal clip-path

### Brand Compliance
- All colors from Quankey Brand System v2.0 tokens.css
- Logo: SSOT compact icon (fingerprint+key) + "QUANKEY" gradient wordmark
- Button color: #0077CC (WCAG AA with white text, 4.78:1 ratio)
- Brand gradient reserved for decorative elements (borders, icon fills, score values)

### Terminal Block
- Added window chrome (three dots + title bar)
- Added $ prompt indicators
- Color-coded: commands (cyan), flags (blue), comments (gray)

### Interaction
- Card hover: border glow + subtle shadow
- Button hover: background shift + shadow expansion + translateY(-1px)
- "PQC detection enabled" pulse badge with subtle animation
- All transitions respect prefers-reduced-motion

### Accessibility
- Skip-to-content link
- focus-visible outlines on all interactive elements
- aria-label on nav and logo
- aria-hidden on decorative SVGs
- prefers-reduced-motion disables all animations

### Contact
- 4 mailto links (nav CTA, hero CTA, CTA section, footer)
- Visible email address in CTA section
- Responsible disclosure link in footer

---

## QA Results

| Test | Result |
|------|--------|
| Non-ASCII / emoji in index.html | 0 matches (PASS) |
| "Cainmani" in index.html | 0 matches (PASS) |
| Forbidden phrasing | 0 matches (PASS) |
| /workspace or IP leakage | 0 in index.html (PASS) |
| mailto CTA present | 4 instances (PASS) |
| Anchor integrity | 5/5 match (PASS) |
| Single file | Yes, 780 lines, 36KB (PASS) |
| prefers-reduced-motion | Implemented (PASS) |

---

## Files Added/Changed

| File | Action | Size |
|------|--------|------|
| index.html | REWRITTEN | 780 lines, 36KB |
| docs/DESIGN/G9_LANDING_AUDIT.md | NEW | Audit + trade-offs |
| docs/DESIGN/G9_LANDING_CONTENT_PLAN.md | NEW | Content strategy |
| docs/DESIGN/G9_CHANGELOG.md | NEW | This file |
| docs/PUBLISH_QSA_SUBDOMAIN_RUNBOOK.md | Existing | From earlier sprint |

---

*No external assets added. Single-file architecture preserved.*
