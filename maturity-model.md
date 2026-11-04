# Autonomous operations maturity model

> **Status:** draft (v0.2.0) · **Owned by:** MAMA Stewardship Council · **License:** CC-BY-4.0
>
> **Read the rules before the model.** This is a **descriptive, evidence-gated
> instrument** for a single unit's operating practice — not a ranking, not a
> target, not a score, and never blended with `mama` autonomy outputs
> ([ADR-004](decisions/adr-004-practice-maturity-model.md)). It exists because
> organizations asked "how do we know our *operations around* autonomous
> systems are maturing?" — a different question from "`mama`'s" *what
> decision rights are delegated and how controlled are they?*

## 1. What this model is — and is not

| It **is** | It **is not** |
|---|---|
| A five-dimension profile of operating practice for one automation/autonomy use case | A maturity ladder to climb for its own sake |
| Evidence-gated: a stage is claimed only with the evidence named in it | A self-image survey; unevidenced stage claims are recorded as the stage below |
| Paired with balanced metric sets ([taxonomy rule 2](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/taxonomy.md)) | A single number, composite, or org ranking ([ADR-003](decisions/adr-003-no-composite-score.md)) |
| Separate from and orthogonal to `mama` autonomy levels | An input to, or output of, `mama` scoring — the two are read **side by side**, never combined |

**Relationship to `mama` autonomy levels (v2.0.0):** `mama` measures
*delegated decision rights* (L0 Submarine Line through L5 Accountable, per
domain). This model describes *how maturely the surrounding operation
runs* — guardrail engineering, observability discipline, oversight,
learning, and workforce stewardship. **Neither implies the other**, and the
interesting signal is the cross-reading a human makes: a high autonomy
grant sitting on low practice maturity is a flagged risk, not a computed
one. The profile is captured per use case alongside the
[`mama` integration outputs](integration-contract.md) and reviewed together
at the [lifecycle review gates](lifecycle.md).

**Relationship to external maturity models:** TM Forum's Autonomous
Operations Maturity Model ([GB1042A](https://www.tmforum.org/resources/guidebook/gb1042a-autonomous-operations-maturity-model-aomm-v1-8-0))
is acknowledged prior art in the same problem space, referenced per the
[external-mappings policy](external-mappings.md); the value-cadence framing
draws on the [MAMA Whitepaper (IG1301)](https://www.tmforum.org/resources/introductory-guide/ig1301-measuring-and-managing-autonomy-whitepaper-v1-2-0)
and the [MAMA Framework Guidebook (GB1040)](https://www.tmforum.org/resources/guidebook/gb1040-mama-framework-guidebook-v1-0-0).
This model is independent; **no stage-to-level mapping is claimed** in
either direction, and no equivalence, endorsement, or conformance is
implied.

## 2. The five practice dimensions

Each dimension is staged 0–4. The stage is the **highest stage fully
supported by evidence** (partial achievement records as the stage below).
Stage names are shared across dimensions; the meaning is defined per
dimension.

| Stage | Label | Meaning (generic) |
|---|---|---|
| 0 | **Absent** | No evidence of any deliberate practice in this dimension |
| 1 | **Ad hoc** | Practice exists locally, unwritten, dependent on individuals |
| 2 | **Defined** | Practice is written, assigned, and repeatable |
| 3 | **Exercised** | Practice is instrumented and has been exercised under real conditions, with records |
| 4 | **Self-improving** | The unit improves the practice itself from its own evidence and teaches it onward |

### D-A — Guardrail engineering and testing

How the unit designs, implements, and *exercises* the limits that make
automated/autonomous operation safe. (Note: this is the operational
discipline around guardrails; the granted decision rights themselves are
`mama`'s [D3](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy/blob/main/docs/maturity-model.md).)

- **0 Absent** — no deliberate guardrail practice; limits are whatever the tool defaults are.
- **1 Ad hoc** — informal limits; "we watch it"; no written boundary.
- **2 Defined** — written limits per [workflow mapping](templates/workflow-decision-rights-mapping.md); owners assigned; safe-stop/rollback paths documented.
- **3 Exercised** — limits automated where the risk warrants; drills or real trips recorded (see the `guardrail-drill-adherence` metric card); results fed to the risk/impact review.
- **4 Self-improving** — the unit designs and stress-tests its own guardrails, shares failure stories, and revises limits on a cadence.

### D-B — Observability and telemetry discipline

Whether consequences of automated/autonomous action are visible, fast, and
honest — including known blind spots.

- **0 Absent** — outcomes discovered by others, late.
- **1 Ad hoc** — scattered dashboards; manual checks when someone remembers.
- **2 Defined** — standard metric set from [mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) instrumented with baselines ([baselining guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/baselining.md)).
- **3 Exercised** — near-real-time signals with breach alerts routed to unit **and** grantor; uncertainty and blind spots reported with the numbers ([uncertainty guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/uncertainty.md)).
- **4 Self-improving** — the unit detects and corrects drift before external parties notice; telemetry design is revised from evidence.

### D-C — Oversight and intervention

Whether human oversight is designed, staffed, and actually works — response,
override, safe stop.

- **0 Absent** — no designed oversight; intervention is improvised.
- **1 Ad hoc** — someone "keeps an eye on it"; no response expectations.
- **2 Defined** — oversight roles per the [role model](roles.md); response expectations and escalation routes written; grantor ≠ grantee respected.
- **3 Exercised** — oversight tested in drills or real events; intervention and safe-stop records kept; response times measured.
- **4 Self-improving** — oversight design is revised from intervention evidence; oversight burden on humans is measured and reduced deliberately (workforce-impact pairing).

### D-D — Incident learning and adaptation

Whether failures and near-misses change the system.

- **0 Absent** — incidents are survived, not learned from.
- **1 Ad hoc** — post-incident discussion happens; no record of changes.
- **2 Defined** — blameless review is standard; every consequential incident has an owner and a written outcome.
- **3 Exercised** — learning-loop closure is tracked (see the `incident-learning-closure` metric card): recommended changes shipped, verified, and re-tested.
- **4 Self-improving** — near-misses and external failures are actively harvested; learning artifacts are reused by other units.

### D-E — Workforce and impact stewardship

Whether effects on workers, customers, and affected groups are measured and
acted on — the balanced-reporting duty made operational.

- **0 Absent** — impacts are unknown or unowned.
- **1 Ad hoc** — anecdotal attention; no measurement.
- **2 Defined** — impact measures selected from [mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) (worker-experience-impact, customer-impact, distributional-effects) with owners and baselines.
- **3 Exercised** — impact signals reviewed at the same cadence as performance signals; adverse findings trigger the [risk/impact review](templates/risk-impact-review.md), not a press release.
- **4 Self-improving** — impact evidence changes operating design; affected-stakeholder perspectives have a standing channel into decisions ([roles.md](roles.md)).

## 3. Using the model

1. **One profile per use case** (unit × process), produced with the same
   dual-assessor discipline as a `mama` assessment; keep both in the
   project's evidence record.
2. **Report the profile, not a total.** Five stage values, each with its
   evidence links. No average, no sum, no radar-chart-derived score.
3. **Read beside, never merged.** At review gates, present the practice
   profile next to the `mama` autonomy profile and the balanced metric set;
   decisions are made by the named decision owners ([risk-value-interpretation](risk-value-interpretation.md)).
4. **Stage claims are auditable.** The evidence for each claimed stage is
   linked and versioned; an unauditable claim is recorded at the stage
   below.
5. **No universal targets.** No stage is "where everyone should be" — the
   useful stage depends on blast radius, reversibility, and the
   [value hypothesis](value-framework.md).

## 4. Indicator metric cards

Two [mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics)
cards support this model directly; the rest of the evidence comes from the
existing card set and `mama` profiles:

- [`guardrail-drill-adherence`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/cards/guardrail-drill-adherence.yaml) — are the drills happening on cadence (D-A stage 3+)
- [`incident-learning-closure`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/cards/incident-learning-closure.yaml) — do lessons actually close the loop (D-D stage 3+)

## 5. Status and validation

This model is **pilot-stage** ([charter §5](charter.md#5-limitations)):
stage definitions may change as pilots report. Changes ride the framework's
[versioning and ADR process](decisions/adr-004-practice-maturity-model.md).
Known open questions are recorded in the ADR; the multi-organization pilot
([charter §7](charter.md#7-roadmap)) tests whether the five dimensions and
stage gates are usable and distinguishable in practice.
