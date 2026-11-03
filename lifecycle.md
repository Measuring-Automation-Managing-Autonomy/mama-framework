# MAMA Project / Use-Case Lifecycle

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

Each use case moves through seven stages. Gates are evidence checks, not ceremonies — a stage completes when its artifacts exist and their owners have signed the record.

## Stages

### 1. Intake
**Purpose:** decide whether this use case deserves measurement effort.
**Artifacts:** completed [project intake template](templates/project-intake.md) — investment rationale, scope, affected parties, jurisdictions, risk tier, intended decision use.
**Gate:** named investment owner and use-case owner; explicit intended decision ("we will use this to decide X"); risk tier assigned.

### 2. Baseline & value hypothesis
**Purpose:** fix the before-picture and the claim to be tested.
**Artifacts:** [baseline & value hypothesis template](templates/baseline-value-hypothesis.md) — baseline metrics (per [`mama-metrics`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-metrics) cards), expected benefits, expected adverse effects, attribution method.
**Gate:** baseline recorded with time window and data source; hypothesis falsifiable; attribution approach stated *before* deployment scale-up.

### 3. Map & assess
**Purpose:** describe the work, the technology, and the decision authority.
**Artifacts:** [workflow & decision-rights mapping](templates/workflow-decision-rights-mapping.md) (tasks, roles, automation boundaries, decisions, handoffs, exceptions, recovery paths); technology/capability inventory entries; `mama` assessments and autonomy contracts for each autonomy domain, imported via [`mama-integrations`](https://github.com/Measuring-Automation-Managing-Autonomy/mama-integrations) — passed through exactly as issued.
**Gate:** every consequential decision point is either inside a recorded autonomy contract or explicitly retained by people; inventory versions pinned.

### 4. Control & obligation review
**Purpose:** link the use case to hazards, controls, obligations, and oversight.
**Artifacts:** [risk/impact review template](templates/risk-impact-review.md) — hazards, threat scenarios, control owners and tests, legal/sector obligations (jurisdiction-specific, qualified review required), human oversight design, rollback/stop paths.
**Gate:** residual risk accepted by a named owner; stop/rollback path tested at least once.

### 5. Operate & measure
**Purpose:** collect evidence against baseline.
**Artifacts:** metric computations per card definitions; evidence records (immutable, versioned: data sources, assessment versions, approvals, control tests, incidents); periodic `mama` re-reviews per contract cadence.
**Gate:** data-quality notes current; adverse effects reported alongside benefits; no silent definition changes (metric changes create a new card version).

### 6. Review & decide
**Purpose:** turn evidence into an operating/investment decision.
**Artifacts:** review pack showing expected vs observed outcomes, automation measures, autonomy profiles, risk/control status — side by side, never merged; decision recorded: **continue / adjust / expand / constrain / retire**.
**Gate:** named decision owner; decision and dissent recorded in the evidence register; autonomy grants adjusted through the `mama` contract process (not by editing scores).

### 7. Retire / archive
**Purpose:** clean end.
**Artifacts:** revocation or wind-down of autonomy contracts per their triggers; final outcome record; lessons fed to framework issues.
**Gate:** ledger contracts for retired domains show `revoked`/`expired` status; archived record states which metric/tool/`mama` versions produced it.

## Cross-stage rules

- **Label measurement modes** (observed / estimate / forecast) in every artifact from stage 2 onward.
- **No composite score** at any stage (ADR-003).
- **Pilot-stage honesty:** until the organization-wide pilot completes, records produced with these artifacts are labeled pilot-stage.
- **Data minimization:** keep evidence local or minimized; redact before any external sharing.
