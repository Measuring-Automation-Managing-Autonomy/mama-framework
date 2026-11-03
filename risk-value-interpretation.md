# Risk & Value Interpretation Rules

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

How to read MAMA outputs without fooling yourself. These rules are binding on all MAMA tools, dashboards, and publications.

## 1. No universal targets

MAMA publishes definitions, not quotas. No metric card carries a universal target: "what is good" depends on the use case, sector, jurisdiction, and risk tier. Baselines and targets are set per use case and recorded with their rationale.

## 2. Label the measurement mode

Every number shown as **observed** (measured), **estimate** (inferred, with uncertainty), or **forecast** (projected). Never blend modes in one figure; never present a forecast where a decision expects an observation.

## 3. Attribution before causation

"Automation caused a $2M saving" requires: a recorded baseline, a defined comparison (before/after with confound handling, or matched comparison), stated assumptions, and sensitivity notes. Without that, the claim must read "outcome changed after deployment — attribution not established."

## 4. Report trade-offs and adverse effects

Every benefit report includes, in the same view: quality effects, exception/rework behavior, workforce impact (role changes, oversight burden), affected-group distributional effects, and failure behavior. A benefit claimed without its adverse-effect column is incomplete.

## 5. Automation percentage is not success

Coverage/human-touch numbers describe *what changed*, not *whether it improved*. Never rank or reward raw automation percentage without value, quality, risk, and affected-people context in the same view.

## 6. Autonomy level is not safety or compliance

A `mama` autonomy level describes **granted decision authority and its controls** — nothing else. Specifically:

- Higher is not better. L2 may be the right answer for a high-risk domain.
- Level ≠ safety, ≠ quality, ≠ legal compliance. Risk/control review (lifecycle stage 4) and qualified legal interpretation remain necessary.
- Dimension profiles, guardrails, telemetry, and review horizons are shown next to the level, never averaged away. The weakest-link rule `min(D3, D4, D6)` is displayed exactly as upstream issues it.

## 7. Portfolio comparisons disclose their construction

Any cross-use-case or cross-organization view states: metric definitions and versions, `mama` ruleset/schema versions, scope and inclusion rules, data-quality assessment, and any normalization applied. Comparisons that cannot state these are not published.

## 8. No composite MAMA score

Automation measures and autonomy outputs are shown **side by side, linked, versioned, and interpretable** — never summed, weighted, or folded into one number. A composite is prohibited until its construct, intended use, weighting, validity evidence, and limitations are established through research and governance (see [ADR-003](decisions/adr-003-no-composite-score.md)).

## 9. Decisions are owned

Every interpretation that feeds a decision names the decision owner and records the decision (continue / adjust / expand / constrain / retire) plus dissent in the evidence register. Dashboards inform; owners decide.

## 10. Boundaries on claims

Framework adoption, tool output, conformance to MAMA schemas, and pilot participation are never presented as certification, regulatory approval, conformity, safety, or effectiveness. External-framework mappings are complementarity statements only.
