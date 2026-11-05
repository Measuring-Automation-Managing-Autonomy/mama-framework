# MAMA Charter

**MAMA — Measuring Automation, Managing Autonomy**

**Status:** draft (v0.1.0) · **Owned by:** MAMA Stewardship Council · **License:** CC-BY-4.0

## 1. Purpose

MAMA is an open, practical framework and toolset that helps organizations plan, assess, govern, and improve investments in automation and autonomy — across projects involving AI and other technologies.

MAMA exists because organizations make consequential investment and operating decisions about automation and autonomy with fragmented evidence: delivery metrics in one system, model cards in another, decision-rights documents in email, and outcomes nobody can attribute. MAMA links those views so decisions can be evidence-backed.

MAMA treats automation and autonomy as **connected but distinct concerns**:

- **Measuring automation** answers what work and capabilities are automated, how well the automated process performs, what outcomes it produces, and whether investment benefits are realized.
- **Measuring autonomy** answers what decision authority is delegated to people, teams, systems, networks, software, robots, or AI agents; within what scope; at what level; for how long; and with what controls and accountability.

MAMA integrates these views. It covers systems and networks that are autonomous, automation of processes and capabilities that may enable more autonomy, and the business, operational, human, and societal outcomes of those investments.

### Relationship to the `mama` method

> MAMA (Measuring Automation, Managing Autonomy) uses the `mama` (measuring and managing autonomy) method for its autonomy-governance component.
>
> **The acronym is authoritative and the comma is the constitution.**
> "Measuring Automation" is MAMA's own capability; "Managing Autonomy" is
> delivered by `mama` — so each half of the acronym names the instrument
> that provides it, and `mama` is the managing-autonomy component of MAMA
> by name and by function. No other spelling is permitted
> ([ADR-006](decisions/adr-006-authoritative-expansion.md)).

The lowercase `mama` method is a distinct autonomy method whose canonical home is [`emmanuel-a-otchere/measuring-and-managing-autonomy`](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy). MAMA is the umbrella framework and organization; `mama` is one of its components. The names' case, ownership, homes, repositories, and scores are never merged. MAMA consumes `mama`'s versioned outputs through an explicit interface and does not redefine, rename, or recalculate its scores. MAMA's automation measurement is its own capability and is not represented as supplied by the `mama` autonomy score.

## 2. Scope

**In scope:** investment and portfolio decisions about automation/autonomy; use-case and process assessment; technology and capability inventory; automation measurement; autonomy measurement and management (via `mama`); risk, assurance, and impact; value realization and continuous improvement; the governance that keeps these trustworthy.

**Out of scope:** issuing certifications or regulatory approvals; replacing legal advice, safety case processes, or professional judgment; scoring or ranking organizations; a universal target for any metric; a composite MAMA score (see [ADR-003](decisions/adr-003-no-composite-score.md)).

## 3. Principles

1. **Two measures, never one score.** Automation performance/value measures and `mama` autonomy outputs remain separate, linked, versioned, and interpretable.
2. **Evidence before claims.** A baseline and a defensible attribution/comparison method are required before claiming automation caused a benefit. Observed measures, estimates, and forecasts are labeled distinctly.
3. **Balanced reporting.** Trade-offs, negative effects, and distributional impacts are reported alongside benefits — including failure impacts across affected groups.
4. **Context survives aggregation.** Every cross-project comparison discloses metric definitions, ruleset versions, scope, data quality, and normalization. No ranking rewards raw automation percentage or autonomy level without regard to value, risk, quality, or affected people.
5. **Autonomy is not a virtue score.** A higher autonomy level is neither inherently better nor safer. Low guardrails, telemetry, or accountability are never averaged away.
6. **Traceability.** Organization/portfolio → investment/project → use case/process → technology/capability → automation activity + autonomy domain/decision rights → metrics/evidence/controls → outcomes and review decisions.
7. **Open and versioned decisions.** Core framework decisions are public, versioned, and evidence-linked; dissent and unresolved questions are recorded.
8. **Data minimization and local control.** Tools honor local deployment and data minimization; no centralization of raw telemetry or sensitive ledgers by default.
9. **Honest status.** Every artifact carries a public status label; no claim of certification, approval, or universal validity is made without a separate qualified process.

## 4. Intended users

- **Investment and portfolio owners** deciding where to automate and how much decision authority to delegate.
- **Operational and engineering leaders** running automated and autonomous systems and their guardrails.
- **Risk, assurance, security, and compliance functions** needing linked evidence, not another checklist.
- **Workforce and people functions** assessing impact on roles, skills, and oversight burden.
- **Researchers and evaluators** studying automation and autonomy measurement validity.
- **Affected stakeholders and their representatives** who deserve visibility into what is delegated and how it is controlled.

## 5. Limitations

- MAMA is **pilot-stage**. All public materials are labeled pilot-stage until a multi-organization pilot (≥6 use cases, ≥3 organizations, ≥2 sectors) completes and its findings are published.
- MAMA's metric definitions require local operationalization; data quality and attribution limits are documented per use.
- `mama` autonomy outputs measure **granted decision authority and its controls** — not safety, legality, quality, or compliance. Risk/control review and qualified legal interpretation remain necessary.
- Framework adoption or tool output is **not proof** of conformity, certification, safety, or effectiveness.
- External framework mappings identify complementarity and gaps; they never imply endorsement or equivalence.

## 6. Stewardship

Governed by the MAMA Stewardship Council with the working groups defined in [org GOVERNANCE.md](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/GOVERNANCE.md). Every repository, schema, tool, and published asset has a named accountable maintainer. Decision rights, contribution practices, appeals, and conflict-of-interest separation are defined there.

## 7. Roadmap

| Phase | Focus | Gate to proceed |
|---|---|---|
| 0 — Establish identity & governance | Charter, naming, policies, stewards | this document |
| 1 — Publish umbrella architecture | `.github`, `mama-framework`, `mama-metrics` | schemas stable enough for tools |
| 2 — Integrate the autonomy method | `mama-integrations`, version-pinned import/export | worked integration example passes CI |
| 3 — Minimum useful tools | Use-case registry, metric calculator, evidence record, portfolio view | conformance fixtures pass |
| 4 — Pilot & validate | ≥6 use cases, ≥3 organizations, ≥2 sectors; publish results & limitations | pilot report published |
| 5 — Scale responsibly | Sector packs, training, stable releases, funding plan | — |

Versioning: this charter is v0.1.0 (`draft`). Changes require an ADR once status reaches `reviewed`.
