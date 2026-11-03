# MAMA Role Model

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

Roles are functions, not job titles; one person may hold several — except where separation is required. Every artifact names its role holders.

## Decision-side roles

| Role | Holds | Required separation |
|---|---|---|
| **Investment owner** | The investment rationale and the continue/adjust/expand/constrain/retire decision | Not the sole interpreter of the evidence for their own decision |
| **Use-case owner** | The use-case record, scope, intended outcomes, day-to-day accountability | — |
| **Decision owner** (per review) | Signs a specific recorded decision | Named per decision; not always the investment owner |

## Measurement-side roles

| Role | Holds |
|---|---|
| **Metric owner** | Each metric card's definition, data quality, and review cadence (one named owner per card) |
| **Assessor** | Applies the workflow/decision-rights mapping and supports `mama` assessments; works from documented rules |
| **Second assessor** | Dual-assesses a sample in pilots; disagreements are recorded, not resolved silently |
| **Data steward** | Data minimization, permission, retention, redaction for the use case's evidence |

## Autonomy-side roles (consumed from `mama`)

| Role | Holds |
|---|---|
| **Grantor** | Grants and re-reviews each autonomy contract (upstream `mama` field) — must be accountable for the domain granted |
| **Autonomy reviewer** | Runs the contract review at cadence; may adjust scope, guardrails, or level through the contract process |

MAMA never edits autonomy levels, dimension scores, or weakest-link outputs; changes flow through the upstream `mama` contract/review process and are re-imported with their new version.

## Assurance-side roles

| Role | Holds |
|---|---|
| **Risk/control owner** | Each hazard's controls, tests, and residual-risk acceptance |
| **Human oversight owner** | The design and staffing of human oversight, stop/rollback paths |
| **Obligation owner** | Legal/sector obligations per jurisdiction — with qualified legal review where interpretation is required |

## Stakeholder & governance roles

| Role | Holds |
|---|---|
| **Affected stakeholder representative** | Voice of affected workers/customers/public in reviews — required for higher-risk tiers |
| **Stewardship Council member** | Charter, identity, priorities, claims (see org [GOVERNANCE.md](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/GOVERNANCE.md)) |
| **Repository maintainer** | Named accountable owner per repository/asset (see each repo's `MAINTAINERS.md`) |
| **Tool maintainer** | Tool releases, compatibility declarations, security fixes |

## Separation rules

- **Method steward ≠ assessment subject ≠ tool vendor ≠ independent evaluator.** Where one organization would hold two of these, the review records the conflict and adds independent challenge.
- **Grantor ≠ grantee.** Nobody grants autonomy to their own decisions.
- **Metric owner ≠ benefit claimant.** The person whose benefit is claimed does not own the metric definition or the attribution method.
