# Baseline & Value Hypothesis

**Status:** draft template · Gate: lifecycle stage 2. Complete **before** deployment scale-up.

| Field | Value |
|---|---|
| **MAMA use-case ID** | `usecase-…` |
| **Metric library version** | e.g. mama-metrics v0.1.0 |
| **Baseline window** | from – to (state why this window is representative) |
| **Measurement mode** | observed / estimate / forecast *(label every number below)* |
| **Attribution method** | before/after with confound handling; matched comparison; controlled rollout; none (say so) |

## 1. Baseline metrics
<!-- Use mama-metrics card definitions verbatim; record card version + any local deviation. -->

| Metric (card ID + version) | Baseline value | Unit | Data source | Sampling | Data-quality notes |
|---|---|---|---|---|---|

## 2. Value hypothesis
- **If** we automate/delegate **______**,
- **then** metric **______** will change from **A** to **B** within **window**,
- **because** mechanism **______**,
- **and** we will accept this as success **only if** **______**.

## 3. Expected adverse effects (commit to measuring these too)

| Possible adverse effect | Affected group | How we'll detect it | Threshold for concern |
|---|---|---|---|

## 4. Uncertainty & limits
- Known confounds (seasonality, other initiatives, staffing changes):
- Data-quality risks (coverage, latency, definitions drift):
- What would make this measurement invalid:

## 5. Sign-off
| Role | Name | Date | Note |
|---|---|---|---|
| Use-case owner | | | |
| Investment owner | | | |
| Metric owner | | | |
