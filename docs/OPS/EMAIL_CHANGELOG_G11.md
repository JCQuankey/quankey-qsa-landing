# G11 Email Changelog

**Date:** 2026-02-10
**Change:** Replace all `jcano@cainmani.com` with `dev@quankey.xyz`

---

## Replacements

| Location | Line (approx) | Before | After |
|----------|---------------|--------|-------|
| Nav CTA button | ~540 | `mailto:jcano@cainmani.com?subject=QSA%20Pilot%20Inquiry` | `mailto:dev@quankey.xyz?subject=QSA%20Pilot%20Inquiry` |
| Hero CTA button | ~562 | `mailto:jcano@cainmani.com?subject=QSA%20Pilot%20Inquiry` | `mailto:dev@quankey.xyz?subject=QSA%20Pilot%20Inquiry` |
| CTA section button | ~760 | `mailto:jcano@cainmani.com?subject=QSA%20Pilot%20Inquiry` | `mailto:dev@quankey.xyz?subject=QSA%20Pilot%20Inquiry` |
| CTA section visible email | ~761 | `jcano@cainmani.com` | `dev@quankey.xyz` |
| Footer contact link | ~772 | `mailto:jcano@cainmani.com` | `mailto:dev@quankey.xyz` |

**Total:** 5 replacements (3 mailto with subject, 1 visible text, 1 plain mailto)

## Not Changed

- Responsible disclosure link (line ~773): still points to `SECURITY.md` on GitHub (not a mailto)
- No `security@quankey.xyz` added (not yet confirmed as working)

## Follow-up Required

JC must set up `dev@quankey.xyz` in Hostinger before emails will be received.
See: `docs/OPS/HOSTINGER_EMAIL_SETUP.md`
