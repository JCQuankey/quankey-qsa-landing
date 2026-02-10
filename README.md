# Quankey QSA -- Landing Page

Landing page for **Quankey QSA** (Quantum-Safe Assurance), an on-premises TLS crypto hygiene and PQC readiness scanner.

## What is QSA?

QSA is a command-line tool that scans your TLS endpoints and produces two scores:

- **Crypto Hygiene** (0-100): Current cipher suite, protocol version, and certificate health
- **PQC Readiness** (0-100): Degree to which endpoints support Post-Quantum Cryptography key exchange

Output is an auditable evidence pack with SHA-256 hash-chain integrity, designed for compliance teams.

## This Repository

This repository contains only the static landing page for QSA. It is served via GitHub Pages at [qsa.quankey.xyz](https://qsa.quankey.xyz).

## Contact

For pilot program inquiries: **jcano@cainmani.com**

## Changelog

- **2026-02-10 (G10)**: Header branding fix -- replace fingerprint+key icon with hexagonal SSOT logo, improve wordmark sizing. See `docs/DESIGN/G10_CHANGELOG.md`.
- **2026-02-10 (G9)**: Full visual redesign -- dark theme, hex pattern, glass-morphism cards, fixed nav, SVG hex icons, terminal code block, WCAG-accessible buttons, prefers-reduced-motion. See `docs/DESIGN/G9_CHANGELOG.md`.
- **2026-02-10**: Rewritten landing page -- 8 sections with inline NIST/NSA citations, explicit scope wedge, safety callout, responsible disclosure link.
- **2026-02-10**: Initial publish -- 7-section landing page, Quankey brand, GitHub Pages.

## License

Website content is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
