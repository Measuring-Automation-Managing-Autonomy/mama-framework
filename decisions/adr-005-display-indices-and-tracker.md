# ADR-005: Per-axis display indices and the multi-dimensional tracker

**Status:** accepted (v0.4.0, draft artifact) · **Date:** 2026-11-05 · **Decided by:** MAMA Stewardship Council (interim) · **License:** CC-BY-4.0

## Context

Adopters asked for a way to **track** automation, autonomy, and value
together over time — "an automation index and an autonomy index integrated
into a multi-dimensional plot with a value-outcome metric, as a tracker."
MAMA's existing constraints exist to prevent a specific failure: a single
composite score that hides risk and context ([ADR-003](adr-003-no-composite-score.md),
[charter principles 1 and 5](../charter.md#3-principles),
[risk-value-interpretation](../risk-value-interpretation.md)). A tracker
that plots three **separate** measures as three **separate axes** is the
construction ADR-003's risk table itself points to ("keep dimensions and
measures visible") — provided the axes are never combined.

## Decision

1. **Adopt three per-axis display indices** (v1), computed per use case and
   specified in [indices-and-tracking.md](../indices-and-tracking.md):
   - **Automation Index** — the use case's `automation-coverage` card value (as observed).
   - **Autonomy Index** — mean **granted level** across linked ledger contracts × 20,
     computed strictly from ledger values as issued, with the **minimum
     granted level as a mandatory companion floor**.
   - **Value Realization** — the `realized-vs-forecast-benefit` card value
     (may be negative; displayed unclamped).
2. **Adopt the multi-dimensional tracker**: a versioned tracker-record schema
   and a renderer (SVG trajectory plot + Markdown report) in `mama-tools`,
   with the no-cross-axis rule burned into the artifact ("Display construct —
   separate instruments, never a composite").
3. **Adopt the series interface** (CSV/JSON import of card-versioned,
   labeled metric values per use case) as the seam between an organization's
   own measurement systems and MAMA computation. The autonomy axis has **no
   CSV seam** — it flows only through the version-gated `mama-integrations`
   import.
4. **Binding rules** (full list in indices-and-tracking.md §6): no
   cross-axis arithmetic; no org-level aggregation in v1; floors always
   visible; versions travel; no targets, no ranks; absent axes stay absent
   (never imputed).
5. A **Submarine Line narrative rule**: if any linked domain's granted level
   is 0, the report must say in words that a linked domain holds no autonomy
   at all, regardless of the index value.

## Consequences

- Adopters get a legitimate tracker **without** a composite score: the
  no-collapse guarantee survives because the axes are separate instruments
  and the rule against combining them is load-bearing, documented, and
  enforced in the report format.
- `mama-tools` grows import/compute/render capabilities (v0.3.0); new
  conformance suites cover the tracker and series schemas.
- The Autonomy Index reads **only** as-issued ledger values — upstream
  `mama` remains the sole computational authority for autonomy.
- Thicker indices (weighted multi-card), portfolio-level aggregation, and a
  practice-axis are **explicitly deferred** to pilot evidence and a
  superseding ADR.

## Open questions (carried, not resolved)

- Can thicker (multi-card) indices be made valid, and for whom? Pilot.
- Is a portfolio-level view possible without erasing context? Pilot.
- Should the practice maturity profile become a fourth display axis? Pilot
  ([ADR-004](adr-004-practice-maturity-model.md)).
