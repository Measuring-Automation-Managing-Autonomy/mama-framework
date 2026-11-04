# MAMA Glossary

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

Canonical terminology for MAMA (Measuring Automation & Measuring Autonomy). These definitions are binding across the organization's repositories, tools, and publications. Propose changes via a Framework Proposal issue; accepted changes become ADRs.

## Identity terms

**MAMA** — uppercase — *Measuring Automation & Measuring Autonomy*. The umbrella framework, organization, architecture, integrated approach, and shared toolset. This organization.

**`mama`** — lowercase, in code formatting — *measuring and managing autonomy*. A distinct autonomy method used within MAMA. Canonical home: [`emmanuel-a-otchere/measuring-and-managing-autonomy`](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy). Never merge the names, ownership, repositories, or scores.

**MAMA automation measurement** — the umbrella's own automation and outcome measurement capability. Not supplied by the `mama` autonomy score.

## Framework structure

**Investment / strategic context** — organization goals, portfolio, project, investment rationale, constraints, stakeholders, jurisdiction, and risk appetite surrounding an automation/autonomy effort.

**Use case** — a bounded service, process, value stream, or task area with identified decision points, users, affected parties, a baseline, and an intended outcome. The unit MAMA measures and governs.

**Technology and capability inventory** — the AI models, software, robotic systems, networks, data, infrastructure, vendors, versions, owners, and lifecycle states a use case depends on.

**Automation activity** — a task or process step performed (fully or partly) by an automated capability rather than a person.

**Autonomy domain** — a bounded area of decision-making whose delegated authority is granted, scoped, reviewed, and revocable. The unit `mama` scores.

**Decision rights** — the authority to make specified choices within specified scope, held by a person, team, system, network, software, robot, or AI agent.

**Traceability chain** — organization/portfolio → investment/project → use case/process → technology/capability → automation activity + autonomy domain/decision rights → metrics/evidence/controls → outcomes and review decisions.

## Measurement terms

**Metric card** — a versioned definition of one measure: purpose, formula, unit, denominator, inclusion/exclusion rules, data source, sampling method, time window, owner, baseline, target, uncertainty, limitations, and review cadence. Published in [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics).

**Automation coverage** — the share of eligible work (per an explicit eligibility rule) performed by automated capabilities. One input to automation measurement — never a success proxy on its own.

**Human touch** — the degree of human involvement in a process step (none / by exception / continuous), reported alongside automation coverage.

**Straight-through completion** — an item completed by the automated path with no manual intervention or rework.

**Baseline** — the pre-change or comparison measure against which outcomes are judged. Required before benefit claims.

**Attribution** — the defensible method connecting an observed outcome to the automation/autonomy change (comparison design, confound handling). Required before causal claims.

**Observed / estimate / forecast** — distinct measurement modes that must be labeled distinctly and never blended.

**Adverse effect** — a material negative consequence (quality, workforce, safety, fairness, rights, environment) reported alongside benefits.

## Autonomy terms (consumed from `mama` v2.0.0)

These terms are defined upstream; MAMA consumes them as issued. Canonical definitions: the `mama` repository's docs.

**Autonomy contract** — the recorded grant of decision authority in one autonomy domain: scope, guardrails, telemetry, revocation triggers, grantor, review horizon.

**Autonomy Ledger** — the registry of autonomy contracts (upstream ledger, `schema: 2`), measuring *granted autonomy (supply)*.

**L0 — Submarine Line** — no autonomy granted at all. L1–L5 — the definitive delegated levels. Dimension scores run 0–5 (D1 clarity, D2 capability, D3 guardrails, D4, D5, D6 — see upstream docs for authoritative definitions).

**Weakest link** — upstream's safe-level rule: `min(D3, D4, D6)`. MAMA displays it as issued; it never recomputes it.

**Review horizon** — the date by which an autonomy grant must be re-reviewed to remain valid.

## Governance terms

**Artifact status label** — exactly one of `draft`, `pilot`, `reviewed`, `stable`, `deprecated`, `archived`, on every public artifact.

**ADR** — architecture decision record: an evidence-linked, versioned record of a core framework decision, including dissent.

**Evidence register** — the versioned record of data sources, assessment versions, approvals, control tests, incidents, and review decisions behind a claim.

**Pilot-stage** — the organization-wide label that applies to all public MAMA materials until the multi-organization pilot completes.
