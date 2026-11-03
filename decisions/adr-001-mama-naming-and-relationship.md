# ADR-001: MAMA naming and the MAMA ↔ `mama` relationship

**Status:** accepted (2026-11-04, artifact draft) · **Supersedes:** none

## Context

Two entities share the word MAMA:

1. The umbrella framework/organization — displayed by the GitHub org (slug `Measuring-Automation-Managing-Autonomy`).
2. The lowercase `mama` method (*measuring and managing autonomy*) — canonical home [`emmanuel-a-otchere/MeasuringAndManagingAutonomy`](https://github.com/emmanuel-a-otchere/MeasuringAndManagingAutonomy), ruleset v2.0.0, ledger schema 2.

The organization's original display name used "**Managing** Autonomy", which collides with the `mama` method's expansion and mis-describes the umbrella. The CR (MAMA-ORG-CR-001) fixes the umbrella's expansion as **Measuring Automation & Measuring Autonomy** and requires the two identities to stay distinct.

## Options

1. Rename the org slug to match the new expansion.
2. Keep the slug; change display name, about text, and all documentation to the CR expansion.
3. Merge identities — present `mama` as simply "the MAMA toolkit".

## Decision

**Option 2.** The slug remains `Measuring-Automation-Managing-Autonomy` (stability, links, history). The visible identity everywhere (org display name, profile README, repo descriptions, docs, tools, publications) is:

> **MAMA — Measuring Automation & Measuring Autonomy**,
> which uses the **`mama` (measuring and managing autonomy)** method for its autonomy-governance component.

`mama` stays lowercase in prose and code, links to its canonical home, and keeps its own ownership, repositories, and scores. MAMA's automation measurement is its own capability, never represented as supplied by the `mama` autonomy score.

## Consequences

- A permanent, visible **relationship diagram/table** lives in the org profile README and is referenced by every repository.
- Docs must use the case-sensitive convention on first reference; CI-level checks may be added later.
- The slug/expansion mismatch is accepted and documented here — the display identity is authoritative, not the URL.

## Dissent / unresolved

None recorded at acceptance. If maintainers later choose to rename the slug, this ADR must be superseded with redirect plans for all published links.
