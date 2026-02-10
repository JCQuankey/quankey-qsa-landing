# G9 Landing Content Plan

**Date:** 2026-02-10
**Purpose:** Define message hierarchy and content strategy before touching CSS/HTML.

---

## Core Thesis

**We solve one problem exceptionally well:**
Measure and evidence your TLS cryptographic posture -- including PQC readiness -- with repeatable, auditable scans that run on your infrastructure.

---

## Values to Transmit

| Value | How we communicate it | What we DON'T say |
|-------|----------------------|-------------------|
| Security (operational) | Passive TLS handshakes only. No data leaves your network. | "Military-grade", "impenetrable" |
| Independence | Vendor-neutral. No lock-in. Static binary or Docker. | "Better than [competitor]" |
| PQC readiness (measurable) | Detects hybrid key exchange groups (e.g., X25519MLKEM768). Scores 0-100. | "Quantum-proof", "future-proof" |
| Rigor | Evidence packs with SHA-256 hash chain. Drift diffs between scans. | "Guaranteed compliance" |
| Focus | TLS perimeter only. Explicit out-of-scope list. | "Full crypto inventory" |

---

## Section-by-Section Content

### 1. Hero
- H1: "Quantum-Safe Assurance for your TLS perimeter"
- Sub: Measure crypto hygiene and PQC readiness. On-prem. Evidence you can audit.
- 3 bullets: discover posture, detect PQC, track drift
- CTA: "Request a pilot" (mailto) + "How it works" (anchor)

### 2. Problem
- Framing: operational (not fear-based)
- 3 consequences: incomplete inventories, configuration drift, manual audit cost
- Citations: NIST IR 8547 (2035 deadline), NSA CNSA 2.0 (2030 PQC requirement)

### 3. Scope (In / Out)
- Two columns, explicit wedge
- In: scan, classify, score, diff
- Out: not inline, not migration service, not SaaS

### 4. Why It Matters
- 3 cards: can't prioritize without data, drift goes unnoticed, audits are expensive
- Phrasing: "If you don't measure..." (consequence framing, not fearmongering)

### 5. Differentiators (Our Approach)
- 4 cards based on capability, not comparison:
  1. On-prem by design (static binary, no telemetry)
  2. Vendor-neutral posture (any TLS endpoint, one methodology)
  3. Evidence-first reporting (hash chain, JSON, HTML report)
  4. Drift diffs (scan-to-scan comparison, change advisory boards)

### 6. How It Works
- Terminal-style panel: `qsa scan`, `qsa diff`, `qsa verify`
- Score readouts: 79 (Hygiene) / 40 (PQC Readiness) from real scan
- Note: "Scores from a scan of 5 public endpoints, February 2026"

### 7. Pilot
- 2 weeks, ~30 min setup, no cost, passive-only
- What you provide / what you receive columns
- Safety callout: passive TLS handshakes only

### 8. Contact
- Clear CTA: "Request a pilot"
- Visible email: jcano@cainmani.com
- Responsible disclosure link

---

## Content Rules

1. Every technical claim must be something the scanner actually does (code exists)
2. Scores shown are from real scans (February 2026, 5 public endpoints)
3. No "unique" or "only" -- describe what we do, not what others don't
4. Inline citations for standards (NIST, NSA) -- no saturating with references
5. Keep total word count under 800 (landing, not whitepaper)

---

*Content plan approved. Proceeding to implementation.*
