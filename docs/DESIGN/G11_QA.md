# G11 QA Results

**Date:** 2026-02-10

---

## QA Gate Results

| # | Test | Command / Method | Result |
|---|------|------------------|--------|
| 1 | No "Cainmani" in index.html | `grep -ci cainmani index.html` | **0 matches (PASS)** |
| 2 | No /workspace or internal IPs in index.html | `grep -cE '/workspace\|54\.72' index.html` | **0 matches (PASS)** |
| 3 | No jcano@cainmani.com in index.html | `grep -c 'jcano@cainmani' index.html` | **0 matches (PASS)** |
| 4 | All mailto point to dev@quankey.xyz | `grep -c 'dev@quankey.xyz' index.html` | **5 occurrences (PASS)** |
| 5 | SSOT gradient IDs namespaced | `grep -c 'navGrad1\|navGrad2\|navGlow' index.html` | **11 refs (PASS)** |
| 6 | No un-namespaced SSOT IDs leaked | `grep -cE 'id="glow"\|id="mainGrad' index.html` | **0 matches (PASS)** |
| 7 | 3rd key tooth present | `grep 'rect x="-1" y="40"' index.html` | **Found line 535 (PASS)** |
| 8 | Glow filter present | `grep 'navGlow\|feGaussianBlur' index.html` | **Filter + usage found (PASS)** |
| 9 | SVG `<title>` for a11y | `grep 'Quankey logo' index.html` | **Found line 521 (PASS)** |
| 10 | Layout tokens applied | `grep 'page-max\|page-pad' index.html` | **5 refs: 2 defs + 3 usages (PASS)** |
| 11 | File size reasonable | `wc -l index.html` | **788 lines (PASS)** |

## Viewport Checklist (manual)

| Viewport | Expected behavior |
|----------|------------------|
| 1440px desktop | Container at 1320px, 60px gutter each side. Logo 48px, wordmark 22px. |
| 1024px laptop | Container fills with 32px padding. Logo ~41px (clamp). |
| 768px tablet | Nav links hidden. Logo 36px. Single-column cards. |
| 375px mobile | Container with 20px padding. No horizontal overflow. |

## Regression Check

- Page content unchanged (only header branding + email addresses)
- Responsible disclosure link preserved (SECURITY.md on GitHub)
- Footer standards references preserved
- All existing CSS tokens unchanged
- prefers-reduced-motion still functional
