# Safe to Publish Checklist

**Date:** 2026-02-10
**Repo:** quankey-qsa-landing
**Target:** GitHub Pages at qsa.quankey.xyz

---

## Included Files

| File | Size | Purpose | Safe? |
|------|------|---------|-------|
| `index.html` | 17 KB | QSA landing page (Quankey-branded) | YES |
| `CNAME` | 17 B | GitHub Pages custom domain (qsa.quankey.xyz) | YES |
| `.nojekyll` | 0 B | Prevent Jekyll processing | YES |
| `README.md` | 907 B | Public repo description | YES |
| `LICENSE` | 502 B | CC BY 4.0 content license | YES |
| `SECURITY.md` | 439 B | Responsible disclosure policy | YES |
| `robots.txt` | 25 B | Allow search engine indexing | YES |
| `DEPLOY.md` | 3.8 KB | Deployment instructions (public-safe) | YES |
| `SAFE_TO_PUBLISH.md` | this file | Publication checklist | YES |

**Total: 9 files, ~23 KB**

---

## Explicitly Excluded

| Item | Reason |
|------|--------|
| Go source code | Private scanner repo only |
| Scanner binary (`qsa`) | Not for public distribution via landing |
| Dockerfile | Private repo only |
| Evidence packs / scan results | Client data, never public |
| governance/ (claims, decisions, assumptions) | Internal project tracking |
| docs/PLAN/ (charter, roadmap, architecture) | Internal planning |
| docs/PILOT_PACK/ (outreach, sample report) | Internal operations |
| scripts/ (pilot, analytics) | Internal tooling |
| SAMPLE_REPORT_REDACTED.html | Cainmani brand colors remain; needs rebrand |

---

## Leakage Checks

| Pattern | Expected | Actual | Status |
|---------|----------|--------|--------|
| Cainmani hex codes (#283C63, #1F2E4D, #FABD00, #CC8800) | 0 | 0 | PASS |
| "cainmani" (non-email) | 0 | 0 | PASS |
| "cainmani" (in email: jcano@cainmani.com) | 4 | 4 | PASS (intentional) |
| Internal IPs (54.72.3.39) | 0 | 0 | PASS |
| Internal domains (dev-qk82nx) | 0 | 0 | PASS |
| /workspace/ paths | 0 | 0 | PASS |
| targets.txt | 0 | 0 | PASS |
| internal_pilot | 0 | 0 | PASS |
| governance / CLAIM_LEDGER / DECISIONS | 0 | 0 | PASS |
| evidence/ / outputs/ / scripts/ | 0 | 0 | PASS |
| Private repo name (quankey-qsa without -landing) | 0 | 0 | PASS |
| `<script>` tags | 0 | 0 | PASS |
| Analytics / tracking pixels | 0 | 0 | PASS |

---

## Content Verification

| Check | Status |
|-------|--------|
| Quankey brand colors present (#00A6FB, #00D4FF, #0A1628, #1E3A5F) | PASS |
| Quankey logo SVG inlined | PASS |
| Contact email functional (mailto: link) | PASS |
| No JavaScript execution | PASS |
| Responsive design (mobile media query) | PASS |
| Google Fonts fallback to system fonts | PASS |
| All links are relative or to external public URLs | PASS |
| No broken internal links | PASS |

---

## Decisions for JC

| Decision | Default | Notes |
|----------|---------|-------|
| Repo name | `quankey-qsa-landing` | Public, static only |
| Custom domain | `qsa.quankey.xyz` | CNAME file pre-configured |
| License | CC BY 4.0 | Website content license |
| Font hosting | Google Fonts CDN | Fallback to system fonts if CDN unavailable |
| Sample report | EXCLUDED | Needs Quankey rebrand before inclusion |

---

## Verdict: SAFE TO PUBLISH

All checks pass. No sensitive data, no internal infrastructure references, no scanner code. Ready for JC to run the commands in DEPLOY.md.

---

*Checklist v1.0.0 -- 2026-02-10*
