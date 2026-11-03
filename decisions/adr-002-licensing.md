# ADR-002: Licensing — CC-BY-4.0 for definitions, Apache-2.0 for code

**Status:** accepted (2026-11-04, artifact draft) · **Supersedes:** none

## Context

MAMA publishes two kinds of assets: definitions (charter, glossary, metric cards, schemas-as-specification) that organizations and researchers must be able to reuse and adapt with attribution, and executable code (adapters, validators, future tools) that enterprises must be able to run and integrate without copyleft obligations on their own systems. The upstream `mama` repository is MIT-licensed; MAMA consumes its versioned *outputs* (JSON assessments, YAML ledgers), not its code.

## Options

1. Single license everywhere (MIT / Apache-2.0 / CC-BY-4.0 variants).
2. Split: CC-BY-4.0 for definition assets, Apache-2.0 for code.
3. Copyleft (GPL family) for code.

## Decision

**Option 2**, per the org [LICENSE-POLICY](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/LICENSE-POLICY.md):

- **CC-BY-4.0** — `mama-framework`, `mama-metrics` (cards/schemas/docs), org policy docs, future example/learning content.
- **Apache-2.0** — `mama-integrations`, `mama-tools`, and any executable code under other repos.

Rationale: CC-BY-4.0 keeps definitions open with attribution and survives paper/diagram reuse; Apache-2.0 adds an explicit patent grant for code, which matters for enterprise adoption of adapters and tools.

## Consequences

- Dual-licensed repos state the split in their README.
- Contributions are accepted under the repo's stated license(s) only — no CLA, no additional terms.
- Consuming upstream `mama` MIT-licensed *outputs* and pointing at its MIT *code* is compatible; MAMA still does not vendor or reimplement upstream logic without an explicit maintainer agreement (see [integration contract](../integration-contract.md)).

## Dissent / unresolved

None recorded at acceptance.
