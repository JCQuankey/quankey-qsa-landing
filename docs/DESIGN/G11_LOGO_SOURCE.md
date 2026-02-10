# G11 Logo Source

**Date:** 2026-02-10
**SSOT:** quankey-hexagonal-refined.html, "Logo Principal"

---

## Source File

| Field | Value |
|-------|-------|
| Path | `/workspace/Quankey_26/dev/Brand/Hexagonal/quankey-hexagonal-refined.html` |
| SHA-256 | `00c89ce6aade80671da52fb6a6f3c9cbcc884c078d33a21240123dc06e563f20` |
| Logo section | Lines 410-460, badge label "Principal" |

## Why This Is SSOT

1. The file is titled "Sistema de Identidad Hexagonal Final" (Final Hexagonal Identity System).
2. It lives in `/dev/Brand/Hexagonal/` -- the definitive brand directory per IMPLEMENTATION_GUIDE.md.
3. It contains the most refined version: glow filter, 3 key teeth (vs 2 in logo-main.svg), and annotated structure.
4. It supersedes `logo-main.svg` which was an earlier export without the glow or 3rd tooth.

## Extraction Notes

- Extracted the `<g transform="translate(160, 160)">` group (lines 430-458)
- Gradient IDs renamed: `mainGrad1` -> `navGrad1`, `mainGrad2` -> `navGrad2`, `glow` -> `navGlow`
- ViewBox cropped from 320x320 to icon bounds + glow padding: `"109 115 102 93"`
- Icon bounds: x 115-205, y 121-202 (90x81 units). With 6px glow padding: 102x93.
- Added `<title>Quankey logo</title>` for accessibility.

## Previous Source (G10 -- superseded)

| Field | Value |
|-------|-------|
| File | `logo-main.svg` |
| SHA-256 | `462382a6811a2dc1028fa064c1c98cef524026e4b5b6889f02db511782bdbc86` |
| Issue | Missing glow filter and 3rd key tooth vs refined SSOT |
