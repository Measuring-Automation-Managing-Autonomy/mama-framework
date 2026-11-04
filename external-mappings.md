# External Mappings & Crosswalks

**Status:** draft (v0.1.0) · **License:** CC-BY-4.0

MAMA complements external frameworks; it replaces none of them. This document defines how crosswalks are built and what they may claim. **No external body endorses MAMA, and MAMA never implies equivalence, conformity, or certification.**

## Crosswalk discipline

Every mapping entry states:

1. **Authority & version** — the external source and the specific version/profile mapped.
2. **Mapped scope** — which MAMA asset (component, template, metric, artifact) relates to which external requirement/outcome.
3. **Gaps both ways** — what the external framework requires that MAMA does not provide, and vice versa.
4. **Usage limits** — legal/sector interpretations are jurisdiction-specific and require qualified review.
5. **Owner & review date** — named maintainer, reviewed cadence.

Mappings live with the Framework & Interoperability Group and change via ADR once this document reaches `reviewed` status.

## Current mapping intents

| External source | Version basis | MAMA uses it for | What MAMA does **not** claim |
|---|---|---|---|
| [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) | AI RMF 1.0 + Generative AI Profile as applicable | Risk-lifecycle alignment for component 6 (risk, assurance & impact); vocabulary for Govern/Map/Measure/Manage activities | Equivalence, conformity, or that MAMA output satisfies any NIST profile |
| [ISO/IEC 42001](https://www.iso.org/standard/42001) | Published standard | Organizational AI-management context: roles, documented information, continual improvement analogies | That using MAMA is or supports certification. Certification requires accredited audit processes |
| [ISO/IEC 23894](https://www.iso.org/standard/77304.html) | Published standard | AI-risk guidance for the risk/impact review template | Conformity or equivalence of MAMA records to the standard's requirements |
| [OECD AI Principles](https://www.oecd.org/en/topics/ai-principles.html) | Updated principles | Value anchors for human agency, oversight, accountability, and trustworthy-AI reporting | That MAMA usage constitutes OECD compliance |
| [TM Forum assets](https://www.tmforum.org/) — **GB1040** (MAMA Framework Guidebook), **GB1042A** (AOMM), **IG1301** (MAMA Whitepaper) only, per the [TM Forum reference policy](https://github.com/Measuring-Automation-Managing-Autonomy/.github/blob/main/GOVERNANCE.md) | Current published versions | Prior art for value-cadence framing (IG1301, GB1040) and operations-maturity assessment (GB1042A); sector input for telecom/network operating patterns | Ownership of the "MAMA" name in TM contexts; equivalence of methods; any endorsement; no stage-to-level or model-to-model mapping in either direction. The TM Forum programme is a separate, authoritative industry asset |
| [OWASP GenAI Security Project](https://genai.owasp.org/) | Current guides | Threat-scenario categories for the risk/impact review of LLM/agent use cases | That MAMA provides security testing or attestation |
| [MITRE ATLAS](https://atlas.mitre.org/) | Current knowledge base | Adversarial test-design vocabulary for AI systems in the inventory | Coverage claims or assessment validity statements |
| Applicable legislation & sector regulation | Per jurisdiction | Requirement identification *inputs* for the obligation register (lifecycle stage 4) | **Any legal interpretation.** Legal mapping is jurisdiction-specific and requires qualified counsel; MAMA records obligations, it does not interpret them |

Sector Working Groups may propose additional mappings by documenting authority, scope, and version, without silently changing the core model.

## Non-endorsement statement

References to external frameworks are for orientation and interoperability. MAMA is not affiliated with, endorsed by, reviewed by, or approved by any of these bodies. Names and standards belong to their owners; standards texts must be purchased or accessed through their publishers and are not reproduced here.
