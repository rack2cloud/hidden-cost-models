# Hidden Cost Models
### The Rack2Cloud Taxonomy for Architecturally-Created, Structurally-Invisible Cost

![Status](https://img.shields.io/badge/status-canonical--taxonomy-64748b)
![Pillar](https://img.shields.io/badge/pillar-Cross--Pillar-64748b)

> **Taxonomy Principle:** A hidden cost is not an expense that was hidden from view. It is a cost that architecture itself created, structurally, before any review process existed that could have seen it. The consequence arrives before the dependency is recognized — that ordering is the defining property, not the size of the bill.

---

## About This Repository

This repository is the canonical source of truth for what qualifies as a **Hidden Cost Model** on Rack2Cloud — a cross-pillar classification, not a pillar-owned one. It does not decide what gets published, when, or in what post. It decides one thing only: does a given mechanism belong in this taxonomy.

Hidden Cost Models cut across AI Infrastructure, Cloud Strategy, Virtualization, Modern Infrastructure & IaC, and Data Protection. Some are Rack2Cloud framework registry entries that happen to describe a hidden-cost mechanism. Some are cost/exposure models that were never minted as frameworks at all, because they were built around a formula rather than a failure-state definition. Both belong here if they pass the qualification test below. Neither belongs here by default.

This repository governs **taxonomy membership only**. It does not govern editorial routing — whether a given signal or post becomes part of a specific Hidden Cost Models article. That is a separate, internally governed decision. See "Relationship to Editorial Routing" below.

---

## The Hidden Cost Model Qualification Test

A candidate qualifies as a Hidden Cost Model only if **all four** of the following hold:

1. **Architecturally created.** The cost is produced by an architectural decision or structural pattern — not by an operational mistake, a vendor error, or a one-time event.
2. **Invisible at decision time — model-absent, not merely unmonitored.** The cost is not represented in the procurement, budgeting, operational, or governance review *models* used to evaluate the decision that creates it. This is a stronger claim than "nobody happened to look": a cost that existing instrumentation could in principle surface with a better dashboard is a visibility gap, not a Hidden Cost Model. A cost whose driving mechanism has no representation in any review model at all — because that model was built around a different assumption entirely — is the target of this taxonomy. Test: could a more thorough version of the *existing* review process have caught this, or does catching it require a different review model altogether? If the former, it fails this criterion.
3. **Consequence precedes recognition.** The organization experiences the consequence before it recognizes the dependency that produced it.
4. **Generalizable.** The mechanism generalizes across technologies and vendors — it is not specific to one implementation.

All four must hold. A candidate that fails any one of them is not a Hidden Cost Model, regardless of how architecturally interesting or costly it is.

**Guardrail:** Criterion 2's model-absence framing explains the *mechanism* of invisibility — it does not redefine the taxonomy. Cost remains load-bearing in Criterion 1. A mechanism that is invisible to every existing decision model but has no cost dimension at all does not qualify; decision-model blindness is the reason a genuine Hidden Cost Model stays hidden, not an alternate criterion that can substitute for cost.

![Hidden Cost Model Qualification Test — four sequential gates showing a passing mechanism versus a false positive stopped at gate two](https://www.rack2cloud.com/wp-content/uploads/2026/08/hidden-cost-model-qualification-test.jpg)


### Common False Positives

A taxonomy without a documented miss case expands until it swallows everything. These are candidates that look like a fit and aren't. The BMC firmware RCE signal below is the taxonomy's current documented miss case — no additional negative example is required to consider the qualification test calibrated, though a Criterion-2-specific miss (architecturally created, generalizable, consequence-precedes-recognition, but still visible to existing models) would be useful future calibration if one surfaces.

| Candidate | Why It Fails |
|---|---|
| Capacity planning shortfall | Cost was visible beforehand — fails test 2 |
| Known licensing increase | Cost was disclosed and measurable — fails test 2 |
| Standard technical debt backlog | Recognized by existing review mechanisms — fails test 2 |
| BMC firmware RCE signal | Real operational-risk cost, but not architecture-created — fails test 1. Also a documented editorial-routing miss case: looked cost/risk-adjacent on framing, proved a different (Operational Resilience) thesis on inspection |

---

## Taxonomy Structure

Organized by **registry residency**, not by asset type. Residency is a durable, pipeline-tracked property; asset type (framework vs. formula vs. assessment model) is not tracked anywhere and would force a restructure the moment a future framework includes a formula, or a future non-framework model needs a home.

![Hidden Cost Models Taxonomy Structure — framework registry members versus associated models, organized by residency not asset type](https://www.rack2cloud.com/wp-content/uploads/2026/08/hidden-cost-models-taxonomy-structure.jpg)

### Part I — Framework Registry Members

Mechanisms with an existing entry in Rack2Cloud's internal framework registry.

| Framework | Failure State | Notes |
|---|---|---|
| #81 Latency Debt | — | Accumulated performance/cost penalty when placement decisions defer latency until it must be bought back through architecture change |
| #82 False Completion | — | Operation reports success by system metrics while the underlying objective was not met |
| #115 Control Plane Capture | — | Authority concentration cost invisible in normal reviews until alternatives become impractical |
| #132 Coordination Density | — | Orchestration/governance overhead required to produce a unit of agentic execution, absent from Compute Density-oriented capacity and cost models by construction, not merely under-instrumented |
| #154 Governance Legitimacy Boundary | Governance Theater | Governance structures exist, are documented, and are staffed, but cannot produce a revocation decision, an audit result, or a challenge to a specific delegation |

Framework and failure state are recorded as separate fields deliberately — they are not interchangeable, and collapsing them into one label ("#154 Governance Theater") loses the distinction between the mechanism and its named failure signature.

**Candidate provenance — #132 Coordination Density.** Initially held rather than admitted on first pass. Initial concern: could be interpreted as ordinary resource consumption (CPU cycles are expensive) rather than a hidden-cost mechanism, which would fail Criterion 2. Resolution: direct evidence review against the post's actual body text ([`/cpu-coordination-density-agentic-ai/`](https://www.rack2cloud.com/cpu-coordination-density-agentic-ai/)) found that coordination-specific cost drivers — orchestration calls per task, memory/context arbitration latency, cross-agent lock contention, policy-evaluation cycles per request — are absent from the capacity and cost review *models* currently in use, not merely unmonitored inside models that could otherwise see them (per the sharpened Criterion 2 above). Confirmed via the post's own framing of the Xeon supply shortage as a pre-existing dependency exposed by an external event, not created by it — the same hidden-dependency-exists-before-trigger shape as #115 and Cloud Concentration Risk. Preserved here as precedent for reviewing future borderline candidates that read as resource consumption on a secondhand summary but may pass on direct-text review.

### Part II — Associated Models and Mechanisms

Cost/exposure mechanisms with no framework registry entry.

Unlike Part I, Part II captures mechanisms that satisfy the Hidden Cost Model qualification test but do not resolve into reusable framework-registry failure-state definitions. These residents are expressed as formulas, evaluative models, architectural lenses, or decision-analysis mechanisms whose value lies in exposing hidden exposure rather than defining a reusable architectural failure state.

#### Cloud Concentration Risk

**Status:** Confirmed

`Business Impact × Duration × Dependency Concentration = Exposure` — no framework residency; belongs here by formula, not by registry number.

Confirmed after review against all four qualification criteria.

Criterion 1: exposure is created by architectural concentration decisions, not by the triggering event that later reveals it.

Criterion 2: dependency concentration is typically absent from procurement, cost, and resilience review models as an explicit decision variable; reviews evaluate the component being adopted, not the aggregate concentration being accumulated.

Criterion 3: organizations experience the consequence only when an outage, commercial dispute, regulatory action, or platform dependency event reveals the concentration that already existed.

Criterion 4: the mechanism generalizes across cloud providers, SaaS platforms, infrastructure vendors, and internal platform dependencies.

Residency: Part II because the model is expressed as a formula rather than a framework-registry failure-state definition.

#### Access Authorization Gap

**Status:** Confirmed

Self-attestation as a purpose-verification control produces an answer without independently establishing the fact it exists to verify — architecturally created by the self-attestation design choice, not an operational lapse.

Full-body evidence review against [Access Authorization Gap](https://www.rack2cloud.com/access-authorization-gap/) confirmed all four criteria. 

Criterion 1: the gap is produced by the self-attestation control design itself — any system adopting self-attestation as its purpose-check inherits this gap by construction, not by accident. 

Criterion 2 (deterministic test applied): the standard entitlement/access review ("does this identity hold a grant that technically covers this resource") cannot surface a self-attestation gap no matter how thoroughly it is run, because it is structurally asking a different question than purpose-verification asks; catching it requires a different review model, not a more thorough version of the existing one. Model-absent, not merely unmonitored. 

Criterion 3: the control fired and logged an answer that verified nothing; the consequence surfaced only after the architectural decision was already operating, not at decision time. 

Criterion 4: the post demonstrates recurrence across three independent layers within its own body — GhostApproval (AI coding-assistant approval, human-in-the-loop), the Entra ID exploitation status reversal (vendor-scale self-attestation with no independent customer-side check), and Session Control Gap (downstream sibling failure, same lifecycle) — same underlying shape: a control producing an answer without independently establishing the condition it claims to verify. 

Residency: Part II because the mechanism functions as an evaluative lens for identifying purpose-verification failures rather than a reusable framework-registry failure-state definition. Preserved here as a second worked example of the Criterion 2 "model-absent" test, alongside #132 Coordination Density's provenance above, for future borderline-candidate reference.

---

## Relationship to Editorial Routing

Classification under the Hidden Cost Models taxonomy does not imply eligibility for inclusion in a specific Hidden Cost Models article. Editorial routing is governed separately, by Rack2Cloud's internal editorial process.

Taxonomy membership is **necessary but not sufficient** for series-post inclusion:

- A mechanism that fails the taxonomy test is never an editorial-routing candidate, regardless of narrative fit.
- A mechanism that passes the taxonomy test does not automatically satisfy the editorial process's own series test (survives on its own merits / proves the specific installment's thesis / the post is measurably weaker without it).

This repository answers "does this mechanism belong in the taxonomy." The editorial process answers "does this signal belong in this specific post." They are different questions at different altitudes, evaluated separately, by design.

---

## Non-Goals

- General AI/cloud cost optimization guidance unrelated to the architecturally-created/structurally-invisible pattern
- Vendor pricing comparisons
- Operational incident cost accounting (costs visible at the time of the decision that created them)
- A general "cost is bad" catalog — the qualification test exists specifically to keep this narrow

---

## Maintenance Notes

This repository is the authoritative source for Hidden Cost Models taxonomy membership. It is maintained against the Rack2Cloud [Canonical Architecture Specifications](https://www.rack2cloud.com/canonical-architecture-specifications/) governance system, including the internal framework registry (residency truth) and the internal editorial-routing process. Framework entries in Part I are pulled from registry truth, not restated independently — if the registry updates a framework's name, failure state, or status, this file's Part I table should be checked for drift at that time.

New candidates (framework or non-framework) are added only after an explicit qualification-test pass — recorded in the Part I table with status, or as a new Part II registry entry with status. Pending candidates stay marked Pending Validation until an evidence review is completed and documented — never promoted on title or thesis-summary recognition alone.

---

## Support

Architectural taxonomy maintained by [Rack2Cloud](https://www.rack2cloud.com)
