# Risk / Impact Review

**Status:** draft template · Gate: lifecycle stage 4. Re-run at review cadence and after incidents.

| Field | Value |
|---|---|
| **MAMA use-case ID** | `usecase-…` |
| **Risk tier** | low / medium / high |
| **Review date & reviewers** | |
| **`mama` ruleset version in context** | e.g. 2.0.0 *(recorded, never re-scored here)* |

## 1. Hazard register

| # | Hazard / failure mode | Affected group | Likelihood (justified, not scored) | Impact | Controls (existing) | Control owner | Control test & date | Residual risk & acceptor |
|---|---|---|---|---|---|---|---|---|

## 2. Threat scenarios (security)
<!-- Vocabulary: OWASP GenAI / MITRE ATLAS categories — orientation, not attestations. -->

| # | Scenario | Vector (e.g. prompt injection, data poisoning, model DoS) | Prevention | Detection | Response |
|---|---|---|---|---|---|

## 3. Human oversight design

| Delegated decision (domain / contract ID) | Oversight mode (in-loop / on-loop / after) | Who oversees | Authority to stop/override | Stop/rollback test date |
|---|---|---|---|---|

## 4. Obligations register
<!-- Jurisdiction-specific. Record the obligation and its source; interpretation requires qualified review. -->

| Obligation | Jurisdiction / sector | Source (instrument, section, version) | How this use case meets it | Evidence link | Owner |
|---|---|---|---|---|---|

## 5. Impact screening

| Dimension | Screening question | Finding | Follow-up needed |
|---|---|---|---|
| Workforce | Do roles, skills, headcount, or oversight burden change? | | |
| Customers/service | Does service quality, access, or redress change? | | |
| Fairness/rights | Could effects differ across groups? | | |
| Privacy | What personal data is processed; minimization applied? | | |
| Safety | Any physical-safety surface (robots, OT, networks)? | | |
| Environment | Material energy/resource effects? | | |

## 6. Incident learning
- Incidents since last review (link to evidence register):
- What changed because of them:
- Revocation triggers touched? (cross-check `mama` ledger `revocation_triggers`)

## 7. Decision
- Residual risk accepted by (name/role), date:
- Conditions/restrictions imposed:
- Open questions & dissent (recorded, not resolved by force):
