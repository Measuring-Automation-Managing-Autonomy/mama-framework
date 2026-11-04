# MAMA Implementation Guide

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

From investment question to evidence-backed operating decision, in eight steps. Each step lists inputs, activity, and the artifact that proves it happened. Stage gates live in [lifecycle.md](lifecycle.md).

## Step 0 — Prepare

- Read the [charter](charter.md) and [risk & value interpretation rules](risk-value-interpretation.md) with everyone who will own a decision.
- Name the roles ([roles.md](roles.md)): investment owner, use-case owner, metric owner, assessors, data steward, grantors.
- Decide where evidence lives (local-first), who may see it, and its retention/redaction rules **before** collecting anything.

## Step 1 — Intake the project/use case
Fill the [project intake template](templates/project-intake.md): goals, scope, affected parties, jurisdictions, risk tier, and — critically — the **intended decision** ("we will use this to decide whether to expand X to region Y"). Skip this and measurement becomes decoration.

## Step 2 — Map work and decisions
Fill the [workflow & decision-rights mapping template](templates/workflow-decision-rights-mapping.md): tasks, human/system roles, automation boundaries, decision points, handoffs, exceptions, recovery paths. Mark each consequential decision: *retained by people* or *delegated → candidate autonomy domain*.

## Step 3 — Inventory technology & capability
Record models, software, robots, networks, data, vendors, versions, owners, lifecycle status. Pin versions — they are join keys for everything that follows.

## Step 4 — Fix the baseline and value hypothesis
Fill the [baseline & value hypothesis template](templates/baseline-value-hypothesis.md) using metric definitions from [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics). State expected benefits **and** expected adverse effects, plus the attribution method. All before scale-up.

## Step 5 — Assess autonomy with `mama`
For each candidate autonomy domain, run the upstream `mama` assessment and contract process at [`emmanuel-a-otchere/measuring-and-managing-autonomy`](https://github.com/emmanuel-a-otchere/measuring-and-managing-autonomy). Import results via [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations): assessments (`autonomy-score --json`) and ledger contracts (`schema: 2`), recorded **exactly as issued** with their `ruleset_version`/`schema`. Create the use-case↔domain mapping file.

## Step 6 — Review risk, controls, obligations
Fill the [risk/impact review template](templates/risk-impact-review.md): hazards, threat scenarios, control owners and tests, legal/sector obligations (jurisdiction-specific — qualified review required), human oversight design, and a tested stop/rollback path. Link to [external mappings](external-mappings.md) as orientation, never as conformity.

## Step 7 — Operate & measure
Compute metrics per card definitions; record evidence immutably (sources, versions, approvals, control tests, incidents); re-review autonomy contracts on their cadence; report adverse effects in the same view as benefits. Label observed / estimate / forecast on everything.

## Step 8 — Review & decide
Assemble the review pack: expected vs observed outcomes, automation measures, `mama` autonomy profiles (as issued), risk/control status — side by side, linked, **never merged into one score**. The decision owner records: **continue / adjust / expand / constrain / retire**, plus dissent. Autonomy changes flow through the upstream contract process; metric changes become new card versions.

## Common failure modes (and the rule that prevents them)

| Failure | Prevented by |
|---|---|
| Dashboard without method — measurements nobody decides with | Step 1's intended-decision requirement |
| Automation % as success proxy | Interpretation rules §5; balanced reporting |
| Scores edited to "fix" a review | Pass-through rule; upstream owns scoring |
| Benefit claim without baseline/attribution | Step 4 gate; interpretation §3 |
| Composite "MAMA score" appearing in a slide | ADR-003; interpretation §8 |
| Sensitive pilot data leaking into issues/examples | Data minimization; synthetic-only rule |

## Minimal viable adoption (one use case, ~2–4 weeks)

Intake + workflow map + 3–5 metric cards baselined + one `mama` assessment/contract + one risk review + one decision review. Everything runs locally; the only tooling required is the upstream `mama` CLI and the [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) card library.
