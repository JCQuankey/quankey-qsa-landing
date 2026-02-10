# G10 Logo Source

**Date:** 2026-02-10
**Scope:** Header branding fix -- replace fingerprint+key icon with hexagonal SSOT

---

## Selected Asset

| Field | Value |
|-------|-------|
| File | `/workspace/Quankey_26/dev/Brand/Hexagonal/logo-main.svg` |
| SHA-256 | `462382a6811a2dc1028fa064c1c98cef524026e4b5b6889f02db511782bdbc86` |
| Dimensions | 200x200 viewBox, icon bounds ~94x88 (centered at 100,100) |
| Structure | 3 concentric hexagons (outer/mid/inner) + key shaft + key teeth + center dot |
| Colors | linearGradient #00A6FB -> #00D4FF (matches Quankey Brand System v2.0) |

## Why This File

1. **IMPLEMENTATION_GUIDE.md** (same directory) says: "Usar logo-main.svg para fondos oscuros con gradientes" -- our landing is dark theme.
2. It is the full-color gradient version, matching the QSA landing's dark aesthetic.
3. The `/workspace/Quankey_26/dev/Brand/Hexagonal/` directory is the SSOT for hexagonal brand assets per the Brand Guidelines PDF.

## Alternatives Considered

| File | Reason Rejected |
|------|-----------------|
| `quankey-logo-horizontal.svg` | Uses `SF Pro Display` font (Apple-only). Would render incorrectly on Windows/Linux. |
| `logo-corporate.svg` | Dark color fills (#0A1628) designed for light backgrounds. Invisible on our dark theme. |
| `logo-white.svg` | Monochrome. Loses the brand gradient. |
| Old `logo-compact.svg` (in `frontend/public/icons/`) | Fingerprint+key pattern, NOT hexagonal. This is what we're replacing. |

## Composition Strategy

**Icon**: `logo-main.svg` paths inlined in nav SVG, viewBox cropped to icon bounds.
**Wordmark**: HTML `<span>` with Inter web font + CSS gradient text. NOT the SVG text element (avoids SF Pro Display dependency).

This matches the IMPLEMENTATION_GUIDE.md pattern for Header usage while ensuring cross-platform font rendering.

---

*Traceability: checksum computed 2026-02-10 via sha256sum.*
