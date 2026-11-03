# ADR-003: No composite MAMA score

**Status:** accepted (2026-11-04, artifact draft) · **Supersedes:** none

## Context

Stakeholders keep asking for "the MAMA score" — one number blending automation performance, value, risk, and autonomy. A composite would make dashboards simpler and comparisons easier, but automation metrics measure *what changed in work*, while `mama` autonomy outputs measure *delegated decision authority and its controls*. They have different units, different validity conditions, and different failure modes when misread. The upstream `mama` method itself warns against blending autonomy scores with other measures; the CR (§5.3, §14) prohibits an unvalidated composite.

## Options

1. Publish a weighted composite MAMA score now (0–100 or similar).
2. Publish an unweighted average of normalized components.
3. No composite. Show measures side by side, linked, versioned, with disclosure rules.

## Decision

**Option 3.** There is no composite MAMA score. Portfolio and use-case views present:

- automation measures (per metric cards, with baselines and uncertainty),
- `mama` autonomy outputs (dimension profiles, safe-grant level, granted level, contracts — exactly as issued),
- risk/control status and value realization,

…linked by use-case IDs and versions, **never aggregated into one number**. Relationships between the two sides may be reported as *descriptive* observations ("expanded grants coincided with lower exception rates in 3 of 5 use cases") unless a causal design justifies more.

**A composite may only be proposed** after: (a) pilot evidence demonstrates construct validity, (b) intended use and misuse cases are documented, (c) weighting rationale and sensitivity analysis are published, (d) limitations are explicit, and (e) the change passes Stewardship Council review with upstream `mama` maintainer coordination. Until then this ADR blocks any composite in MAMA tools, dashboards, or publications.

## Consequences

- Dashboards will look "less simple" than a single-score product; that is the point.
- Requesters of "the one number" are pointed to this ADR and to [risk-value-interpretation.md](../risk-value-interpretation.md) §8.
- Tools (`mama-tools`) must enforce this: no aggregation endpoint, no blended chart types.

## Dissent / unresolved

Open question recorded: *what evidence would suffice for a composite?* Deferred to the Validation & Research Group's pilot protocol; revisit only via a superseding ADR.
