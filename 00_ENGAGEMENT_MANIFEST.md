\
# Engagement Manifest — NURA ERP Architecture

Engagement ID: ENG-NURA-ERP-001  
Title / Approved Alias: NURA ERP Architecture  
Status: ACTIVE  
Canonical Store: private GitHub repository `nura-erp-architecture`  
Runtime Context: dedicated Engagement runtime — VERIFICATION STATUS UNVERIFIED  
Confidentiality: TO_CONFIRM  
Engagement Owner: Project owner / applicable Engagement authority  
Engagement Confidentiality Authority: TO_CONFIRM  
ARCHITECT Maintainer ID: ARCH-MAINT-001  

## 1. Purpose

Develop and maintain the conceptual, logical and governing architecture for the NURA ERP system, preserving the history of architectural decisions and enabling continued work with ARCHITECT across sessions and runtimes.

## 2. Scope

### In scope

- NURA ERP Architecture documents and Parts;
- architectural concepts, requirements and decisions;
- process/system/data/solution architecture reasoning relevant to the ERP;
- current and historical design alternatives;
- source documents used to support the architecture;
- QA/chat history needed to reconstruct how the architecture evolved;
- Engagement-specific lessons and unresolved issues;
- Engagement-side learning candidates;
- current Engagement phase / consolidation / checkpoint / transition-readiness control.

### Out of scope

- permanent ARCHITECT Expert Memory itself;
- raw material from unrelated Engagements;
- automatic promotion of NURA-specific knowledge into permanent ARCHITECT candidate storage or global EKB.

## 3. ARCHITECT Runtime Binding

RUNTIME_ID: TO_BE_ASSIGNED / VERIFIED  
ARCHITECT_RELEASE_ID: ARCH-0.2.1-RC5  
PROJECT_INSTRUCTIONS_ID: ARCH-PI-0.2.1-RC5  
PI_CONTENT_VERIFICATION: UNVERIFIED  
GOVERNING_PACK_REVISION: 6f843575253c35312d24d03bd6fe9560045b8e95  
EXECUTION_PROFILE_ID: TO_BE_ASSIGNED / VERIFIED  
EKB_UPDATE_POLICY: CONTROLLED_UPDATE  
EKB_REVISION_CURRENT: 6f843575253c35312d24d03bd6fe9560045b8e95  
RUNTIME_DEPLOYMENT_RECORD_ID: TO_BE_ASSIGNED / VERIFIED  
RUNTIME_STATE: UNVERIFIED  
ISOLATION_REQUIRED: YES  
ISOLATION_STATUS: UNVERIFIED  

Where a canonical Runtime Deployment Record exists, it owns the detailed runtime configuration. Engagement checkpoint state should reference that record rather than duplicating independently maintained runtime configuration.

## 4. Canonical Engagement Memory

`memory/ENGAGEMENT_MEMORY.md`

This is the controlled Engagement-specific memory for current established NURA ERP knowledge.

It contains accepted/reconciled decisions, rejected/superseded decisions, unresolved issues, material constraints, current solution state and cross-Part dependencies.

Historical QA / Bootstrap materials remain evidence and lineage sources; they are not the default current working truth.

Engagement Memory is authoritative for established Engagement state **within the applicable claim-relative authority hierarchy**. It does not override higher-authority legal, institutional, policy, System-of-Record, or other applicable sources.

## 5. Runtime Professional Profile

`runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md`

Status: **PROVISIONAL RUNTIME PROFESSIONAL PROFILE**

This profile defines the professional formation, depth of expertise and working posture ARCHITECT applies within this Engagement.

It is subordinate to Project Instructions, Cognitive Core and governing System Protocols.

It does not constitute permanent Expert Memory / EKB promotion and does not independently create governance authority or permissions.

## 6. Learning Candidate Staging

Canonical Engagement-side candidate staging:

`memory/LEARNING_CANDIDATES.md`

After each Learning & Change Review, newly identified or materially updated transferable learning candidates must be recorded in this file.

Engagement-side candidate staging does not constitute transfer to permanent ARCHITECT candidate storage or promotion to Expert Memory / EKB.

Candidate staging is not authoritative for established NURA ERP business truth merely because an item appears there.

## 7. Engagement Control State

Canonical Engagement-side control artifact:

`runtime/ENGAGEMENT_CONTROL.md`

`ENGAGEMENT_CONTROL.md` is authoritative within this Engagement specifically for:

- current phase;
- next planned material phase;
- consolidation-control state;
- System State Checkpoint identity / status;
- reporting-window baseline;
- uncheckpointed-material-delta state;
- transition-readiness / gate state;
- verification evidence for those control states.

This authority is limited to control/reporting state.

It does not make Control authoritative for NURA business truth.

### Consolidation / Transition Relationship

Phase-transition control supplements, but does not replace, applicable Learning & Change Review and Engagement Memory consolidation triggers after material accepted work.

A material phase transition is therefore a downstream backstop, not the sole trigger for learning / memory maintenance.

### Consolidation Pressure Sensor

NURA uses a **Consolidation Pressure Sensor based on observable proxies**.

It does not claim to measure actual model context-window occupancy.

The sensor uses:

- approximate volume proxy;
- semantic / decision pressure;
- context-degradation symptoms.

The operative sensor rules are maintained in `runtime/ENGAGEMENT_CONTROL.md`.

## 8. System State Checkpoint

### 8.1 System State Bundle

For checkpoint / delta-reporting purposes, the System State Bundle consists of:

- `00_ENGAGEMENT_MANIFEST.md`;
- `runtime/ENGAGEMENT_CONTROL.md`;
- `memory/ENGAGEMENT_MEMORY.md`;
- `memory/LEARNING_CANDIDATES.md`;
- `runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md`;
- pointer to the applicable Runtime Deployment Record where available.

If no formal Runtime Deployment Record exists, verified runtime-binding fields may be used as fallback evidence.

### 8.2 Architecture Outputs

Architecture Parts and other outputs are not System State Bundle members.

However, checkpoint evidence must preserve the relevant architecture-output revision/pointer set used by ARCHITECT at that checkpoint.

This enables later reconstruction of which Part versions were current or stale at the checkpoint baseline.

### 8.3 Checkpoint Identity

Each System State Checkpoint uses an independent logical ID, e.g.:

`CP-NURA-001`

Preferred Git reference:

`refs/tags/nura-checkpoint/CP-NURA-001`

The checkpoint Control must not contain the hash of the same Git commit that contains that Control revision.

### 8.4 Checkpoint Finalization

A checkpoint is not operationally verified merely because its candidate commit exists.

Verification requires successful completion of the applicable finalization sequence defined in `runtime/ENGAGEMENT_CONTROL.md`, including:

- canonical commit;
- checkpoint Git reference creation/push;
- resolution of that reference to the intended commit;
- resolved commit-hash evidence recorded non-self-referentially;
- required runtime/source verification;
- checkpoint-integrity verification.

The finalization record may be written in a later administrative Control revision because that later record points backward to the already-existing checkpoint commit and therefore does not create self-reference.

### 8.5 Checkpoint Git Reference Integrity

A Git tag is not assumed immutable merely because it exists.

Preferred repository control is protection of the checkpoint-tag namespace, e.g.:

`nura-checkpoint/*`

against unauthorized update/deletion.

The checkpoint's resolved commit hash must be preserved as verification evidence in a non-self-referential finalization record.

If the tag later resolves to a different commit than the recorded hash, treat this as a checkpoint-integrity failure.

### 8.6 Bootstrap Safeguard

When the checkpoint mechanism is introduced while unreviewed material delta already exists:

- do not establish the first checkpoint from the latest edited files;
- preserve the unreviewed delta;
- review from the earliest reliably identifiable pre-delta baseline;
- if exact historical coherent baseline is unavailable, record it as `UNVERIFIED`;
- establish the first verified checkpoint only after catch-up review, system-state update, canonical persistence and runtime/source verification.

For the current NURA state, the conservative bootstrap semantic baseline is `ENGAGEMENT_MEMORY.md v1.3`, while exact coherent bundle revision remains to be verified.

## 9. Delta Reporting

Learning & Change Review reports material delta since the last verified System State Checkpoint, or from the explicit conservative bootstrap baseline while the first checkpoint is pending.

Previously checkpointed unchanged Engagement state must not be represented as new work or new learning merely because it is mentioned again.

Earlier state may be included when it:

- changed;
- was corrected, superseded or rejected;
- became conflicted;
- gained materially new evidence;
- created a new dependency;
- is required to explain current delta.

Modification of one System State Bundle file does not by itself advance the reporting baseline.

Administrative / formatting edits must not reset the reporting window while uncheckpointed material delta remains.

## 10. Claim-Relative Authority Hierarchy

For current Engagement truth, use the following claim-relative working order:

1. applicable authoritative NURA / NU / legal / institutional sources for the claim in question;
2. current accepted architecture Parts together with controlled Engagement Memory;
3. verified supporting evidence;
4. historical QA / Bootstrap materials for rationale, lineage, rejected/superseded alternatives and unresolved conflicts.

Do not infer authority merely from file age, chat order, document format, or the identity of the current human interactor.

### Artifact-specific authority

- `ENGAGEMENT_MEMORY.md` — established Engagement knowledge, subject to the hierarchy above;
- `ENGAGEMENT_CONTROL.md` — phase, consolidation, checkpoint, delta-reporting and transition-readiness state;
- `LEARNING_CANDIDATES.md` — candidate staging status only;
- `ARCHITECT_PROFESSIONAL_BACKGROUND.md` — runtime professional formation/working profile, subordinate to governing ARCHITECT sources.

### Role-specific authority

Authority arises from the applicable role, not merely from the person occupying it.

- NURA / Engagement business decisions → applicable Engagement / business authority;
- confidentiality / transfer permission → Engagement Confidentiality Authority;
- permanent ARCHITECT governance, permanent EKB promotion and governing-behavior changes → ARCHITECT Maintainer under the applicable permanent governance process.

One person may occupy more than one role, but the authority basis remains role-specific.

### Part ↔ Memory conflicts

If an accepted / reconciled correction is explicitly recorded in Engagement Memory as not yet propagated to a Part, that Part is treated as stale for that specific claim until synchronization.

In other Part ↔ Engagement Memory conflicts, do not silently prefer either source. Record the discrepancy and reconcile it explicitly.

### Conflicting authoritative sources

If authoritative sources conflict, do not silently blend them.

Resolve the claim, scope, jurisdiction, precedence, effective date, version or System-of-Record basis where possible; otherwise escalate the unresolved conflict.

## 11. Engagement Context

- `context/chat_qa/`
- `context/source_documents/`
- `outputs/architecture/`

Historical QA / Bootstrap artifacts are retained for provenance, rationale, disputed decisions and reconstruction of solution lineage.

They do not need to remain continuously loaded into the active runtime after their material current state has been consolidated into controlled Engagement Memory.

## 12. Runtime Isolation

Required:

- no raw context from unrelated Engagements;
- Project-only / equivalent context isolation where available;
- connector/source access limited to what the Engagement requires.

Isolation verification status: UNVERIFIED

## 13. Platform / Organizational Data Handling

Required for this Engagement: TO_CONFIRM  
PLATFORM_DATA_HANDLING_STATUS: UNVERIFIED  
ORGANIZATION_POLICY_STATUS: UNVERIFIED  

Context isolation does not by itself establish organizational approval for confidential data.

## 14. Confidentiality / Transfer Rules

Before anything leaves the Engagement for permanent ARCHITECT candidate/EKB storage, de-identify unnecessary:

- personal names;
- internal document names;
- financial figures;
- sensitive institutional details.

Processes/cases: ASK ENGAGEMENT CONFIDENTIALITY AUTHORITY until explicitly classified.

Permission to transfer out of the Engagement does not authorize permanent EKB promotion.

## 15. Provenance Mapping

Opaque IDs used in EKB: none yet  
Identifiable mapping location: Engagement-side only  
Access control: private repository / Engagement runtime

## 16. Open Governance Issues

- Confirm confidentiality classification.
- Confirm Engagement Confidentiality Authority.
- Complete runtime/source verification where current values remain UNVERIFIED.
- Establish / verify Runtime Deployment Record if adopted as the canonical runtime-binding owner.
- Configure or verify checkpoint-tag protection for `nura-checkpoint/*` if repository controls permit it.
