# G11 Step 0 Audit

**Date:** 2026-02-10
**Scope:** Header logo, layout width, email swap, email infra runbook

---

## A) SSOT Logo Located

| Field | Value |
|-------|-------|
| File | `/workspace/Quankey_26/dev/Brand/Hexagonal/quankey-hexagonal-refined.html` |
| SHA-256 | `00c89ce6aade80671da52fb6a6f3c9cbcc884c078d33a21240123dc06e563f20` |
| Logo used | "Logo Principal" (lines 410-460), badge label "Principal" |
| ViewBox | 320x320, icon centered at translate(160, 160) |

### Extracted SVG structure (Logo Principal)

3 elements:
1. **Outer hex** (opacity 0.5): `d="M -45,0 L -22.5,-39 ... Z"`, stroke gradient #00A6FB->#00D4FF->#0084D4
2. **Inner hex** (opacity 0.75): `d="M -30,0 L -15,-26 ... Z"`, same gradient
3. **Key group** (with glow filter):
   - Hex key head: `d="M -12,0 L -6,-10.4 ... Z"`, stroke gradient #00D4FF->#00A6FB
   - Key shaft: 6x32 rect
   - 3 key teeth (not 2): `rect(-3,38,3,4)`, `rect(2,36,3,6)`, `rect(-1,40,2,2)`
   - Center dot: circle r=3, fill #00D4FF

### Why it's different from G10

G10 nav logo was sourced from `logo-main.svg` (a separate, simpler file). The refined version adds:
1. **3rd key tooth** (`<rect x="-1" y="40" width="2" height="2">`) -- missing in G10
2. **Glow filter** (`feGaussianBlur stdDeviation="3"`) on the key group
3. The 320x320 viewBox (G10 used 200x200 coords from logo-main.svg)

---

## B) Current Header Implementation

- Nav SVG (line 517): `viewBox="53 56 94 88"` with 200x200 coordinate space
- 2 gradient IDs: `navGrad1`, `navGrad2`
- Icon size: 36x36px CSS (from G10)
- Wordmark: 20px, 700 weight, 0.08em tracking
- Missing: glow filter, 3rd tooth, `<title>` element

---

## C) Layout Analysis

- Container: `max-width: 1200px`, padding `0 32px`
- Nav inner: `max-width: 1200px`
- On 1440px viewport: 120px dark gutter on each side = "boxed" feel
- Text blocks already have sensible max-widths (680px, 720px, etc.)
- Fix: widen container to 1320px via CSS tokens, keep text max-widths

---

## D) Email Audit

5 occurrences of `jcano@cainmani.com`:
- Line 540: nav CTA `mailto:`
- Line 562: hero CTA `mailto:`
- Line 760: CTA section `mailto:`
- Line 761: visible email text `<span class="cta-email">`
- Line 772: footer contact `mailto:`

Responsible disclosure (line 773): links to SECURITY.md on GitHub (not a mailto). No security@ address needed.

User override: use `dev@quankey.xyz` (not contact@).
