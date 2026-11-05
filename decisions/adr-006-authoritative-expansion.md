# ADR-006: Authoritative expansion of MAMA — "Measuring Automation, Managing Autonomy"

**Status:** accepted (v0.5.0, draft artifact) · **Date:** 2026-11-05 · **Decided by:** MAMA Stewardship Council (interim) · **License:** CC-BY-4.0

## Context

The acronym's expansion had been spelled inconsistently — notably
"Measuring Automation & Measuring Autonomy" — across the charter, glossary,
READMEs, templates, the upstream `mama` repository's naming box and
integration guide, and the founding change requests. The spellings are not
interchangeable: they carry different claims about who does what.

## Decision

1. The **authoritative expansion** of **MAMA** is:
   **Measuring Automation, Managing Autonomy**.
   No other spelling is permitted in any MAMA or `mama` artifact. Prior
   variants are spelling mistakes and are corrected retroactively —
   including in the founding change requests (CR MAMA-ORG-CR-001,
   CR MAMA-AUT-CR-001) and the upstream repository (v2.1.2).
2. **The comma is the constitution — it carries the division of labor:**
   - **"Measuring Automation"** is MAMA's own capability
     ([mama-metrics](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics)):
     what work is automated, how well the automated process performs, what
     value is realized. The `mama` method does not provide this.
   - **"Managing Autonomy"** is delivered by `mama` — *measuring and
     managing autonomy* — which makes delegated decision rights explicit,
     assessable, and governed. MAMA's own layers do not provide this; they
     consume it ([integration contract](../integration-contract.md)).
3. **The interlock by name:** each half of the acronym names the instrument
   that provides it. `mama` is, by name and by function, the
   managing-autonomy component of MAMA; MAMA is, by name and by function,
   the measuring-automation frame in which `mama` operates. Lowercase and
   uppercase fit together rather than overlap — no merged identity, no
   duplicated capability, no composite ([ADR-003](adr-003-no-composite-score.md)).
4. The old spelling ("Measuring Automation & Measuring Autonomy") was a
   **spelling mistake with semantic damage**: it claimed `mama` only
   *measured* autonomy — dropping the *managing* that is the method's
   entire point — and broke the name-to-function mapping above. Two
   mentions of the old form are deliberately retained where documents name
   the mistake itself (this ADR, the upstream changelog/integration guide).

## Consequences

- All artifacts corrected in the same release wave: charter, glossary,
  READMEs, policies, templates, schemas' descriptive text, upstream naming
  box/integration guide/site (upstream `mama` v2.1.2).
- [ADR-001](adr-001-mama-naming-and-relationship.md) documented a
  display-expansion vs. org-slug mismatch ("Measuring Automation &…"
  vs. the slug's `…Managing…`); **that mismatch is now resolved** — the
  authoritative expansion matches the slug's wording. ADR-001's remaining
  decisions (keep the slug; display identity is authoritative) stand.
- Future artifacts (talks, papers, diagrams, training) must use the
  authoritative expansion; deviations are spelling mistakes to fix on sight.

## Open questions

None. This is an identity decision; substantive measurement questions remain
with [ADR-004](adr-004-practice-maturity-model.md) and
[ADR-005](adr-005-display-indices-and-tracker.md).
