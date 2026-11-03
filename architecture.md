# MAMA Reference Architecture

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

## The linked, non-collapsed model

MAMA organizes automation/autonomy governance around seven linked components. The links are mandatory; the collapse is forbidden — no single ladder, ladder position, or scalar score may substitute for the distinct views below.

| # | Component | Answers | Where it lives |
|---|---|---|---|
| 1 | **Investment & strategic context** | Why is this money being spent? Goals, portfolio, project, rationale, constraints, stakeholders, jurisdiction, risk appetite | Use-case record (intake template) |
| 2 | **Use case & process context** | What work is in scope? Service, process, value stream, tasks, decision points, users, affected parties, baseline, intended outcome | Use-case record |
| 3 | **Technology & capability inventory** | What runs it? AI models, software, robotic systems, networks, data, infrastructure, vendors, versions, owners, lifecycle status | Use-case record / asset registry |
| 4 | **Automation measurement** | How much work is automated, how well it performs, what outcomes and benefits are realized | [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) |
| 5 | **Autonomy measurement & management (`mama`)** | What decision authority is delegated, at what level, with what controls — via autonomy contracts, six-dimension profiles, ledger, evidence, review decisions | Upstream `mama` tool, imported via [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations) |
| 6 | **Risk, assurance & impact** | What could go wrong and what controls exist? Reliability, safety, security, privacy, fairness, human oversight, legal/sector obligations, resilience, workforce/customer impact, environmental impact where material, incident learning | Risk/impact review template; control register |
| 7 | **Value realization & continuous improvement** | Did it pay off against baseline and hypothesis? Continue / adjust / expand / constrain / retire | Baseline & value-hypothesis template; review decisions |

## Traceability chain

Every MAMA record must be able to walk this chain without ambiguity:

**Organization/portfolio → investment/project → use case/process → technology/capability → automation activity + autonomy domain/decision rights → metrics/evidence/controls → outcomes and review decisions.**

Practical requirements:

- **Stable IDs.** Each level carries a stable identifier (e.g., `proj-2026-014`, `usecase-payments-disputes`, `domain-production-deploys`) that survives renames.
- **Versioned links.** Links record versions: metric library version, `mama` ruleset/schema version, assessment date.
- **Two join keys.** Use cases join to *automation activities* (for metric computation) and to *autonomy domains* (for `mama` contracts) independently. Neither join implies the other.

```mermaid
flowchart LR
  P[Portfolio / investment] --> U[Use case / process]
  U --> T[Technology & capability inventory]
  U --> A[Automation activities]
  U --> D[Autonomy domains / decision rights]
  A --> M[Metric cards & evidence]
  D --> L["`mama` contracts & ledger\n(ruleset v2.0.0, schema 2)"]
  T --> R[Risk, control & obligation register]
  M --> O[Outcomes & review decisions]
  L --> O
  R --> O
  O --> P
```

## Non-collapse rules

1. **A project may automate a process without delegating consequential decision rights.** High automation coverage with L0/L1 autonomy is a normal, describable state — not an inconsistency.
2. **An autonomous unit may rely on both automated and human work.** The autonomy profile describes decision authority, not staffing or automation degree.
3. **No forced ladder.** Automation degree and autonomy level are different axes. Nothing in MAMA maps one onto the other.
4. **No composite score.** Metrics and autonomy outputs are displayed side by side, linked and versioned — never aggregated into a single number (see [ADR-003](decisions/adr-003-no-composite-score.md)).
5. **No averaging away guardrails.** Portfolio views preserve each autonomy domain's dimension profile, guardrails, and review horizon.

## Interfaces

- **To the `mama` method:** the versioned contract in [integration-contract.md](integration-contract.md); implemented by [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations).
- **To external frameworks:** complementarity mappings in [external-mappings.md](external-mappings.md) — never equivalence claims.
- **To tools (Phase 3):** `mama-tools` consumes the schemas in `mama-metrics` and the import formats in `mama-integrations`; it must keep automation and autonomy measures distinct in UI and storage.
