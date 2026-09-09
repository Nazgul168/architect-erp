# LEARNING_CANDIDATES.md

Durable Engagement-side staging for transferable learning identified during NURA ERP work.

## Maintenance Rule

After each Learning & Change Review:

- add all newly identified transferable candidates;
- update existing candidates if new evidence materially changes them;
- preserve candidate status and provenance;
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

### Expected behavioral impact
Produces cleaner lifecycle semantics and avoids artificially open parent records.

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
- an external evaluator controls a stage that the system cannot actually observe;
- support activity is optional but represented as mandatory lifecycle state.

### Applicability
Applications, contracts, cases, submissions, compliance processes, onboarding.

### Limits
A support/review step may legitimately be a lifecycle state where it is mandatory, authoritative and part of the object's own state semantics.

### Evidence summary
Derived from separating administrative application checking from scientific peer review, external submission and funding outcome.

### Expected behavioral impact
Reduces overloaded state models and improves authority semantics.

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

# Candidate Register

| ID | Title | Status | Permanent ARCHITECT staging |
|---|---|---|---|
| CAND-NURA-001 | Separate Lifecycle, Readiness and Operational Authorization | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-002 | Planning Approval Is Not Transaction Authorization | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-003 | Changed Conditions Trigger Re-evaluation, Not Silent Reversal of Explicit Control | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-004 | Composite Authorization Preconditions | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-005 | Variable Policy as Versioned, Explainable Configuration | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-006 | Closure-Blocking Obligations vs Obligations That Outlive Closure | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-007 | Business Purpose Is Not Financial Attribution | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-008 | Responsibility Duration Is Not Labor Effort | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-009 | Administrative Support Workflow Is Not Object Lifecycle | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-010 | Missing Architecture Layer Detection | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-011 | Material Phase Transition Requires Explicit State Consolidation | CANDIDATE ONLY | NOT TRANSFERRED |
| CAND-NURA-012 | Significant Accepted Work Can Require Consolidation Without a Phase Transition | CANDIDATE ONLY | NOT TRANSFERRED |

---

## Review Rule

After every Learning & Change Review:
1. add every newly identified transferable candidate to this file;
2. update existing candidates when new evidence materially confirms, limits, contradicts or refines them;
3. do not label any candidate as validated Expert Memory;
4. record transfer/promotion separately if a governed permanent-ARCHITECT process is later executed.

