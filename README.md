# Hidden Cost Models
### The Rack2Cloud Taxonomy for Architecturally-Created, Structurally-Invisible Cost

![Status](https://img.shields.io/badge/status-canonical--taxonomy-64748b)
![Pillar](https://img.shields.io/badge/pillar-Cross--Pillar-64748b)

> **Taxonomy Principle:** A hidden cost is not an expense that was hidden from view. It is a cost that architecture itself created, structurally, before any review process existed that could have seen it. The consequence arrives before the dependency is recognized — that ordering is the defining property, not the size of the bill.

---

## About This Repository

This repository is the canonical source of truth for what qualifies as a **Hidden Cost Model** on Rack2Cloud — a cross-pillar classification, not a pillar-owned one. It does not decide what gets published, when, or in what post. It decides one thing only: does a given mechanism belong in this taxonomy.

Hidden Cost Models cut across AI Infrastructure, Cloud Strategy, Virtualization, Modern Infrastructure & IaC, and Data Protection. Some are Rack2Cloud framework registry entries (`r2c-frameworks.json`) that happen to describe a hidden-cost mechanism. Some are cost/exposure models that were never minted as frameworks at all, because they were built around a formula rather than a failure-state definition. Both belong here if they pass the qualification test below. Neither belongs here by default.

This repository governs **taxonomy membership only**. It does not govern editorial routing — whether a given signal or post becomes part of a specific Hidden Cost Models article. That is a separate decision, governed by Rule 29 (Signal-Series Join Rule) in `skill-wp-standards.md`. See "Relationship to Editorial Routing" below.

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
| BMC firmware RCE signal (`sig_20260820_004`) | Real operational-risk cost, but not architecture-created — fails test 1. Also Rule 29's own reference miss case: looked cost/risk-adjacent on framing, proved a different (Operational Resilience) thesis on inspection |

---

## Taxonomy Structure

Organized by **registry residency**, not by asset type. Residency is a durable, pipeline-tracked property; asset type (framework vs. formula vs. assessment model) is not tracked anywhere and would force a restructure the moment a future framework includes a formula, or a future non-framework model needs a home.

![Hidden Cost Models Taxonomy Structure — framework registry members versus associated models, organized by residency not asset type](https://www.rack2cloud.com/wp-content/uploads/2026/08/hidden-cost-models-taxonomy-structure.jpg)

### Part I — Framework Registry Members

Mechanisms with an existing entry in `r2c-frameworks.json`.

| Framework | Failure State | Notes |
|---|---|---|
| #81 Latency Debt | — | Accumulated performance/cost penalty when placement decisions defer latency until it must be bought back through architecture change |
| #82 False Completion | — | Operation reports success by system metrics while the underlying objective was not met |
| #115 Control Plane Capture | — | Authority concentration cost invisible in normal reviews until alternatives become impractical |
| #132 Coordination Density | — | Orchestration/governance overhead required to produce a unit of agentic execution, absent from Compute Density-oriented capacity and cost models by construction, not merely under-instrumented |
| #154 Governance Legitimacy Boundary | Governance Theater | Governance structures exist, are documented, and are staffed, but cannot produce a revocation decision, an audit result, or a challenge to a specific delegation |

Framework and failure state are recorded as separate fields deliberately — they are not interchangeable, and collapsing them into one label ("#154 Governance Theater") loses the distinction between the mechanism and its named failure signature.

**Candidate provenance — #132 Coordination Density.** Initially held rather than admitted on first pass. Initial concern: could be interpreted as ordinary resource consumption (CPU cycles are expensive) rather than a hidden-cost mechanism, which would fail Criterion 2. Resolution: direct evidence review against the post's actual body text (`/cpu-coordination-density-agentic-ai/`) found that coordination-specific cost drivers — orchestration calls per task, memory/context arbitration latency, cross-agent lock contention, policy-evaluation cycles per request — are absent from the capacity and cost review *models* currently in use, not merely unmonitored inside models that could otherwise see them (per the sharpened Criterion 2 above). Confirmed via the post's own framing of the Xeon supply shortage as a pre-existing dependency exposed by an external event, not created by it — the same hidden-dependency-exists-before-trigger shape as #115 and Cloud Concentration Risk. Preserved here as precedent for reviewing future borderline candidates that read as resource consumption on a secondhand summary but may pass on direct-text review.

### Part II — Associated Models and Mechanisms

Cost/exposure mechanisms with no framework registry entry.

| Model | Status | Notes |
|---|---|---|
| Cloud Concentration Risk | Confirmed | `Business Impact × Duration × Dependency Concentration = Exposure` — no framework residency; belongs here by formula, not by registry number |
| Access Authorization Gap | Pending Validation | Candidate only — qualification test not yet run against actual post content. Do not treat as a confirmed member until an evidence review (Candidate / Evidence Review / Pass-Fail / Reason) is completed and recorded here |

---

## Relationship to Editorial Routing

Classification under the Hidden Cost Models taxonomy does not imply eligibility for inclusion in a specific Hidden Cost Models article. Editorial routing remains governed by Rule 29 (Signal-Series Join Rule) in `skill-wp-standards.md`.

Taxonomy membership is **necessary but not sufficient** for series-post inclusion:

- A mechanism that fails the taxonomy test is never a Rule 29 candidate, regardless of narrative fit.
- A mechanism that passes the taxonomy test does not automatically satisfy Rule 29's three-part series test (survives on its own merits / proves the specific installment's thesis / the post is measurably weaker without it).

This repository answers "does this mechanism belong in the taxonomy." Rule 29 answers "does this signal belong in this specific post." They are different questions at different altitudes, evaluated separately, by design.

---

## Non-Goals

- General AI/cloud cost optimization guidance unrelated to the architecturally-created/structurally-invisible pattern
- Vendor pricing comparisons
- Operational incident cost accounting (costs visible at the time of the decision that created them)
- A general "cost is bad" catalog — the qualification test exists specifically to keep this narrow

---

## Maintenance Notes

This repository is the authoritative source for Hidden Cost Models taxonomy membership. It is maintained against `r2c-frameworks.json` (framework residency truth) and `skill-wp-standards.md` Rule 29 (editorial routing). Framework entries in Part I are pulled from registry truth, not restated independently — if the registry updates a framework's name, failure state, or status, this file's Part I table should be checked for drift at that time.

New candidates (framework or non-framework) are added only after an explicit qualification-test pass, recorded in the relevant Part I/Part II table with status. Pending candidates stay marked Pending Validation until an evidence review is completed and documented — never promoted on title or thesis-summary recognition alone.

---

## Support

Architectural taxonomy maintained by [Rack2Cloud](https://www.rack2cloud.com)
