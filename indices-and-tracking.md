# Indices and tracking — the computational and reporting reference

> **Status:** draft (v0.4.0) · **Owned by:** MAMA Stewardship Council · **License:** CC-BY-4.0
>
> The unified reference for MAMA's **display indices** and the
> **multi-dimensional tracker**: what each index is, exactly how it is
> computed, what it must never be used for, and the report format that binds
> them. Authorized by [ADR-005](decisions/adr-005-display-indices-and-tracker.md)
> under the constraints of [ADR-003](decisions/adr-003-no-composite-score.md)
> and [charter principle 1](charter.md#3-principles).

## 1. The three axes — separate by construction

MAMA's tracker plots **three independent axes per use case**, each computed
from its own instrument, each carrying its own provenance. **No axis is ever
summed, averaged, or weighted with another** — there is no composite "MAMA
score", and ADR-005 keeps it that way. The plot is the product: the
*co-movement* of three separate measures is what a human reviewer reads.

| Axis | Index (v1) | Computed from | Scale |
|---|---|---|---|
| **X — Automation** | `automation_index` | The use case's `automation-coverage` metric-card value (as observed), with card version + window | 0–100 percent |
| **Y — Autonomy** | `autonomy_index` | Mean **granted level** across the use case's linked ledger contracts (as issued by upstream `mama`), scaled ×20 → 0–100; the **minimum granted level travels with it** as a mandatory floor field | 0–100 (floor 0–5 shown) |
| **Bubble — Value realization** | `value_realization` | The use case's `realized-vs-forecast-benefit` card value (as observed; may be negative = below forecast) | percent vs. forecast |

Why these three: they are the three questions the
[charter](charter.md#1-purpose) separates — what is automated, what
authority is delegated, and did it pay off. Each v1 index is deliberately
**thin**: one as-issued source value (or a mean over as-issued ledger
levels), not a weighted blend of heterogeneous metrics. Thicker indices are
a research question, not a v1 feature ([open questions](#7-open-questions)).

## 2. Computational definitions (v1)

### 2.1 Automation Index

```
automation_index = automation-coverage card value      (0–100, as observed)
provenance       = card_id, card_version, window, label ("observed")
```

- Source of truth: the `automation-coverage` metric card
  ([mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics)),
  computed by the use case from its own systems and imported via the
  [series interface](#4-the-series-interface-pulling-the-actual-numbers).
- If the card is unmeasured, the axis is **absent** — never imputed.

### 2.2 Autonomy Index

```
mean_level      = mean(level) over the use case's linked ledger contracts   (0–5, as issued)
min_level       = min(level) over the same contracts                        (0–5, the floor)
autonomy_index  = mean_level × 20                                           (0–100)
provenance      = ledger `schema`, `ruleset_version` in force, contract ids, count
```

- Computed **strictly from ledger values as issued** — never from
  recomputed scores, never from dimension profiles
  ([integration contract](integration-contract.md)). The weakest-link
  computation is upstream's; MAMA only reads granted levels.
- **The floor travels with the index.** A mean can hide a domain at the
  Submarine Line; every display of the index shows `min_level` beside it
  (as a floor marker on the plot). If the floor and the mean diverge by ≥ 2
  levels, the report says so in words.
- `min_level = 0` (Submarine Line in any linked domain) **caps the narrative**:
  the report must state that at least one linked domain holds no autonomy at
  all, regardless of the index.

### 2.3 Value Realization

```
value_realization = realized-vs-forecast-benefit card value   (percent vs. forecast; may be negative)
provenance        = card_id, card_version, window, label, attribution status
```

- Absent until the use case has a forecast and a measured realization
  ([value framework](value-framework.md) gate 5). Negative values are
  **displayed**, not clamped — below-forecast is a finding.

## 3. The tracker record

One **tracker record** per use case per generated point:

```json
{
  "tracker_version": "1.0.0",
  "usecase_id": "usecase-refunds-agent",
  "generated_at": "2026-11-05T09:00:00Z",
  "axes": {
    "automation":  { "value": 72.5, "card_id": "automation-coverage", "card_version": "0.1.0", "window": "2026-10", "label": "observed" },
    "autonomy":    { "index": 60.0, "mean_level": 3.0, "min_level": 2, "domains": 2, "ruleset_version": "2.0.0", "ledger_schema": 2, "contract_ids": ["refund-agent-v2"] },
    "value":       { "value": -12.5, "card_id": "realized-vs-forecast-benefit", "card_version": "0.1.0", "window": "2026-10", "label": "observed", "attribution": "partially established" }
  },
  "practice_profile": { "stages": { "D-A": 3, "D-B": 4, "D-C": 2, "D-D": 3, "D-E": 2 } },
  "provenance": { "tool": "mama-tools", "tool_version": "0.3.0" }
}
```

Schema: [`mama-tools/schemas/tracker-record.schema.json`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-tools/blob/main/schemas/tracker-record.schema.json)
(conformance suite: `mama-conformance`). Absent axes are `null` — a missing
measurement is information, never an imputation.

## 4. The series interface — pulling the actual numbers

The seam between an organization's systems and MAMA's computation is a
**flat, versioned import format** — deliberately boring so any export can
reach it:

```csv
usecase_id,card_id,card_version,window,value,label,source_note
usecase-refunds-agent,automation-coverage,0.1.0,2026-10,72.5,observed,workflow logs (export 2026-11-01)
usecase-refunds-agent,exception-rate,0.1.0,2026-10,4.1,observed,ticket classification v3
usecase-refunds-agent,realized-vs-forecast-benefit,0.1.0,2026-10,-12.5,observed,finance close 2026-10
```

JSON is accepted with the same fields. Rules:

- Every row is **card-versioned and labeled**; unlabeled rows are rejected.
- `usecase_id` must exist in the registry (linkage is explicit; no orphans).
- Rows are appended to the use case's **series** (immutable, append-only);
  recomputation of an index never edits history — it generates a new tracker
  record with a new `generated_at`.
- **Where the numbers come from** remains organization-side by design
  (data minimization, local-first): your process logs, ticketing, finance
  close, observability exports write this format. Reference connectors for
  vendor systems are deliberately out of MAMA's scope; the
  [capability map](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations/blob/main/compatibility.md)
  documents the interfaces instead.
- The **autonomy axis has no CSV seam**: it is imported from the ledger via
  `mama-integrations`, version-gated and fail-closed — the numbers that
  denote delegated authority must come through the controlled interface,
  not a spreadsheet.

## 5. The tracker plot and report

`mama-tools tracker render` produces, from a registry + series + ledger:

1. **SVG scatter/trajectory plot**: X = automation index, Y = autonomy
   index, bubble area = |value realization| (hollow = below forecast), one
   trajectory per use case across windows, floor markers for `min_level`.
   Caption burned into the SVG: *"Display construct — separate instruments,
   never a composite (ADR-003/005)."*
2. **Markdown report**: per use case — the three axes with provenance, the
   autonomy floor sentence, practice profile, and open decisions. No
   ranking section; use cases appear as separate rows, and any cross-use-case
   reading follows [risk-value-interpretation §6](risk-value-interpretation.md)
   (disclose construction; context survives).

## 6. Rules that bind every use of the indices

1. **No cross-axis arithmetic.** Automation, autonomy, and value indices are
   never summed, averaged, diffed into a "net", or weighted together.
2. **No org-level aggregation in v1.** The tracker is per use case; portfolio
   synthesis is a research question ([ADR-005 open questions](#7-open-questions)).
3. **Floors are visible.** The autonomy index never appears without
   `min_level`.
4. **Versions travel.** Card versions, `ruleset_version`, ledger `schema`,
   tool version — all inside every record.
5. **Comparability discipline.** Indices are comparable across windows of
   the **same use case** with the same card versions and ruleset MAJOR;
   cross-use-case comparison discloses construction
   ([risk-value-interpretation §6](risk-value-interpretation.md)).
6. **Not a target, not a rank.** No target lines, no leaderboards, no
   "index should rise" narratives — a rising autonomy index is not a virtue
   ([charter principle 5](charter.md#3-principles)); a falling one is not a
   failure. The plot supports decisions; it does not make them.

## 7. Open questions

- **Thicker indices?** Weighted multi-card automation indices could say more
  — and would need validity evidence per
  [ADR-003](decisions/adr-003-no-composite-score.md) before adoption.
  Deferred to the pilot.
- **Portfolio-level views?** Aggregating across use cases without erasing
  context is unsolved; deferred.
- **Practice axis?** The maturity model's profile could become a fourth,
  display-only axis; deferred until the pilot shows the practice model is
  usable ([ADR-004 open questions](decisions/adr-004-practice-maturity-model.md)).
