# MAMA ↔ `mama` Integration Contract

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0
**Implemented by:** [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations) · **Upstream:** [`emmanuel-a-otchere/measuring-and-managing-autonomy`](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy)

This is the versioned interface between MAMA (Measuring Automation & Measuring Autonomy) and the lowercase `mama` (measuring and managing autonomy) method. The upstream repository is canonical for autonomy vocabulary, the L0–L5 scale, autonomy contracts, the ledger, and scoring. MAMA consumes; it never redefines.

## What MAMA consumes

| Upstream artifact | Format | Current version | How |
|---|---|---|---|
| Autonomy assessment ("scorecard") | JSON from `autonomy-score --json` | ruleset `2.0.0` | `mama_integrations.assessment.import_assessment()` |
| Autonomy Ledger | YAML, top-level `schema: 2` | ledger schema `2` | `mama_integrations.ledger.load_ledger()` |

### Assessment record (as issued by upstream)

MAMA stores and displays these fields verbatim:

```json
{
  "ruleset_version": "2.0.0",
  "scores": { "D1": 0, "D2": 0, "D3": 0, "D4": 0, "D5": 0, "D6": 0 },
  "safe_grant_level": 0,
  "granted_level": null,
  "notes": ["…"],
  "recommended_move": "…"
}
```

Dimensions: D1 decision clarity, D2 capability, D3 guardrails, D4 telemetry, D5 transparency, D6 accountability — each 0–5. Safe-grant level is upstream's weakest-link rule `min(D3, D4, D6)`. L0 is the Submarine Line (no autonomy granted); L1–L5 are the definitive delegated levels.

### Ledger contracts (as issued by upstream)

`contracts[]` entries carry: `id`, `unit`, `domain`, `level` (0–5), `scope`, `guardrails[]`, `telemetry[]`, `revocation_triggers[]`, `escalation`, `grantor`, `horizon`, `last_review`, `review_cadence_days`, `status` (`active | expired | revoked | draft`), `notes`. MAMA validates structure (per upstream field rules) and passes content through unmodified.

## Binding rules

1. **Pass-through, exactly as issued.** MAMA displays scores, levels, notes, and recommended moves verbatim, with the `ruleset_version` / `schema` recorded alongside every stored record. It never renames, re-weights, re-computes, or "translates" upstream outputs.
2. **No scoring logic in MAMA.** Weakest-link, level definitions, dimension semantics, and the two-clean-cycles expansion rule live upstream. Any fork, vendoring, or reimplementation requires an explicit maintainer agreement, compatible licensing, provenance records, and a compatibility plan — recorded as an ADR before code exists.
3. **Fail closed on unknown versions.** An unknown `ruleset_version` or ledger `schema` fails the import with a clear error naming supported versions. Retired inputs (ledger `schema: 1`, pre-versioning files) may load with a loud retired-scale warning pointing at upstream's migration guidance — never silently.
4. **Reviews stay in `mama`.** Expand / contract / re-shape / revoke decisions come from the upstream governance loop. MAMA context (automation outcomes, value signals) is an *input* a grantor may consider — never an override of the method, and never applied by editing scores.
5. **Correlation is the interface.** MAMA may report relationships between automation metrics and autonomy outputs (e.g., does an expanded grant coincide with changed completion/exception rates?) as *descriptive* statements, unless a causal design justifies more. No composite blending (see [ADR-003](decisions/adr-003-no-composite-score.md)).
6. **Linkage, not merging.** MAMA use cases link to `mama` units/domains/contracts through the mapping file (below). The link carries identifiers and versions only — never a merged identity.
7. **Data minimization.** Imports carry scores, levels, versions, dates, and links to evidence — not raw evidence copies. Unit names may be redacted for wider audiences. Everything runs locally/offline; no telemetry is centralized.

## Linkage file (MAMA use case ↔ `mama` domain)

A mapping record joins one MAMA use case to one autonomy domain's contract:

```yaml
mappings:
  - mama_use_case_id: usecase-payments-disputes   # MAMA side, stable ID
    project_id: proj-2026-014                     # MAMA side
    mama_unit: payments-team                      # upstream `mama` side
    mama_domain: production-deploys
    mama_contract_id: payments-deploys-v2
    ruleset_version: "2.0.0"                      # recorded with the link
    ledger_schema: 2
    linked_at: 2026-11-04
    note: >
      Contract displayed as issued; MAMA automation metrics tracked separately.
```

Schema and validation: [`mama-integrations/contracts/usecase-mapping.schema.json`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations/blob/main/contracts/usecase-mapping.schema.json).

## Compatibility policy

The compatibility matrix lives in [`mama-integrations/compatibility.md`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations/blob/main/compatibility.md). Summary:

| Upstream change | Upstream bump | MAMA behavior |
|---|---|---|
| No scored-output change | PATCH | Compatible |
| Additive optional metadata | MINOR | Compatible; importers ignore unknown optional fields |
| Clarified wording | MINOR | Comparable with footnote; re-run at next review cadence |
| Re-scoring (items, levels, dimensions, weights, weakest link) | MAJOR | **Not comparable** — requires re-baseline; MAMA importer accepts only if explicitly added to the support matrix, with migration notes |

## Change process

Changes to this contract require an ADR in [`decisions/`](decisions/) and coordination with the upstream maintainers. MAMA's importer declares supported upstream versions in code (`mama_integrations/versions.py`) and documentation, and CI tests the fail-closed behavior against unknown versions.
