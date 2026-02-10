# G12 Copy Audit: Scope Clarification (Landing)

**Date:** 2026-02-10
**Sprint:** G12 -- scope copy + plan alignment

---

## Problem

The landing footer states:

> "Performs passive TLS handshake analysis only. Does not exploit vulnerabilities, manage certificates, or implement PQC algorithms."

This undersells the product. The Architecture V0 Collector already captures leaf certificate fields (subject, issuer, not_after, sig_algorithm, public_key_type, public_key_bits). The MVP Charter Section 3 already includes "certificate chain health" in the wedge definition. The landing copy should reflect what the scanner actually does.

Additionally, "manage certificates" is ambiguous -- it could mean "view/read certificate data" (which we DO) or "issue/renew/rotate certificates" (which we DON'T). The new copy must be precise.

---

## What Will Change

### Footer disclaimer (line 778)

**Before:**
```
Quankey QSA -- TLS posture assurance and PQC readiness measurement.
Performs passive TLS handshake analysis only.
Does not exploit vulnerabilities, manage certificates, or implement PQC algorithms.
```

**After:**
```
Quankey QSA -- read-only TLS posture assurance and PQC readiness measurement.
Passive analysis of TLS handshake negotiation and leaf-certificate metadata.
Does not exploit vulnerabilities, issue or renew certificates, terminate TLS connections,
or implement PQC algorithms.
```

**Why:**
- "read-only" reinforces passive posture (not inline, not modifying)
- "leaf-certificate metadata" is precise (we do NOT parse full chain yet)
- "issue or renew" replaces ambiguous "manage" with specific exclusions
- "terminate TLS connections" adds explicit non-inline assurance

### Scope section -- In Scope (lines 611-616)

**Add bullet after cipher suite bullet:**
```
Inspect leaf-certificate metadata: subject, issuer, expiry, signature algorithm,
public-key type and length
```

**Why:** The Architecture Collector already captures these 6 fields. The landing should reflect this.

### Scope section -- Not in Scope (lines 620-624)

**Add bullet:**
```
Not a certificate manager -- QSA reads certificate metadata but does not issue, renew,
rotate, or revoke certificates
```

**Why:** Explicitly separates "reading cert data" (what we do) from "managing cert lifecycle" (what we don't).

---

## What Will NOT Change

- Hero section text
- "Why it matters" section
- CTA section
- Standards references in footer
- Any CSS or layout

---

## Risks

| Risk | Mitigation |
|------|-----------|
| Over-promising full chain analysis | Use "leaf-certificate metadata" (not "certificate chain") |
| Confusion with cert management tools | Explicit exclusion bullet in Not in Scope |
| HandshakeResult schema drift if we later add chain | "leaf-certificate" is accurate for frozen v0.1.0 schema |

---

## Traceability

| Claim | Source |
|-------|--------|
| Collector captures 6 cert fields | Architecture V0, lines 86-93 |
| MVP Charter includes "certificate chain health" | MVP_CHARTER_1P.md, Section 3, line 61 |
| HandshakeResult v0.1.0 is frozen | ADR-008 |
| Drift compares cert fingerprint + expiry + key | ADR-012 |
| Cert management explicitly excluded in ADR-001 | DECISIONS.md, ADR-001 alternatives |
