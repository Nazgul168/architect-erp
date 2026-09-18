# LEARNING_CANDIDATES.md

- **REVISION:** `2026-09-18-r5`
- **LAST_UPDATED:** `2026-09-18`

Durable Engagement-side staging for transferable learning identified during NURA ERP work.

## Maintenance Rule

After significant work, at each Learning & Change Review, and before material Part/phase handoff where learning may have changed:

- add all newly identified transferable candidates that meet the proportional candidate threshold;
- update existing candidates if new evidence materially changes them;
- record material Engagement artifacts created/changed because of a candidate and why;
- record explicit user disposition when it occurs; preserve `NOT_REVIEWED` when it does not;
- preserve candidate status and provenance across chats/runtimes;
- do not treat a candidate as validated Expert Memory;
- do not transfer it to permanent ARCHITECT candidate storage or EKB unless applicable confidentiality, transfer and Slow-Loop governance requirements are satisfied.

# Learning Candidates

Document status: ENGAGEMENT-SIDE CANDIDATE BACKLOG  
Engagement: ENG-NURA-ERP-001  
Candidate status: CANDIDATE ONLY  
Canonical EKB status: NOT PROMOTED  
Purpose: preserve transferable-learning candidates identified during NURA ERP Learning & Change Reviews so they are not lost between reviews.

> This file is an Engagement-side staging/backlog artifact. Nothing in it is validated Expert Memory.  
> Any transfer into permanent ARCHITECT `memory/candidates/` must first pass de-identification and applicable confidentiality/provenance review.  
> Canonical promotion to EKB is a separate governed process.


## Approval / Role Review Tracking

This Engagement file also records the user's explicit disposition of transferable-learning candidates so that, at Engagement close or another agreed review point, ARCHITECT can produce an **approved-candidate export** for a separate Role Updater / permanent-role review process.

Allowed Engagement-side disposition values:

- `NOT_REVIEWED` — no explicit user disposition has been recorded;
- `APPROVED_FOR_ENGAGEMENT_USE` — the user explicitly accepted the method/principle for use in this Engagement;
- `APPROVED_FOR_ROLE_REVIEW` — the user explicitly accepted the learning candidate for the RF Role Learning Export / later Role Updater review;
- `HOLD` — useful candidate, but the user does not yet want it advanced for Role Updater review;
- `REJECTED_BY_USER` — the user explicitly rejected the proposed transferable learning.

An Engagement-side approval recorded here is **evidence of user acceptance**, not canonical ARCHITECT Maintainer authorization and not EKB validation/promotion. Permanent ARCHITECT change remains governed by the applicable Slow-Loop process.

Where a candidate materially changes Engagement artifacts, record the artifact implementation evidence and rationale so that the Role Updater can distinguish:

1. the transferable learning itself;
2. how it was operationalized in the Engagement;
3. why the artifact change was made; and
4. whether the user explicitly approved that change/learning.

At final handoff, produce a separate export containing candidates marked `APPROVED_FOR_ROLE_REVIEW`, with the fields required by `_ROLE_LEARNING_EXPORT_TEMPLATE.md`, including approval metadata, latest evidence, limits, artifact-change history and disposition record.

### Cross-runtime continuity rule

This approval/artifact trail is Engagement-wide. A new chat/runtime using the current controlled NURA ERP sources must continue the same record rather than starting a separate informal learning history. Explicit user disposition is recorded as evidence; silence or ordinary continuation is not approval.

### Multi-actor / tool provenance rule

When learning evidence was produced through several roles, runtimes or verification instruments, the trail must attribute those contributions explicitly rather than describe the outcome as work of ARCHITECT alone.

For Part 05, the working pattern was:

- **ARCHITECT** — source-derived analysis, modelling decisions, candidate architecture and correction synthesis;
- **independently run DTA / DMV verification instrument/runtime** — adversarial review of candidates against declared baselines, blocking findings and scoped gate outcomes;
- **Engagement owner / user** — supplied or relayed the independent review results into the controlling ARCHITECT conversation, confirmed the gate state used for continuation, and controlled continuation between passes.

DTA/DMV provides verification evidence; it does not silently invent NURA business meaning. Conversely, ARCHITECT must not represent independently verified outcomes as self-validation by one model/runtime.

---

## CAND-NURA-001 — Separate Lifecycle, Readiness and Operational Authorization

**Type:** decision principle / modeling pattern  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
When a business object can legally/business-wise exist, be administratively unready, and still lack permission for specific operations, model these as separate dimensions rather than one overloaded status.

Typical separation:
- lifecycle / legal-business state;
- setup or readiness state;
- operational authorization / permission state.

### Recognition cues
- object is “active” in one sense but still cannot perform certain actions;
- setup checklist exists separately from legal existence;
- users propose statuses such as `Pending Activation`, `Ready`, `Active with Restrictions`;
- cash availability, readiness and authority are being mixed.

### Applicability
Projects, contracts, accounts, suppliers, facilities, regulated operations, onboarding.

### Limits
Do not split dimensions when the business genuinely treats them as one indivisible state.

### Evidence summary
Derived from a case where legal/project existence, administrative setup, funding availability and permission to initiate expenditure were distinct facts.

### Expected behavioral impact
Improves lifecycle modeling and reduces overloaded status enums.

---

## CAND-NURA-002 — Planning Approval Is Not Transaction Authorization

**Type:** decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
Approval of a plan, forecast or anticipated need does not itself authorize the later transaction or commitment unless the governing business rule explicitly says so.

A planned item may pre-populate or streamline a later transaction, but the transaction must still satisfy the controls applicable at execution time.

### Recognition cues
- approved procurement plan is being treated as permission to buy;
- approved forecast is being treated as spending authority;
- users want to bypass all checks because an item was previously planned.

### Applicability
Procurement, budgeting, hiring plans, capital plans, travel plans, project work plans.

### Limits
A governing rule may explicitly make planning approval transaction-authorizing; if so, follow that authority.

### Evidence summary
Derived from separation of research/procurement planning from later financial commitments and transaction-time validation.

### Expected behavioral impact
Prevents plans from silently becoming uncontrolled execution authority.

---

## CAND-NURA-003 — Changed Conditions Trigger Re-evaluation, Not Silent Reversal of Explicit Control

**Type:** decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
When a control decision was explicitly imposed by an authorized person or process, a later change in underlying conditions should normally trigger re-evaluation rather than silently removing or reversing that control.

### Recognition cues
- a restriction was explicitly imposed for a reason;
- a later system event appears to remove the original reason;
- automation is proposed to lift the restriction without a new accountable decision.

### Applicability
Operational restrictions, risk holds, compliance controls, spending restrictions, approvals, exceptions.

### Limits
Automatic reversal is appropriate where the original rule explicitly defines the control as purely condition-derived and no accountable discretion is involved.

### Evidence summary
Derived from a case where delayed funding could motivate a restriction, but later receipt of funding should not silently remove a restriction explicitly imposed by management.

### Expected behavioral impact
Improves accountability and preserves causal auditability.

---

## CAND-NURA-004 — Composite Authorization Preconditions

**Type:** pattern / decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
Do not model authorization as a single “authorizing document” when real authority may depend on several official instruments or conditions.

Represent:
- an authorization requirement;
- the applicable rule for the scenario;
- one or more instruments/evidence items that satisfy it fully or partially.

The requirement may include AND / OR / conditional logic.

### Recognition cues
- one agreement starts preparation but does not yet authorize execution;
- multiple decisions/documents must coexist before activation;
- different scenarios require different evidence combinations;
- one document may be sufficient in one case but only partial in another.

### Applicability
Project activation, regulatory permissions, supplier qualification, onboarding, product release, contract effectiveness.

### Limits
Use the simpler single-instrument model where the domain truly guarantees one stable authorizing instrument.

### Evidence summary
Derived from scenarios where a project could require one decision, one registered agreement, or a composite set of consortium/lead-organization instruments.

### Expected behavioral impact
Avoids brittle one-document authorization models and supports explainable activation prerequisites.

---

## CAND-NURA-005 — Variable Policy as Versioned, Explainable Configuration

**Type:** architecture principle / method component  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
When a recurring business decision varies by controlled context, model it as a versioned policy/rule family rather than scattering hard-coded branches across workflows.

A sufficient policy model should support:
- applicability;
- conditions / evidence;
- outcome;
- effective dates / version;
- authority or source;
- override semantics;
- explainable evaluation result.

### Recognition cues
- same decision differs by programme/type/jurisdiction;
- staff repeatedly choose from the same bounded set of conditions;
- rules change over time but the core process remains stable;
- users need to know why the system allowed or blocked an action.

### Applicability
Eligibility, authorization prerequisites, closure criteria, approval routing, document profiles, programme validation.

### Limits
Fundamental invariants should not be made configurable merely for symmetry. Avoid an unrestricted general-purpose low-code rules platform unless justified.

### Evidence summary
Derived from repeated rule families that varied by project type, funding mechanism, programme and agreement type.

### Expected behavioral impact
Improves adaptability, versioning, explainability and auditability while reducing scattered hard-coded logic.

---

## CAND-NURA-006 — Closure-Blocking Obligations vs Obligations That Outlive Closure

**Type:** modeling pattern  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
A parent business object should not remain administratively open indefinitely merely because some legitimate obligations continue after normal administrative closure.

Classify obligations according to whether they:
- block closure; or
- may continue after closure with their own lifecycle, owner, due date and evidence.

### Recognition cues
- publications, warranties, retention duties or follow-up reporting continue long after financial/administrative close;
- a project/case remains “open” for years despite all core administration being complete;
- all obligations are being treated as one closure gate.

### Applicability
Projects, contracts, programmes, regulatory cases, service engagements.

### Limits
An obligation must remain closure-blocking where applicable authority explicitly requires completion before closure.

### Evidence summary
Derived from a case where long-term dissemination obligations could continue after administrative and financial project closure.

### Material refinement — 2026-09-10
Closure significance may be relationship/context-specific rather than an intrinsic property of the obligation. The same underlying obligation may be permitted to outlive closure of one parent object while still blocking closure of another parent object if unresolved consequences remain under that second object.

Recognition cue: the same obligation is linked to several governed parent objects whose closure criteria differ.

### Expected behavioral impact
Produces cleaner lifecycle semantics, avoids artificially open parent records, and prevents one global `closure-blocking` flag from being misapplied across different parent-object contexts.

---

## CAND-NURA-007 — Business Purpose Is Not Financial Attribution

**Type:** decision principle / data-modeling principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
The object that explains why an expense/activity exists should be modeled separately from the funding source, budget or cost object from which it is financially attributed.

### Recognition cues
- an obligation belongs to one project but is paid from another permitted funding source;
- traceability and accounting attribution are being forced into one relationship;
- a user needs to answer both “what was this for?” and “which funds paid for it?”.

### Applicability
Projects, grants, shared services, internal subsidies, cost reallocation, cross-funded obligations.

### Limits
In domains where governing rules require purpose and funding source to be identical, enforce that constraint without collapsing the concepts.

### Evidence summary
Derived from post-period obligations that remain related to a project while being funded from separately authorized organizational funds.

### Expected behavioral impact
Improves financial correctness and causal traceability.

---

## CAND-NURA-008 — Responsibility Duration Is Not Labor Effort

**Type:** process-analytics heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
Workflow systems may reliably measure how long an object was assigned to or waiting with a person/unit, but elapsed responsibility/custody time must not be represented as actual labor effort unless effort is independently captured.

### Recognition cues
- management asks “how long was the document with each employee?”;
- elapsed time is being converted into employee hours;
- queue/waiting time and active work time are mixed.

### Applicability
SLA analytics, document processing, case management, legal workflows, procurement, application processing.

### Limits
If actual effort is required, use explicit effort capture, time tracking or another defensible source.

### Evidence summary
Derived from a need to measure contribution and bottlenecks across staff without introducing false timesheet precision.

### Expected behavioral impact
Prevents misleading productivity metrics while preserving useful workload/SLA analytics.

---

## CAND-NURA-009 — Administrative Support Workflow Is Not Object Lifecycle

**Type:** modeling pattern  
**Status:** CANDIDATE ONLY  
**Confidence:** high

### Proposed knowledge
Internal administrative support/check activities, external expert evaluation and final business outcome should not automatically become states of the primary business object's lifecycle.

Model separate workflows or related facts where they have independent actors, authority or meaning.

### Recognition cues
- one status enum contains internal review, external review, submission, decision and handover stages;
- an external evaluator or counterparty controls a stage that the system cannot actually observe reliably;
- support activity is optional but represented as mandatory lifecycle state;
- real work permits several valid orderings or repeated cycles of the same coordination activities.

### Applicability
Applications, contracts, cases, submissions, compliance processes, onboarding.

### Limits
A support/review step may legitimately be a lifecycle state where it is mandatory, authoritative and part of the object's own state semantics.

### Evidence summary
Originally derived from separating administrative application checking from scientific peer review, external submission and funding outcome. Further refined by a contract-preparation case where external/manual counterparty coordination was real but not reliably observable by the system and could occur in different/repeated sequences.

### Material refinement — 2026-09-10
An externally performed or manually communicated activity should not become a mandatory lifecycle state merely because it is useful to know that it happened, especially where the system cannot reliably observe its start/end. Prefer action/evidence/timestamps or optional operational progress where appropriate.

### Expected behavioral impact
Reduces overloaded state models, improves authority/observability semantics and avoids false precision in workflow status.

---

## CAND-NURA-010 — Missing Architecture Layer Detection

**Type:** methodology heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high

### Proposed knowledge
If application style, persistence, technology stack, deployment, observability, infrastructure and operations decisions begin to scatter across scope/principles and system-analysis documents, inspect the master architecture structure for a missing Solution Architecture layer before continuing detailed design.

### Recognition cues
- technical implementation decisions have no clear document home;
- scope/principles documents contain detailed platform choices;
- system analysis contains architecture-style, storage and deployment design;
- enterprise architecture is expected to absorb solution-level technical design.

### Applicability
Large architecture documents and multi-part system design specifications.

### Limits
A separate Solution Architecture artifact is not mandatory for small/simple systems where the structure remains coherent without it.

### Evidence summary
Derived from recognizing that solution-level technical material was distributed across several analytical layers because no explicit solution-architecture layer existed.

### Expected behavioral impact
Improves architecture completeness, document-layer clarity and traceability from requirements to implementation design.

---

## CAND-NURA-011 — Material Phase Transition Requires Explicit State Consolidation

**Type:** methodology heuristic / decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high  
**Origin:** NURA ERP Engagement control incident, 2026-09-09

### Proposed knowledge
Completion of a local task sequence is not sufficient evidence of readiness for a material downstream transformation when materially accepted Working State produced during that sequence has not yet been consolidated into the applicable controlled working state.

Before a material downstream phase transition, verify that accepted state has been consolidated, relevant issue/status registers are synchronized, the applicable learning review has occurred, and no blocking inconsistency remains.

### Recognition cues
- a discovery / reconciliation / design question cycle appears complete;
- a rewrite, migration, implementation, data-modeling, publication, release, or other large downstream transformation is about to begin;
- the upstream work produced materially accepted decisions or corrections;
- downstream transformation would be expensive to redo if stale state is used.

### Applicability
Architecture and systems design, policy/procedure development, research synthesis, data-model transitions, implementation handoff, document rewrites, release/migration readiness, and other multi-stage knowledge-work processes.

### Limits
Do not require a heavy checkpoint for trivial task transitions. The control should be proportional to the cost and risk of the downstream transformation.

A textual phase gate is an externalized control state, not a hard technical platform lock.

### Evidence summary
Derived from an Engagement control incident where a substantial semantic question cycle had completed and the next planned action was a full downstream rewrite, but materially accepted decisions still existed only in Working State / chat and had not yet been consolidated into controlled Engagement Memory.

### Expected behavioral impact
Reduces premature movement into expensive downstream work while accepted upstream state is still unconsolidated or stale in the active canonical working state.

---

## CAND-NURA-012 — Significant Accepted Work Can Require Consolidation Without a Phase Transition

**Type:** failure mode / methodology heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** medium  
**Origin:** NURA ERP Engagement control incident, 2026-09-09

### Proposed knowledge
Materially significant accepted Working State can accumulate while work remains inside the same formal phase.

Therefore, phase-transition checks cannot be the sole trigger for Engagement Memory consolidation or Learning & Change Review. A separate observable indication is needed when material accepted state has accumulated since the last consolidation checkpoint.

### Recognition cues
- multiple accepted decisions accumulate within one ongoing phase;
- Open Issues are resolved or materially reclassified without a phase change;
- accepted rules, concepts, relationships, boundaries or terminology are corrected;
- reusable learning is identified during ongoing work;
- important accepted truth would otherwise remain only in chat / Working State.

### Applicability
Long-running analysis, architecture engagements, research and policy work, iterative product design, legal/contract analysis, and other work where one phase can contain many material decisions.

### Limits
Do not force a heavy review after every minor correction. The threshold should remain proportional to materiality and the risk of losing or misapplying accepted state.

### Evidence summary
Derived from the same Engagement control incident: the primary failure occurred because significant accepted design work did not autonomously trigger consolidation; the later planned phase transition merely exposed the gap.

### Expected behavioral impact
Reduces dependence on the model remembering an abstract significant-work rule and reduces loss of accepted state during long same-phase work.

---

## CAND-NURA-013 — Operational Current State Is Not the Same as Formal Approved Snapshot

**Type:** decision principle / modeling pattern  
**Status:** CANDIDATE ONLY  
**Confidence:** high
**Origin:** NURA ERP Engagement Learning & Change Review, 2026-09-10  

### Proposed knowledge
When a working state changes continuously while formal approval occurs periodically, model the current operational state separately from the immutable formally approved snapshot.

The latest approved snapshot may be historically/formally authoritative without being the freshest operational truth.

### Recognition cues
- rolling plan or forecast changes between formal approvals;
- users work from a live operational register while governance signs periodic snapshots;
- `approved`, `effective`, `current` or `consolidated` are being used interchangeably;
- formal approval frequency is lower than operational change frequency.

### Applicability
Procurement plans, operating plans, forecasts, board-approved plans, regulatory submissions, policy baselines, portfolio plans.

### Limits
If formal approval is itself the event that makes every change operationally usable, the two states may legitimately coincide.

### Evidence summary
Derived from a planning model where operationally accepted changes became immediately relevant for monitoring/work, while immutable formally approved versions were created only periodically.

### Expected behavioral impact
Prevents stale formal snapshots from being misrepresented as live operational truth and prevents continuous work from creating unnecessary formal versions.

---

## CAND-NURA-014 — Aggregate Progress Should Be Derived from Item-Level Outcomes When Children Diverge

**Type:** modeling pattern / heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** high
**Origin:** NURA ERP Engagement Learning & Change Review, 2026-09-10  

### Proposed knowledge
When one aggregate object contains child items that may legitimately be at different downstream stages at the same time, detailed progress should live at the child/item/allocation level and aggregate progress should be derived or intentionally coarse.

A single detailed manual status on the parent should not pretend that all children share one stage.

### Recognition cues
- one case/order/request contains many items or lots;
- some children are selected/contracted/delivered while others failed or remain under evaluation;
- users ask for one status although the underlying state is heterogeneous;
- parent status repeatedly becomes ambiguous or misleading.

### Applicability
Procurement cases, orders, shipments, batch processing, portfolios, multi-item service requests, fulfillment systems.

### Limits
A single parent status may still be appropriate where children are required to move atomically or the parent lifecycle intentionally represents only a coarse phase.

### Evidence summary
Derived from a procurement case that could contain many items/lots with simultaneous Evaluation, Contracting, Delivery and Not-Procured outcomes.

### Expected behavioral impact
Improves status truthfulness, analytics and exception handling while reducing overloaded parent lifecycle models.

---

## CAND-NURA-015 — Upstream Planning Change Must Not Silently Rewrite an Existing Downstream Obligation

**Type:** decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high
**Origin:** NURA ERP Engagement Learning & Change Review, 2026-09-10  

### Proposed knowledge
A planning or demand object may remain revisable, but once a downstream contractual, financial or other binding obligation exists, changing the upstream object must trigger the applicable downstream change / amendment / termination / reconciliation path rather than silently rewriting the obligation history.

The existence of an obligation is not necessarily an absolute prohibition on later change; it changes the governance and consequences of that change.

### Recognition cues
- upstream quantity/scope changes after contract or commitment;
- users want to edit the original request as if no downstream obligation exists;
- amendment/termination cost or counterparty consent becomes relevant;
- auditability requires preserving the originally authorized/contracted facts.

### Applicability
Procurement, budgets, resource plans, orders, subscriptions, service requests, reservations, contracts.

### Limits
If the downstream object is explicitly non-binding or designed to inherit upstream edits until a later commitment event, the boundary should be placed at the actual obligation-forming event instead.

### Evidence summary
Derived from a quantity change requested after a supplier contract had already been concluded, where change remained possible only through a controlled procurement/contract path.

### Expected behavioral impact
Preserves causal history and prevents upstream edits from fabricating a false downstream past.

---

## CAND-NURA-016 — Automation May Require Changing the Evidence-Supply Environment, Not Only the Software

**Type:** architecture principle / heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high
**Origin:** NURA ERP Engagement Learning & Change Review, 2026-09-10  

### Proposed knowledge
When useful automation depends on a fact that the system cannot infer and only an external actor knows, architecture should examine whether the surrounding process, interface, policy or contractual obligation should require that actor to provide the fact.

The software should still support fallback handling when the expected evidence/input is absent or late.

### Recognition cues
- automation needs shipment/content/timing details known only by a supplier or partner;
- the system is blamed for not routing/alerting correctly despite missing upstream evidence;
- better automation requires a behavioral/process/contract change outside the application itself;
- failure to provide data must not make real-world events impossible to record.

### Applicability
Supplier portals, logistics, service appointments, partner integrations, compliance submissions, external evidence collection.

### Limits
Do not impose contractual/process obligations where the required information is unavailable to the external actor, disproportionate to collect, or not material enough to justify the burden.

### Evidence summary
Derived from a delivery-notification problem where correct receiver routing depended on supplier-provided shipment contents and timing, which the ERP could not otherwise know.

### Expected behavioral impact
Broadens architecture from application-only design to socio-technical evidence supply while preserving operational resilience through fallback paths.

---


## CAND-NURA-017 — AI-Assisted Extraction Must Not Be the Sole Institutional Source of Truth

**Type:** architecture principle / decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high  
**Origin:** NURA ERP Engagement clarification, 2026-09-11  

### Proposed knowledge
When an organization needs durable multi-year analytics from narrative reports or other unstructured evidence, AI may accelerate extraction, classification and summarization, but the long-term information architecture should not depend on continuing access to a particular AI capability.

Material extracted facts should become structured records with provenance and an applicable confirmation / validation state. AI-generated proposals remain proposals until the governing business process makes them trusted institutional facts.

### Recognition cues
- valuable results exist mainly in PDFs, reports, emails or narrative documents;
- retrospective analytics require repeated manual reading of large document sets;
- AI can extract likely facts but access, model quality or cost may change over time;
- the organization needs defensible institutional reporting rather than one-off summaries.

### Applicability
Research administration, knowledge management, compliance reporting, impact reporting, case management, grant administration and other domains that convert unstructured evidence into durable institutional data.

### Limits
Where the use case is intentionally exploratory and no durable institutional fact is created, formal confirmation may be unnecessary. The required validation level should remain proportional to the consequence of the extracted claim.

### Evidence summary
Derived from a research-administration need to identify meaningful research results across multi-year narrative reports while avoiding long-term dependence on AI availability.

### Expected behavioral impact
Encourages durable structured data capture with provenance, while using AI as an optional accelerator rather than an irreplaceable source of truth.

---


## CAND-NURA-018 — Legal Document Type and Economic Direction Are Independent Architecture Dimensions

**Type:** architecture / domain-modeling principle  
**Status:** CANDIDATE ONLY  
**Confidence:** high  
**Origin:** NURA ERP Engagement clarification, 2026-09-11  

### Proposed knowledge
In ERP and case-management domains, the legal type or name of a contract should not be assumed to determine the economic direction of the relationship or the workflow that originates it.

A contract can be incoming relative to the organization, outgoing, non-monetary, or materially mixed. Financial direction is relative to the modeled organization and can invert across the two parties to the same relationship.

Shared legal-document capabilities can be reused across contract classes, but a common Contract entity does not imply one universal creation workflow. Incoming contracts may originate in grants, legal intake or other funding/revenue processes; outgoing contracts may originate in procurement, project expenditure or service-purchasing processes.

### Limits
Financial direction must not be confused with accounting revenue recognition or expense classification. Exact role ownership remains organization-specific.

---

## CAND-NURA-019 — Architecture Documents Should Be Authored for Downstream Verifiability

**Type:** methodology principle / architecture-authoring method component  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high  
**Origin:** NURA ERP Engagement architecture-to-delivery design, refined 2026-09-16  

### Proposed knowledge
When substantial software architecture will later govern technical specification, incremental delivery, acceptance and conformance verification, human-readable architecture should be authored so that material architectural assertions can be transformed into downstream requirements, implementation obligations, acceptance criteria and conformance rules **without inventing new domain meaning**.

A practical authoring method should preserve:

- human-readable architecture as the source of meaning;
- stable identification of material rules where useful;
- separation of normative rule from rationale, explanation and example;
- explicit subject/object, applicability, required/permitted/prohibited behavior, authority, temporal effect, exception semantics and evidence/provenance where relevant;
- explicit unresolved authority rather than false precision;
- layer discipline so downstream implementation detail is not prematurely embedded;
- a downstream-readiness check before the architecture section is treated as complete.

### Recognition cues
- architecture will be handed to internal/external developers;
- implementation specifications will be generated from the architecture;
- delivery is split across multiple increments/vendors/teams;
- acceptance must demonstrate architecture compliance;
- machine-readable control or automated conformance is planned;
- narrative architecture contains consequential statements that are difficult to translate into objective obligations.

### Applicability
ERP, enterprise systems, regulated systems, outsourced development, long-running solution programmes, contract-based software delivery and other environments where architecture must remain traceable into implementation and acceptance.

### Limits
Not every architectural judgment is mechanically testable or should be written as a pseudo-formal invariant. Narrative context, rationale, strategy and professional judgment may remain human-readable. Downstream verifiability must not force a Part to choose implementation detail owned by a later architecture layer or embed the future control-model DSL into the architecture document.

### Evidence summary
Derived from designing NURA ERP Parts 00–08 as human-readable architecture that must later support Requirements/Rules Catalogue, per-increment Implementation Specifications, Acceptance Scenarios and a machine-readable Architecture Control Model.

### Expected behavioral impact
Reduces semantic loss between architecture and delivery; improves traceability and specification quality; makes later deterministic/automated conformance more feasible; reduces the risk that downstream teams silently make new architecture decisions while claiming merely to implement existing architecture.

### Engagement implementation / artifact evidence

The candidate was operationalized in the NURA Engagement through a controlled authoring standard and related state/control updates:

- **Created** `runtime/ARCHITECTURE_PART_AUTHORING_STANDARD.md` v1.0 to make downstream-verifiable authoring an explicit reusable rule for Parts 04–08 rather than leaving the method only in chat history.
- **Updated** `ENGAGEMENT_MEMORY.md` to v2.1 so the cross-Part rule is part of established Engagement state: human-readable Parts remain the source of architectural meaning; material assertions must be precise enough for later transformation into requirements, implementation obligations, acceptance criteria and conformance rules without inventing new business meaning.
- **Updated** `ENGAGEMENT_CONTROL.md` (v1.8, then corrective v1.9) to make the Authoring Standard and an Architecture-to-Delivery Readiness Check part of the completion gate for Parts 04–08. This prevents a Part from being treated as complete merely because it is narratively polished.
- **Updated** `00_ENGAGEMENT_MANIFEST.md` (v1.2, then merged/corrected v1.3) so the new Authoring Standard is a controlled Engagement artifact, is included in the System State Bundle, and remains available to future chats working on Parts 05–08.
- **Part 05 completion evidence (2026-09-18):** the Data Model was authored through eight scoped modelling passes plus correction passes and independent DTA/DMV gates across identity, relationships, cardinality/optionality, temporal/version semantics, Logical Entity Model, identifiers/attributes/provenance, Reference/Configuration + logical integrity, and Data Dictionary. The final completion package performs cross-Part semantic coverage, end-to-end traceability, unresolved-item disposition and Architecture-to-Delivery Readiness before a full `MODEL PASS` may be claimed.
- **Multi-actor provenance for this evidence:** ARCHITECT produced the modelling candidates and corrections; an independently run DTA/DMV verifier performed adversarial checks and issued scoped findings/gates; the Engagement owner/user relayed and confirmed those gate outcomes before ARCHITECT continued. This evidence therefore must not be read as self-validation by a single model/runtime.

**Why these file changes were needed:** the method affects how multiple future Parts must be authored. Keeping it only in one chat would create a high risk that later chats reproduce the content but lose the downstream-verifiability constraint.

### User disposition

- **Disposition:** `APPROVED_FOR_ROLE_REVIEW`
- **Approved by:** `RF_OWNER_CURRENT_HUMAN`
- **Approved at:** `2026-09-16`
- **Approval evidence:** on 2026-09-16 the user explicitly approved creation of `ARCHITECTURE_PART_AUTHORING_STANDARD.md`, the associated Memory / Control / Manifest changes, and requested that this methodology be captured in Learning Candidates for later Role Updater review.

---

## CAND-NURA-020 — Independently Acceptable End-to-End Increments

**Type:** delivery methodology heuristic / decision principle  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high  
**Origin:** NURA ERP Engagement delivery-planning clarification, 2026-09-14  

### Proposed knowledge
When a complex system is delivered incrementally, decompose work so that each increment ends in a usable end-to-end procedure or coherent capability that can be accepted using the functionality available at that stage. Later increments may depend on earlier technical foundations, but acceptance of an earlier increment should not depend on future functionality that has not yet been delivered.

### Recognition cues
- long programmes are being split by technical layer (database/backend/frontend) rather than usable outcomes;
- acceptance cannot occur until several later phases are complete;
- each new phase retroactively reveals that the prior phase was not actually usable.

### Limits
Technical independence is not required. Shared platform capabilities and prior increments may be prerequisites. The rule concerns independent acceptability and completeness of the delivered business outcome, not absence of dependencies.

### Expected behavioral impact
Supports earlier real-world validation, clearer acceptance boundaries and lower rework risk.


### Engagement implementation / artifact evidence

- The principle was recorded in `ENGAGEMENT_MEMORY.md` as an accepted Architecture-to-Delivery objective: each delivery increment should end in a usable end-to-end procedure/capability whose acceptance does not depend on functionality planned only for future increments.
- `ENGAGEMENT_CONTROL.md` preserves this downstream objective as part of the transition from human-readable Architecture toward later delivery tooling and specifications.
- No final `Delivery / Increment Model` artifact has yet been created; that artifact belongs to later Architecture-to-Delivery work after Parts are sufficiently complete.

**Why these file changes were needed:** the principle changes how future delivery specifications will be decomposed. It therefore had to be preserved before the delivery-model artifacts themselves exist, so later roles do not default to horizontal database/backend/frontend phases that cannot be independently accepted.

### User disposition

- **Disposition:** `APPROVED_FOR_ROLE_REVIEW`
- **Approved by:** `RF_OWNER_CURRENT_HUMAN`
- **Approved at:** `2026-09-14`
- **Approval evidence:** the user explicitly accepted the independently acceptable end-to-end increment principle and the associated Architecture-to-Delivery model during the 2026-09-14 discussion.

---

## CAND-NURA-021 — Machine-Readable Architecture Control Model as a Conformance Interface

**Type:** architecture / delivery-control pattern  
**Status:** CANDIDATE ONLY  
**Confidence:** medium  
**Origin:** NURA ERP Engagement conformance-planning clarification, refined 2026-09-16  

### Proposed knowledge
A machine-readable Architecture Control Model can serve as a controlled interface between human-readable architecture and conformance checking when it formalizes requirements, invariants and constraints while preserving traceability to the governing human-readable source. The control model should not become a second independent architecture.

The model may support several verification modes, including deterministic/formal constraint checking, static code/schema analysis, automated tests, API/integration tests, runtime evidence and business acceptance scenarios. It should preserve explicit non-binary outcomes where evidence is insufficient or a requirement is not statically/formally decidable.

### Recognition cues
- architecture contains state-transition, permission, authority, dependency, data, API or audit invariants;
- multiple implementation artifacts must be checked against the same governed requirements;
- acceptance evidence must remain traceable to architecture version/revision;
- AI-assisted review is desired but must not become the sole source of truth.

### Limits
The control model cannot make inherently contextual or runtime-only requirements statically provable. It requires controlled synchronization/versioning with human-readable architecture. The exact formal language/solver/tool should be selected later based on rule classes and implementation constraints rather than fixed prematurely.

### Expected behavioral impact
Makes architecture conformance more repeatable and automatable while preserving source authority, traceability and epistemic honesty about what can and cannot be proven.


### Engagement implementation / artifact evidence

- `ENGAGEMENT_MEMORY.md` records the Architecture Control Model as an accepted future Architecture-to-Delivery artifact that formalizes requirements, invariants and constraints while preserving traceability to human-readable Parts.
- `00_ENGAGEMENT_MANIFEST.md` includes the Architecture-to-Delivery objective and conformance direction in Engagement scope/state so later tool-design chats can work from the same accepted target.
- `ARCHITECTURE_PART_AUTHORING_STANDARD.md` requires Parts 04–08 to remain precise enough for later machine-readable formalization while prohibiting premature embedding of the future DSL/control representation into the Parts themselves.
- The actual Architecture Control Model schema/DSL has **not** been created in this Engagement phase; only its required role and authoring prerequisites have been established.

**Why these file changes were needed:** a machine-readable control model can only be derived reliably if the source architecture preserves clear normative meaning, identifiers, authority, conditions and exceptions. The current changes prepare the Parts for that later derivation without prematurely fixing the control technology.

### User disposition

- **Disposition:** `APPROVED_FOR_ROLE_REVIEW`
- **Approved by:** `RF_OWNER_CURRENT_HUMAN`
- **Approved at:** `2026-09-14`
- **Approval evidence:** the user explicitly accepted the Architecture Control Model definition, its place inside the Architecture-to-Delivery Layer, and its use as the basis for later conformance checking.

---

## CAND-NURA-022 — Deterministic Conformance Core with Optional AI Assurance

**Type:** architecture / verification-control principle  
**Status:** CANDIDATE ONLY  
**Confidence:** medium  
**Origin:** NURA ERP formal-conformance clarification, 2026-09-16  

### Proposed knowledge
Where architecture requirements can be expressed objectively, conformance should preferentially rely on deterministic/formal/automated mechanisms rather than an AI model deciding compliance from narrative context.

Potential mechanisms include model/state checks, constraint solvers, static analysis, schema/API validation, dependency checks, generated contract tests and runtime assertions. AI may assist with mapping, investigation, explanation, unstructured evidence review or proposal generation, but should not override deterministic violations or be treated as proof merely because it found no problem.

A robust conformance system should distinguish at least:

- proven/verified within the selected deterministic check scope;
- violation;
- not implemented;
- insufficient evidence;
- manual/runtime verification required;
- not formally verifiable by the current control mechanism.

### Recognition cues
- the same architecture rule must be checked repeatedly across releases;
- objective invariants exist (state transitions, permissions, authority, cardinalities, dependencies, API/data contracts);
- AI consistency/reproducibility would be insufficient for the assurance level required;
- proprietary/vendor implementation must still produce auditable evidence.

### Applicability
Architecture conformance, regulated/controlled software delivery, outsourced development, CI/CD quality gates, platform-based implementations and systems requiring repeatable acceptance evidence.

### Limits
Deterministic verification proves only what has been formalized and what the available evidence exposes. Human judgment and runtime/manual evidence remain necessary for contextual requirements. Formal methods must remain proportionate; not every business rule requires theorem proving.

### Evidence summary
Derived from examining whether a future NURA ERP Architecture Control Model should work conceptually like a formal proof/checking system rather than depend on an AI-based reviewer.

### Expected behavioral impact
Improves repeatability, auditability and trust in conformance findings while preserving AI as an optional productivity/assurance layer instead of the verification authority.


### Engagement implementation / artifact evidence

- `ENGAGEMENT_MEMORY.md` v2.1 records the refinement that future conformance should support deterministic/formal verification where architecture statements are objectively formalizable, with AI as an optional supporting assurance/interpretation layer rather than the sole compliance authority.
- `ENGAGEMENT_CONTROL.md` v1.9 preserves this downstream direction while keeping current Parts technology-neutral.
- `00_ENGAGEMENT_MANIFEST.md` v1.3 preserves the Architecture-to-Delivery / conformance objective after the later RF v4.5 manifest merge.
- `ARCHITECTURE_PART_AUTHORING_STANDARD.md` explicitly requires architecture to support both deterministic/formal verification and evidence-based runtime/manual verification without selecting Lean, TLA+, Alloy, Z3, a custom DSL or another concrete engine during Part authoring.

**Why these file changes were needed:** the earlier conformance concept could be read as AI-centric. The refinement prevents future roles from treating probabilistic model judgment as proof where deterministic checks are possible, while also preventing premature commitment to a particular formal-method technology.

### User disposition

- **Disposition:** `APPROVED_FOR_ROLE_REVIEW`
- **Approved by:** `RF_OWNER_CURRENT_HUMAN`
- **Approved at:** `2026-09-16`
- **Approval evidence:** after discussing a Lean-like, non-AI-based control approach, the user approved the subsequent Memory / Control / Manifest / Authoring Standard updates that incorporated deterministic/formal conformance as the preferred core where feasible.

---


## CAND-NURA-023 — Explicit Learning Candidate Approval Trail as Cross-Runtime Engagement Control

**Type:** methodology / learning-governance heuristic  
**Status:** CANDIDATE ONLY  
**Confidence:** medium-high  
**Origin:** NURA ERP multi-chat learning continuity refinement, 2026-09-16  

### Proposed knowledge
In a substantial multi-chat or multi-runtime Engagement, transferable learning should not depend on conversational memory. Maintain one controlled candidate trail that records not only the candidate knowledge but, where material, how it was operationalized in Engagement artifacts, why those artifact changes were made, and the user's explicit disposition.

The process should distinguish:

- candidate discovery / refinement;
- artifact implementation evidence;
- rationale for material artifact changes;
- explicit user disposition;
- absence of disposition (`NOT_REVIEWED`).

A later runtime should continue the same trail rather than reconstruct approval history from chat chronology.

### Recognition cues
- substantial work is intentionally distributed across several chats/runtimes;
- candidate learning influences methods, controls, templates or other durable Engagement artifacts;
- a later role/updater/reviewer must distinguish model-generated ideas from user-approved findings;
- chat history alone is too fragile to serve as the learning/approval system of record.

### Applicability
Long-running architecture, methodology, research, consulting and design Engagements that use multiple runtimes/roles and may later distill transferable professional learning.

### Limits
Do not create a candidate for every editorial change or local fact. The trail records explicit disposition but does not infer it. Candidate approval history does not replace evidence, transferability assessment, confidentiality review or whatever downstream role-governance process is applicable.

### Evidence summary
Derived from the NURA ERP Engagement after accepted methodology changes were spread across multiple controlled artifacts and the user required later chats to preserve the same explicit learning-approval history for eventual Role Updater review.

### Expected behavioral impact
Reduces loss or misattribution of learning across chats, preserves causality between a reusable insight and the artifacts it changed, and gives downstream reviewers a cleaner evidence trail of what the user actually approved.

### Engagement implementation / artifact evidence

- `00_ENGAGEMENT_MANIFEST.md` v1.4 establishes the Learning Candidate approval trail as an Engagement-wide cross-chat control rather than a convention of one conversation.
- `ENGAGEMENT_CONTROL.md` v1.10 adds an explicit cross-chat Learning Candidate Approval Trail section and makes trail currency part of the Part completion gate.
- `ARCHITECTURE_PART_AUTHORING_STANDARD.md` v1.1 adds a Part-completion learning/approval-trail check so Parts 04–08 created in different chats apply the same method.
- `LEARNING_CANDIDATES.md` revision `2026-09-16-r3` makes the candidate/artifact/disposition record continuous across runtimes and preserves `NOT_REVIEWED` when approval is absent.
- Revision `2026-09-16-r4` aligns approved dispositions with RF canonical `APPROVED_FOR_ROLE_REVIEW` and records `approved_by` / `approved_at` metadata required by `_ROLE_LEARNING_EXPORT_TEMPLATE.md`, so approved candidates can be exported without reconstructing approval facts from chat history.
- **Part 05 completion evidence (2026-09-18):** the final Part 05 review explicitly distinguished semantic completion from controlled Engagement completion: `ENGAGEMENT_MEMORY.md`, `ENGAGEMENT_CONTROL.md`, Manifest source-of-truth metadata and this Learning Candidate trail had to be synchronized before a full `MODEL PASS` could be claimed.
- **Multi-runtime / verifier provenance:** Part 05 continuity depended on a three-role loop rather than one assistant acting alone: ARCHITECT authored/revised the model, an independent DTA/DMV runtime/instrument challenged it against declared baselines and produced gate evidence, and the Engagement owner/user carried the accepted review outcome back into the controlling conversation. This directly demonstrates why contributor roles and gate evidence must persist across runtimes.

**Why these file changes were needed:** the prior approval trail existed in the Learning Candidates artifact, but other chats were not yet normatively required to maintain it. Moving the rule into Manifest, Control and the Part Authoring Standard makes it a property of the Engagement workflow and handoff package rather than an accidental behavior of one chat.

### User disposition

- **Disposition:** `APPROVED_FOR_ROLE_REVIEW`
- **Approved by:** `RF_OWNER_CURRENT_HUMAN`
- **Approved at:** `2026-09-16`
- **Approval evidence:** the user explicitly approved making the candidate/artifact/disposition trail mandatory across other NURA ERP chats and approved the associated controlled-file updates on 2026-09-16.

---

# Candidate Register

| ID | Title | Status | User disposition | Permanent ARCHITECT staging |
|---|---|---|---|---|
| CAND-NURA-001 | Separate Lifecycle, Readiness and Operational Authorization | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-002 | Planning Approval Is Not Transaction Authorization | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-003 | Changed Conditions Trigger Re-evaluation, Not Silent Reversal of Explicit Control | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-004 | Composite Authorization Preconditions | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-005 | Variable Policy as Versioned, Explainable Configuration | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-006 | Closure-Blocking Obligations vs Obligations That Outlive Closure | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-007 | Business Purpose Is Not Financial Attribution | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-008 | Responsibility Duration Is Not Labor Effort | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-009 | Administrative Support Workflow Is Not Object Lifecycle | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-010 | Missing Architecture Layer Detection | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-011 | Material Phase Transition Requires Explicit State Consolidation | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-012 | Significant Accepted Work Can Require Consolidation Without a Phase Transition | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-013 | Operational Current State Is Not the Same as Formal Approved Snapshot | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-014 | Aggregate Progress Should Be Derived from Item-Level Outcomes When Children Diverge | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-015 | Upstream Planning Change Must Not Silently Rewrite an Existing Downstream Obligation | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-016 | Automation May Require Changing the Evidence-Supply Environment, Not Only the Software | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-017 | AI-Assisted Extraction Must Not Be the Sole Institutional Source of Truth | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-018 | Legal Document Type and Economic Direction Are Independent Architecture Dimensions | CANDIDATE ONLY | NOT_REVIEWED | NOT TRANSFERRED |
| CAND-NURA-019 | Human-Readable Architecture Should Produce Verifiable Delivery Assertions | CANDIDATE ONLY | APPROVED_FOR_ROLE_REVIEW | NOT TRANSFERRED |
| CAND-NURA-020 | Independently Acceptable End-to-End Increments | CANDIDATE ONLY | APPROVED_FOR_ROLE_REVIEW | NOT TRANSFERRED |
| CAND-NURA-021 | Machine-Readable Architecture Control Model as a Conformance Interface | CANDIDATE ONLY | APPROVED_FOR_ROLE_REVIEW | NOT TRANSFERRED |
| CAND-NURA-022 | Deterministic Conformance Core with Optional AI Assurance | CANDIDATE ONLY | APPROVED_FOR_ROLE_REVIEW | NOT TRANSFERRED |
| CAND-NURA-023 | Explicit Learning Candidate Approval Trail as Cross-Runtime Engagement Control | CANDIDATE ONLY | APPROVED_FOR_ROLE_REVIEW | NOT TRANSFERRED |
---

## Review Rule

After every Learning & Change Review:
1. add every newly identified transferable candidate to this file;
2. update existing candidates when new evidence materially confirms, limits, contradicts or refines them;
3. record material Engagement artifact changes that operationalize a candidate, including what file was created/changed and why;
4. record explicit user disposition when it occurs, without inferring approval from silence or ordinary continuation;
5. keep Engagement-side user approval separate from ARCHITECT Maintainer authorization and canonical EKB promotion;
6. do not label any candidate as validated Expert Memory;
7. record transfer/promotion separately if a governed permanent-ARCHITECT process is later executed;
8. at agreed final handoff, produce an approved-only export for Role Updater review containing the latest versions of candidates explicitly marked `APPROVED_FOR_ROLE_REVIEW`.
9. apply this same trail across all Engagement chats/runtimes using the current controlled sources; do not maintain separate informal approval histories.

