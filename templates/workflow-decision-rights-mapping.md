# Workflow & Decision-Rights Mapping

**Status:** draft template · Gate: lifecycle stage 3. One worksheet per use case.

## A. Workflow map

| # | Task / step | Performed by (human role / system) | Automation boundary (manual / assisted / automated) | Inputs | Outputs | Handoff to | Exception path |
|---|---|---|---|---|---|---|---|

## B. Decision points

| # | Decision | Decision holder today | Options considered per decision | Reversibility | Consequence if wrong | Consequential? (Y/N + why) |
|---|---|---|---|---|---|---|

**Consequential** = affects people's rights, money, safety, employment, access to service, or is hard to reverse. Every consequential decision must end up either (a) explicitly retained by people, or (b) inside a recorded autonomy contract.

## C. Decision-rights disposition

| Decision # | Disposition | Autonomy domain (if delegated) | Upstream `mama` contract ID | Grantor | Level (as issued) | Review horizon |
|---|---|---|---|---|---|---|
| | retained by people | — | — | — | — | — |
| | delegated | `domain-…` | `…-v1` | | *(from ledger — do not edit here)* | |

## D. Dependencies & recovery

- Systems/data this workflow depends on (with versions):
- What happens when the automated path fails (recovery path, who is paged):
- Stop/rollback path for delegated decisions (and where it is tested):

## E. Affected parties per step

| Step # | Affected group | Nature of effect (workload, discretion, quality, rights) | Representative / consultation channel |
|---|---|---|---|

## F. Notes on `mama` integration
- Assessments imported via `mama-integrations`; scores/levels recorded **exactly as issued** with `ruleset_version` and ledger `schema`.
- Mapping file reference (use-case ↔ domain/contract): (link)
- MAMA never edits levels or scores here — changes go through the upstream contract/review process.
