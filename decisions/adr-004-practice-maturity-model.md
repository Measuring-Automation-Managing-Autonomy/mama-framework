# ADR-004: Descriptive practice maturity model and value framework

**Status:** accepted (v0.2.0, draft artifact) · **Date:** 2026-11-04 · **Decided by:** MAMA Stewardship Council (interim) · **License:** CC-BY-4.0

## Context

Two adopter-facing instruments were requested and are now adopted:

1. An **autonomous operations maturity model** — describing how maturely the
   operation around automated/autonomous systems runs (guardrail
   engineering, observability, oversight, incident learning, workforce/impact
   stewardship).
2. A **value framework** — the evidence cadence by which value claims are
   made: intake → baseline → hypothesis → measure → attribution → decision.

Both collide superficially with existing binding constraints:

- `mama-metrics/taxonomy.md` states metric categories are **"never a target,
  maturity stage, or rank"** and "not a maturity ladder".
- [ADR-003](adr-003-no-composite-score.md) prohibits unvalidated composite
  scores; the charter's principles 4–5 forbid rankings and treating autonomy
  as a virtue score.

## Decision

1. **Adopt** `maturity-model.md` and `value-framework.md` in
   `mama-framework` as canonical instruments, status **draft (v0.2.0)**.
2. The maturity model is a **descriptive, evidence-gated, per-use-case
   profile**: five practice dimensions staged 0–4. It is **not** a maturity
   ladder over the metric taxonomy, not a target, not a rank, and carries no
   single/aggregate score — the profile is the output. This is the
   reconciliation with the taxonomy rule: the taxonomy governs *metric
   categories*; the maturity model governs *operating-practice description*
   and must consume taxonomy cards as evidence, never redefine them as
   ladder rungs.
3. The maturity model and `mama` autonomy levels (v2.0.0) are **orthogonal
   instruments**: the former describes operating practice around autonomous
   systems; the latter describes delegated decision rights. They are read
   side by side at review gates and are never combined, mapped, or averaged.
4. The value framework **invents no new scoring** and no value index; it
   consolidates existing templates, guidance, and metric cards into a
   gated cadence, per [ADR-003](adr-003-no-composite-score.md).
5. Two indicator metric cards are added to `mama-metrics`
   (`guardrail-drill-adherence`, `incident-learning-closure`) as evidence
   hooks for stages D-A 3+ and D-D 3+; they follow the card schema and
   taxonomy process and are ordinary cards, not ladder rungs.
6. External maturity models (notably TM Forum
   [GB1042A](https://www.tmforum.org/resources/guidebook/gb1042a-autonomous-operations-maturity-model-aomm-v1-8-0),
   referenced per the [external-mappings policy](../external-mappings.md))
   are acknowledged as prior art; **no stage-to-level or model-to-model
   mapping is claimed** in either direction.

## Consequences

- Adopters get a usable, auditable way to discuss operational maturity
  without violating the no-rank/no-target/no-composite rules.
- Dual-instrumentation discipline is now expected at review gates: practice
  profile + `mama` autonomy profile + balanced metrics, presented separately.
- The `guardrail-drill-adherence` and `incident-learning-closure` cards
  enter the metrics taxonomy under `exceptions-reliability`.
- Documentation, templates, and the architecture "where it lives" table are
  updated in the same release (v0.2.0).

## Open questions (carried, not resolved)

- Are the five practice dimensions and the 0–4 stage gates distinguishable
  and usable in practice? → multi-organization pilot
  ([charter §7](../charter.md#7-roadmap)).
- Should any stage ever be *scored* for a consumer's internal portfolio
  view? Default: no; revisiting requires pilot evidence and a superseding
  ADR (consistent with [ADR-003](adr-003-no-composite-score.md)).
- Whether sector profiles of the maturity model (per the sector working
  groups) should vary stage definitions — deferred to pilot findings.
