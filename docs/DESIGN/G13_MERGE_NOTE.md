# G13 Merge Note

**Date:** 2026-02-10

---

## Merge Order

1. `feat/g11-logo-width-email` (9e813fe) -> main -- **fast-forward**
2. `feat/g12-scope-copy` (220746b) -> main -- **auto-merge** (no conflicts)

## Commits Now in Main

| Hash | Description |
|------|-------------|
| 485720a | Merge branch 'feat/g12-scope-copy' |
| 220746b | G12: scope copy update -- certificate posture signals in landing |
| 9e813fe | G11: SSOT hex logo + widen layout + switch to dev@quankey.xyz |
| c9116e2 | G10: replace header logo with hexagonal SSOT + improve wordmark sizing |

## QA Summary (post-merge)

| Check | Result |
|-------|--------|
| No "Cainmani" in index.html | 0 (PASS) |
| dev@quankey.xyz present | 5 (PASS) |
| "leaf-certificate metadata" present | 2 (PASS) |
| "Not a certificate manager" present | 1 (PASS) |
| No /workspace references | 0 (PASS) |
| SSOT logo (navGlow) | 2 (PASS) |
| Layout tokens (page-max/page-pad) | 5 (PASS) |
| No old email (jcano@cainmani) | 0 (PASS) |
| Line count | 790 (PASS) |

## Conflicts

None. G11 was fast-forward. G12 auto-merged cleanly (index.html changes in non-overlapping regions).
