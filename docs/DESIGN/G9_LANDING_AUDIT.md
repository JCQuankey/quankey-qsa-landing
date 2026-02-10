# G9 Landing Page Audit

**Date:** 2026-02-10
**Auditor:** Claude Code (Senior Frontend + UI/UX)
**Subject:** index.html (previous: 436 lines, 20KB)

---

## TOP 10 Visual/UX Issues

| # | Issue | Severity | Detail |
|---|-------|----------|--------|
| 1 | Light theme reads as "document", not security product | CRITICAL | White bg + gray alternating sections = corporate blog aesthetic. Zero "security console" feel. |
| 2 | Narrow container (max-width: 960px) | HIGH | Page feels like a Notion doc / narrow column. Wastes 30%+ viewport on 1440px screens. |
| 3 | Logo is compact icon at 36px, not horizontal wordmark | HIGH | Tiny icon lacks brand presence. No "QUANKEY" wordmark visible in header. |
| 4 | No navigation | MEDIUM | 8 sections with no way to jump between them. Long scroll without orientation. |
| 5 | Section alternation (white/gray) is generic | HIGH | nth-child(even) pattern is indistinguishable from any template site. No brand identity. |
| 6 | No hexagonal or security-themed visual language | MEDIUM | Zero visual cues that this is a security product. Could be any SaaS landing. |
| 7 | Score cards are plain white boxes | MEDIUM | The two most compelling data points (79/40 scores) are visually flat. Should feel like instrument readouts. |
| 8 | Code block lacks terminal authenticity | MEDIUM | Dark rectangle with colored text. No window chrome, no prompt indicators, no terminal feel. |
| 9 | Cards have no visual weight on white bg | MEDIUM | 1px border on white = nearly invisible. Cards don't "contain" content visually. |
| 10 | No hover/interaction feedback on cards or links | LOW | Static page with zero micro-interactions. Feels printed, not digital. |

---

## 5 Key Design Decisions

### D1: Full dark theme
Switch body bg to `--quankey-dark` (#0A1628). All sections dark. Cards use glass effect (semi-transparent navy + blue border glow). Rationale: Security products universally adopt dark UIs. It signals "operations center" rather than "marketing site."

### D2: Widen container to 1200px
`max-width: 1200px` with generous padding. Sections use full-bleed backgrounds. Content breathes. Desktop users see a real layout, not a narrow column.

### D3: Horizontal wordmark with adapted tagline
Use the SSOT fingerprint+key icon from `logo-compact.svg` paired with "QUANKEY" wordmark + "QUANTUM-SAFE ASSURANCE" tagline. Note: `logo-horizontal.svg` has "QUANTUM PASSWORD SECURITY" (password manager product). The tagline is the only change; icon and wordmark are identical to SSOT.

### D4: Hexagonal SVG background pattern
Subtle repeating hex grid at 3-4% opacity over dark bg. Reinforces "digital security" without being noisy. CSS-only via inline SVG data URI.

### D5: Accessible button contrast
Brand gradient (#00A6FB->#00D4FF) with white text fails WCAG AA (2.68:1). Primary CTA uses solid `#0077CC` (4.78:1 with white = passes AA). Brand gradient reserved for decorative borders, icon fills, and text on dark backgrounds where it passes comfortably.

---

## No-Go List (Forbidden Claims/Phrases)

| Phrase | Why forbidden |
|--------|---------------|
| "Military-grade" | No military certification exists for this product |
| "Enterprise-grade" | No enterprise deployments yet |
| "Best-in-class" / "market-leading" | Unverifiable superlative |
| "Unique" / "only solution" | Competitor landscape exists (testssl.sh, Qualys, etc.) |
| "Unbreakable" / "quantum-proof forever" | No cryptographic guarantee is absolute |
| "Guaranteed compliance" | QSA measures posture; it doesn't guarantee regulatory outcomes |
| "AI-powered" | Not applicable |
| "Zero-day protection" | Not a WAF or IDS |

**Allowed phrasing:** "operationally rigorous", "auditable", "evidence-based", "repeatable", "passive-only", "on-prem by design", "vendor-neutral"

---

## Trade-offs for JC

### T1: Logo tagline
- **Option A (recommended):** Icon + "QUANKEY" wordmark + "QUANTUM-SAFE ASSURANCE" (adapted tagline)
- **Option B:** Compact icon only + HTML text "Quankey QSA" (current approach)
- **Proceeding with:** Option A (more brand presence, same visual assets)

### T2: Contact method
- **Option A (recommended):** mailto only (v0, zero complexity)
- **Option B:** Formspree/Getform form with mailto fallback
- **Proceeding with:** Option A (no proven demand for forms yet)

### T3: Button contrast
- **Option A (recommended):** Solid #0077CC buttons (passes WCAG AA)
- **Option B:** Brand gradient buttons with dark text (passes but looks unusual)
- **Proceeding with:** Option A

---

*Audit complete. Proceeding to content plan and implementation.*
