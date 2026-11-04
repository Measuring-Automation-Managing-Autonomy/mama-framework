# MAMA adoption walkthrough (self-guided)

> **Status:** draft (v0.3.0) · **Owned by:** MAMA Stewardship Council · **License:** CC-BY-4.0
>
> A ~90-minute walkthrough that takes an investment/operations team from
> zero to a **linked evidence view** on one real use case — automation
> measures, an imported `mama` autonomy profile, and a value decision read
> side by side. Companion to the upstream
> [`mama` training module](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy/blob/main/docs/training.md)
> (which covers the autonomy method itself); this walkthrough covers the
> **MAMA integration layer** around it. Method status:
> [pilot / under validation](limitations.md).

## Lesson 1 — Two measures, one use case · ~10 min

**Read:** the [charter principles](charter.md#3-principles) and the
[architecture](architecture.md).

MAMA exists because automation evidence and autonomy evidence live in
different systems and are usually read apart. The non-negotiables:

- **Two measures, never one score.** Automation metrics (mama-metrics) and
  `mama` autonomy outputs stay separate and linked
  ([ADR-003](decisions/adr-003-no-composite-score.md)).
- **One join key.** A stable use-case ID (`usecase-<slug>`) links everything.
- **Traceability.** organization/portfolio → investment/project → use case →
  technology → automation activity + autonomy domain → metrics/evidence →
  outcomes and decisions.

✏️ *Exercise:* pick one real automation/autonomy use case you know. Write
its `usecase-<slug>` ID, its intended decision use, and its risk tier — the
[intake template](templates/project-intake.md) walks you through it.

## Lesson 2 — Registry: make the use case legible · ~15 min

**Read:** [implementation guide](implementation-guide.md) steps 1–3.

Create the use-case record with
[mama-tools](https://github.com/Measuring-Automation-Managing-Autonomy/mama-tools):

```bash
mama-tools usecase new --id usecase-<slug> --title "..." --owner ... \
  --risk-tier medium --out registry/
mama-tools usecase validate registry/usecase-<slug>.yaml
```

Fill in: the `domains` block (which unit × decision domains hold delegated
authority — even if the answer today is "none, this is pure automation"),
evidence references, and the intended decision use.

✏️ *Exercise:* scaffold and validate your use-case record.

## Lesson 3 — Baseline and value hypothesis · ~15 min

**Read:** the [value framework](value-framework.md) gates 1–3 and the
[baselining guidance](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/baselining.md).

Choose metric cards from [mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics)
(balanced set: ≥3 categories, include an impact or distributional card for
medium/high risk), record the honest **manual baseline**, and write the
falsifiable value hypothesis in the
[template](templates/baseline-value-hypothesis.md) — direction, rough
magnitude, deadline, and the adverse effects you would consider failure.

✏️ *Exercise:* record two baselines in the `metric_baselines` block (labeled
`observed`/`estimate`/`forecast`) and write your hypothesis.

## Lesson 4 — Import the autonomy side · ~15 min

**Read:** the [integration contract](integration-contract.md) and
[compatibility matrix](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations/blob/main/compatibility.md).

If your use case delegates decision rights, the unit runs an upstream
`mama` assessment and keeps a ledger. Import — never recompute:

```bash
pip install "mama-tools[autonomy]"
mama-tools portfolio registry/ --ledger ledger.yaml
```

The autonomy columns display the six-dimension profile and safe grant level
**exactly as issued**, version-stamped (`ruleset_version`). If the domain is
pure automation, this row stays empty — a project may automate without
delegating authority, and the model must represent that honestly.

✏️ *Exercise:* install the `[autonomy]` extra (or skip) and view your
portfolio. Confirm the view prints the no-blending rule.

## Lesson 5 — Operate, attribute, review · ~15 min

**Read:** [value framework](value-framework.md) gates 4–6,
[risk-value interpretation](risk-value-interpretation.md), and the
[lifecycle](lifecycle.md).

At the review gate: observed deltas vs. baseline with an
[attribution status](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics/blob/main/guidance/attribution.md)
(partially established is honest and common), the **shadow report** (adverse
and distributional effects — a value claim without its shadow returns to the
previous gate), and an owned decision: continue / adjust / expand /
constrain / retire, recorded with rationale in the use-case record.

✏️ *Exercise:* draft the decision entry for your use case's first review —
including what evidence would have changed the decision.

## Lesson 6 — Where this goes next · ~5 min

- **Practice maturity:** profile the operating practice with the
  [maturity model](maturity-model.md) and read it beside the autonomy
  profile ([ADR-004](decisions/adr-004-practice-maturity-model.md)).
- **External mapping:** when someone asks "does this satisfy NIST/ISO/OECD?",
  start from the [crosswalks](crosswalks.md) — coverage and gaps, never
  equivalence.
- **The pilot:** MAMA and `mama` are [pilot-stage](limitations.md) until the
  multi-organization validation reports. Using the method on a real use case
  and reporting back is the highest-value contribution
  ([CONTRIBUTING](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/CONTRIBUTING.md)).

## Check yourself

1. A stakeholder asks for "the MAMA score" of a project. What do you say?
   *(There isn't one — automation measures and autonomy profiles stay
   separate by ADR-003; the join is the use-case ID, not a number.)*
2. Your use case automates a process and delegates zero decision rights.
   Does MAMA apply? *(Yes — component 5 may be empty; automation measurement
   and value work stand alone.)*
3. The autonomy profile shows safe level L3 and the value metrics look
   great. Who decides to expand, and how? *(The grantor, via `mama`'s own
   review process with its own evidence rules — MAMA context informs but
   never authorizes; see [integration contract](integration-contract.md).)*
4. What must accompany every baseline you record? *(Card id + version, a
   value label, window, and ideally a data-quality note.)*
