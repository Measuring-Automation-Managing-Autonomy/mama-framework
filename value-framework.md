# MAMA value framework

> **Status:** draft (v0.2.0) · **Owned by:** MAMA Stewardship Council · **License:** CC-BY-4.0
>
> The value framework is MAMA's answer to one question: *what evidence
> justifies claiming an automation/autonomy investment produced value — and
> what must be reported alongside the claim?* It consolidates existing MAMA
> assets (templates, metric cards, guidance) into one cadence; it defines no
> new scoring and no composite number ([ADR-003](decisions/adr-003-no-composite-score.md)).

## 1. The value cadence

Value is managed as a repeating, evidence-gated cycle per **use case**, tied
to the [project lifecycle](lifecycle.md):

```
Intake → Baseline → Value hypothesis → Operate & measure → Attribution & review → Decision
   ↑_____________________________________________________________________|
```

Each gate has an owner, required evidence, and a failure mode named in the
[implementation guide](implementation-guide.md). The cadence concept is
prior art in industry value-management practice — notably TM Forum's
[MAMA Whitepaper (IG1301)](https://www.tmforum.org/resources/introductory-guide/ig1301-measuring-and-managing-autonomy-whitepaper-v1-2-0)
and [Framework Guidebook (GB1040)](https://www.tmforum.org/resources/guidebook/gb1040-mama-framework-guidebook-v1-0-0),
referenced per the [external-mappings policy](external-mappings.md) — and
this framework is MAMA's independent, open implementation of that pattern.
No equivalence or endorsement is implied.

## 2. Gate 1 — Intake: fix the intended decision use

Start from the [project intake template](templates/project-intake.md): the
investment rationale, scope, risk tier, affected parties, and — mandatory —
the **intended decision use** of the measurement. A metric collected without
a stated decision it informs is inventory, not evidence.

## 3. Gate 2 — Baseline: make the "before" honest

Establish the pre-automation/pre-autonomy baseline using the
[baselining guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/baselining.md).
Rules that matter most:

- The baseline uses the **same metric card versions** as the "after"
  measurement (card id + version recorded in the
  [baseline-value-hypothesis template](templates/baseline-value-hypothesis.md)).
- The manual baseline is measured, not assumed — humans are not 100% STP
  either; the honest baseline makes the delta real.
- Record data-quality notes and known blind spots with the baseline
  ([data-quality guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/data-quality.md)).

## 4. Gate 3 — Value hypothesis: falsifiable and card-keyed

The hypothesis states, *before* operation: which metric cards will move, in
which direction, by roughly how much, by when — and what adverse effects
would look like. Required structure is in the
[template](templates/baseline-value-hypothesis.md); targets come from the
hypothesis, never from a universal benchmark
([risk-value-interpretation §1](risk-value-interpretation.md)).

Balanced-set rule: baselines and claims must draw from **≥3 taxonomy
categories including an impact or distributional card** for medium/high
risk-tier use cases ([taxonomy rule 2](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/taxonomy.md)) —
value without its adverse effects is marketing.

## 5. Gate 4 — Operate & measure: label every number

During operation, measures are labeled **observed**, **estimate**, or
**forecast** ([uncertainty guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/uncertainty.md)),
and attribution is handled per the
[attribution claim ladder](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/attribution.md)
— "partially established" is an honest and common result. Automation
percentage is never read as success
([risk-value-interpretation §4](risk-value-interpretation.md)).

Where the use case delegates decision rights, the
[`mama` integration](integration-contract.md) contributes the **autonomy
profile** (six-dimension scores, safe grant level, contract state) as a
separate, versioned input — displayed beside the value measures, never
combined ([ADR-003](decisions/adr-003-no-composite-score.md)).

## 6. Gate 5 — Attribution & review: the claim, and its shadow

At the review gate, the [worked calculation pattern](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/examples/worked-calculation.md)
is the standard shape: observed deltas against baseline, attribution status
stated, **and the shadow report** — adverse effects, workforce and customer
impacts, distributional gaps, and what got worse. A value claim without its
shadow is incomplete and returns to the previous gate.

## 7. Gate 6 — Decision: continue, adjust, expand, constrain, retire

The review ends in an owned decision at the
[lifecycle review stage](lifecycle.md) — with the decision, its evidence
versions, and dissent recorded. Value realized can justify **expand** (more
scope, higher `mama` grant via `mama`'s own review process — never a MAMA-side
authorization); value missed or adverse effects material can justify
**constrain or retire**. The decision and its rationale are the audit trail.

## 8. Asset map (reuse — nothing new is invented here)

| Cadence element | Canonical asset |
|---|---|
| Intake & decision use | `templates/project-intake.md` |
| Baseline | mama-metrics `guidance/baselining.md` + `guidance/data-quality.md` |
| Hypothesis | `templates/baseline-value-hypothesis.md` |
| Metric definitions | mama-metrics [metric cards](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/tree/main/cards) + [card schema](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/schema/metric-card.schema.json) |
| Measurement labeling | mama-metrics `guidance/uncertainty.md` |
| Attribution | mama-metrics `guidance/attribution.md` |
| Autonomy input | `mama` v2.0.0 outputs via [integration contract](integration-contract.md) |
| Shadow report | `templates/risk-impact-review.md` + mama-metrics impact/distributional cards |
| Interpretation rules | [risk-value-interpretation.md](risk-value-interpretation.md) |
| Decision record | [lifecycle.md](lifecycle.md) review stage |

## 9. What this framework is not

- **Not a score.** There is no "value score" and no blending of value,
  automation, and autonomy measures ([ADR-003](decisions/adr-003-no-composite-score.md)).
- **Not a target set.** Targets originate in each use case's hypothesis;
  the framework publishes none.
- **Not causal proof.** Attribution follows the claim ladder; without an
  appropriate evaluation design, relationships are descriptive
  ([charter §3 principle 2](charter.md#3-principles)).
- **Not done until the pilot reports.** Like all MAMA materials, this
  framework is **pilot-stage** ([charter §5](charter.md#5-limitations)).
