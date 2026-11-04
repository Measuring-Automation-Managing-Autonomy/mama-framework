# Changelog — mama-framework

All notable changes to the MAMA framework documents. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions are semver. `draft`-status artifacts may change without notice; `reviewed`/`stable` artifacts change only with an ADR.

## [0.2.0] — 2026-11-04

### Added

- `maturity-model.md` — autonomous operations practice maturity: five evidence-gated dimensions (guardrail engineering, observability, oversight, incident learning, workforce/impact stewardship), staged 0–4, descriptive profile only (ADR-004)
- `value-framework.md` — the gated value cadence consolidating existing templates, guidance, and metric cards by reference; no new scoring (ADR-004)
- `decisions/adr-004-practice-maturity-model.md` — reconciles the maturity model with the taxonomy's no-ladder rule and ADR-003's no-composite rule
- Two practice-indicator metric cards in `mama-metrics` v0.2.0: `guardrail-drill-adherence`, `incident-learning-closure`

### Changed

- `architecture.md`: components 6–7 "where it lives" now point to the maturity model and value framework
- `external-mappings.md`: TM Forum row re-scoped to the approved asset set (GB1040, GB1042A, IG1301) per the standing TM Forum reference policy; Autonomous Networks and VOF references removed
- `templates/baseline-value-hypothesis.md`: metric-library version example updated (v0.1.0 → v0.2.0)
- README: artifact table gains the two new documents

## [0.1.0] — 2026-11-04

### Added (initial scaffold, CR MAMA-ORG-CR-001)

- Charter, glossary, reference architecture, lifecycle, roles
- Implementation guide and risk/value interpretation rules
- Integration contract to the upstream `mama` method (ruleset v2.0.0, ledger schema 2)
- External mappings approach (NIST AI RMF, ISO/IEC 42001 & 23894, OECD, TM Forum, OWASP GenAI, MITRE ATLAS)
- Templates: project intake, baseline & value hypothesis, workflow & decision-rights mapping, risk/impact review
- ADRs 001–003 (naming & relationship, licensing, no composite score)

[0.1.0]: https://github.com/Measuring-Automation-Managing-Autonomy/mama-framework/releases/tag/v0.1.0
