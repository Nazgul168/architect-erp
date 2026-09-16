# Engagement Manifest — NURA ERP Architecture

Engagement ID: ENG-NURA-ERP-001  
RF System ID: architect-nura-erp  
RF System Type: TASK_SPECIFIC_ROLE  
Title / Approved Alias: NURA ERP Architecture  
Status: ACTIVE  
Canonical Store: private GitHub repository `Nazgul168/nura-erp-architecture`  
Runtime Context: dedicated Engagement runtime — VERIFICATION STATUS UNVERIFIED  
Confidentiality: TO_CONFIRM  
Engagement Owner: Project owner / applicable Engagement authority  
Engagement Confidentiality Authority: TO_CONFIRM  
RF Owner / current clean-ROLE AUTH-ROLE: RF_OWNER_CURRENT_HUMAN  
Legacy ARCHITECT Maintainer ID: ARCH-MAINT-001 — same current human owner; no independent clean-ROLE release authority  

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
- automatic promotion of NURA-specific knowledge into clean ARCHITECT or its Expert Memory / EKB.

## 3. ARCHITECT Parent Binding and Runtime Binding

This Engagement is an **ACTIVE task-specific ARCHITECT system** managed under RF v4.5.

The RF migration records the parent relationship that already existed operationally. It does **not** stop or suspend the Engagement while future clean-ROLE validation work is pending.

```yaml
parent_role:
  role_id: architect
  core_repo: Nazgul168/architect
  binding_state: ACTIVE
  bound_release: ARCH-0.2.1-RC5
  bound_revision: 6f843575253c35312d24d03bd6fe9560045b8e95
  binding_origin: LEGACY_OPERATIONAL_BASELINE_IMPORTED_TO_RF
  update_policy: CONTROLLED_UPDATE
  update_authority_ref: RF_OWNER_CURRENT_HUMAN

parent_role_update_authority:
  type: USER
  identity_ref: RF_OWNER_CURRENT_HUMAN

resolved_role_learning:
  enabled: true
  resolved_by: RF_OWNER_CURRENT_HUMAN
  resolution_basis: Preserve existing Engagement learning behavior under clean ARCHITECT policy.
  resolved_at: 2026-09-16

runtime_binding:
  runtime_id: TO_BE_ASSIGNED / VERIFIED
  platform: ChatGPT Project
  execution_profile_id: TO_BE_ASSIGNED / VERIFIED
  observed_project_instructions_id: ARCH-PI-0.2.1-RC5
  project_instructions_verification: UNVERIFIED
  observed_parent_revision: 6f843575253c35312d24d03bd6fe9560045b8e95
  runtime_sync_status: UNKNOWN
  runtime_record: runtime/RUNTIME_DEPLOYMENT_RECORD.md
```

The current parent binding is therefore **operational now**.

Future clean ARCHITECT releases are handled separately by `CONTROLLED_UPDATE`. A future release becomes an update candidate only when it is actually available for adoption; there is no reason to mark the currently working Engagement itself `BLOCKED` while that future release is still being prepared.

Canonical parent-binding changes and ChatGPT runtime synchronization remain separate. A later Role Updater adoption changes the canonical parent binding only after the required human approval; ChatGPT runtime synchronization is then verified separately.

### Canonical RF v4.5 Engagement paths

```yaml
canonical_paths:
  engagement_memory: memory/ENGAGEMENT_MEMORY.md
  learning_candidates: memory/LEARNING_CANDIDATES.md
  role_performance_log: memory/ROLE_PERFORMANCE_LOG.md
  role_change_log: memory/ROLE_CHANGE_LOG.md
  role_learning_exports: memory/role_learning_exports/
  engagement_control: runtime/ENGAGEMENT_CONTROL.md
  runtime_record: runtime/RUNTIME_DEPLOYMENT_RECORD.md
```

Expert Memory / EKB belongs to the bound clean ARCHITECT release. It no longer has an independent Engagement-side floating update policy.

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

## 6. Learning / ROLE Feedback Artifacts

This Engagement has learning enabled.

Canonical Engagement-side candidate staging:

`memory/LEARNING_CANDIDATES.md`

RF lifecycle:

`CANDIDATE → LOCAL_ONLY / REJECTED / RECOMMENDED_FOR_ROLE_REVIEW → explicit human approval → APPROVED_FOR_ROLE_REVIEW → Role Learning Export → EXPORTED_TO_ROLE_UPDATER`

ARCHITECT may create/update candidates, mark them `LOCAL_ONLY`, recommend rejection, or set `RECOMMENDED_FOR_ROLE_REVIEW`. ARCHITECT may **not** self-assign `APPROVED_FOR_ROLE_REVIEW`.

In the current single-user deployment, only the current human owner may explicitly approve a candidate for Role Updater review. Approval means "review this candidate", not "promote this learning".

Additional Engagement-side ROLE feedback artifacts:

- `memory/ROLE_PERFORMANCE_LOG.md` — user feedback about ARCHITECT behavior/performance; not NURA domain truth;
- `memory/ROLE_CHANGE_LOG.md` — clean-role adoption/change events affecting this Engagement; not NURA domain truth;
- `memory/role_learning_exports/` — safe exports containing only candidates that were explicitly `APPROVED_FOR_ROLE_REVIEW`.

Engagement-side candidate staging or export does not itself change clean ARCHITECT Expert Memory / EKB. Clean-role evaluation and change are owned by Role Updater.

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

For checkpoint / delta-reporting purposes, the System State Bundle remains:

- `00_ENGAGEMENT_MANIFEST.md`;
- `runtime/ENGAGEMENT_CONTROL.md`;
- `memory/ENGAGEMENT_MEMORY.md`;
- `memory/LEARNING_CANDIDATES.md`;
- `runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md`;
- pointer to `runtime/RUNTIME_DEPLOYMENT_RECORD.md`.

`ROLE_PERFORMANCE_LOG.md`, `ROLE_CHANGE_LOG.md` and Role Learning Exports are canonical Engagement-side RF artifacts, but they are not automatically checkpoint-bundle members. Reference them in checkpoint evidence only when a material ROLE-state event requires it.

The Runtime Deployment Record owns detailed runtime configuration and synchronization state; the checkpoint bundle stores/reference-points to it rather than duplicating that state.

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
- `LEARNING_CANDIDATES.md` — candidate staging/status only;
- `ROLE_PERFORMANCE_LOG.md` — user feedback about ROLE behavior/performance only;
- `ROLE_CHANGE_LOG.md` — parent-role adoption/change lineage only;
- `ARCHITECT_PROFESSIONAL_BACKGROUND.md` — runtime professional formation/working profile, subordinate to governing ARCHITECT sources;
- `RUNTIME_DEPLOYMENT_RECORD.md` — runtime binding/synchronization evidence only.

### Role-specific authority

Authority arises from the applicable role, not merely from the person occupying it.

- NURA / Engagement business decisions → applicable Engagement / business authority;
- confidentiality / transfer permission → Engagement Confidentiality Authority;
- `APPROVED_FOR_ROLE_REVIEW` → current human owner acting as the applicable Engagement-side approval authority;
- clean ARCHITECT change/release approval → RF Owner / current human AUTH-ROLE;
- clean ARCHITECT change execution → Role Updater.

`ARCH-MAINT-001` is retained only as a legacy/local label for the same current human owner. It does not independently authorize clean-ROLE modification or release.

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

Before anything leaves the Engagement in a Role Learning Export for Role Updater review, de-identify unnecessary:

- personal names;
- internal document names;
- financial figures;
- sensitive institutional details.

Raw identifying/sensitive evidence remains Engagement-side. Export safe summaries or opaque evidence references.

Processes/cases: ASK ENGAGEMENT CONFIDENTIALITY AUTHORITY until explicitly classified.

Permission to transfer out of the Engagement does not authorize clean ARCHITECT promotion/change. `APPROVED_FOR_ROLE_REVIEW` authorizes review only; Role Updater and the RF Owner release process remain required.

## 15. Provenance Mapping

Opaque IDs used in EKB: none yet  
Identifiable mapping location: Engagement-side only  
Access control: private repository / Engagement runtime

## 16. Open Governance / Migration Issues

- Confirm confidentiality classification.
- Confirm Engagement Confidentiality Authority.
- Complete runtime/source verification where current values remain UNVERIFIED.
- Continue normal NURA ERP architecture work with the current active parent binding.
- When a newer clean ARCHITECT release becomes available for adoption, handle it as a separate `CONTROLLED_UPDATE` decision through Role Updater.
- After canonical parent adoption, synchronize the ChatGPT runtime and verify the active Project Instructions/content separately.
- Configure or verify checkpoint-tag protection for `nura-checkpoint/*` if repository controls permit it.
