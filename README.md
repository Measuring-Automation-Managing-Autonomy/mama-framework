# mama-framework

**MAMA** (Measuring Automation, Managing Autonomy) — the source of truth for what MAMA means.

**Status:** `draft` (v0.5.0) · **License:** CC-BY-4.0 · **Maintainer:** see [MAINTAINERS.md](MAINTAINERS.md)

This repository holds the umbrella charter, canonical terminology, reference architecture, concepts and lifecycle, implementation method, role model, risk/value interpretation rules, external mappings, and the integration contract to the lowercase `mama` method. If a definition conflicts anywhere else in the organization, this repository wins until an ADR says otherwise.

> **First reference:** MAMA (Measuring Automation, Managing Autonomy) uses the `mama` (measuring and managing autonomy) method for its autonomy-governance component. The `mama` method's canonical home is [`emmanuel-a-otchere/measuring-and-managing-autonomy`](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy). The names are case-sensitive and their homes, ownership, repositories, and scores are not merged.

## Contents

| Document | What it defines |
|---|---|
| [charter.md](charter.md) | Purpose, scope, principles, intended users, limitations, roadmap |
| [glossary.md](glossary.md) | Canonical terminology (binding across the organization) |
| [architecture.md](architecture.md) | Reference architecture and the traceability model |
| [lifecycle.md](lifecycle.md) | Project/use-case lifecycle stages and their gates |
| [roles.md](roles.md) | Role model: who holds which responsibility |
| [implementation-guide.md](implementation-guide.md) | End-to-end adoption method, from investment question to operating decision |
| [risk-value-interpretation.md](risk-value-interpretation.md) | How to interpret measures without collapsing them; no composite score |
| [maturity-model.md](maturity-model.md) | Autonomous operations practice maturity — five evidence-gated dimensions, descriptive profile (ADR-004) |
| [value-framework.md](value-framework.md) | The gated value cadence: intake → baseline → hypothesis → measure → attribution → decision |
| [adoption-walkthrough.md](adoption-walkthrough.md) | Self-guided ~90-minute MAMA adoption walkthrough (integration layer) |
| [indices-and-tracking.md](indices-and-tracking.md) | The computational/reporting reference: three per-axis display indices, the series interface, tracker plot rules (ADR-005) |
| [integration-contract.md](integration-contract.md) | Versioned interface to the upstream `mama` method |
| [external-mappings.md](external-mappings.md) | Crosswalk approach to NIST, ISO/IEC, OECD, TM Forum, OWASP, MITRE |
| [templates/](templates/) | Project intake, baseline & value hypothesis, workflow & decision-rights mapping, risk/impact review |
| [decisions/](decisions/) | Architecture decision records (ADRs) |

## Artifact status

| Artifact | Status |
|---|---|
| charter.md | draft |
| glossary.md | draft |
| architecture.md | draft |
| lifecycle.md | draft |
| roles.md | draft |
| implementation-guide.md | draft |
| risk-value-interpretation.md | draft |
| maturity-model.md | draft |
| value-framework.md | draft |
| adoption-walkthrough.md | draft |
| indices-and-tracking.md | draft |
| integration-contract.md | draft |
| external-mappings.md | draft |
| templates/* | draft |

## How to propose changes

Open a [Framework Proposal issue](https://github.com/Measuring-Automation-Managing-Autonomy/mama-framework/issues/new?template=framework-proposal.yml). Proposals sit open for at least 7 days; accepted changes are recorded as ADRs in [`decisions/`](decisions/). See the org [CONTRIBUTING.md](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/CONTRIBUTING.md).

## Related repositories

- [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) — metric taxonomy, cards, guidance
- [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations) — versioned adapters to upstream `mama`
- Organization profile & governance: [`/.github`](https://github.com/Measuring-Automation-Managing-Autonomy/.github)

## License

Documentation under [CC-BY-4.0](LICENSE); code (if any) under Apache-2.0. See the [license policy](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/LICENSE-POLICY.md).
