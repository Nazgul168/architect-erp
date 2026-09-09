# ENGAGEMENT_CONTROL.md

- **ENGAGEMENT_ID:** `ENG-NURA-ERP-001`
- **CONTROL_VERSION:** `1.0`
- **CONTROL_STATUS:** ACTIVE
- **LAST_UPDATED:** `2026-09-09`

## 1. Purpose

This file is the canonical Engagement-side control artifact for:

1. **consolidation state after materially significant accepted work**; and
2. **readiness for material phase transitions**.

It externalizes control state so that ARCHITECT does not rely only on conversational continuity or on remembering a general rule at the correct moment.

This is a textual control artifact, not a hard technical platform lock. ARCHITECT must read and apply it when relevant.

This file does not replace the Learning Protocol or Engagement Memory. It supplements them with observable control state.

---

## 2. Claim-Relative Authority

`ENGAGEMENT_CONTROL.md` is authoritative within this Engagement for:

- `CURRENT_PHASE`;
- `NEXT_PHASE`;
- consolidation-control state;
- transition-readiness state;
- recorded verification evidence for those states.

It is **not** authoritative for NURA business truth or architectural decisions. Established Engagement knowledge belongs in `memory/ENGAGEMENT_MEMORY.md`, subject to the applicable Engagement authority hierarchy.

---

## 3. Current Control State

### Phase State

- **CURRENT_PHASE:** Semantic Reconciliation / Question Cycle Complete — Consolidation Pending
- **NEXT_PHASE:** Full Rewrite / Synchronization of Parts 00–03
- **NEXT_PHASE_GATE:** `NOT_READY`

### Consolidation State

- **LAST_CONSOLIDATION_CHECKPOINT:** `ENGAGEMENT_MEMORY.md v1.3` — 2026-09-09
- **CONSOLIDATION_STATE:** `DUE`
- **SIGNIFICANT_ACCEPTED_WORK_SINCE_CHECKPOINT:** `YES`

Reason: a materially significant design block occurred after the last consolidated Engagement Memory baseline and introduced accepted / established decisions that must be reviewed and consolidated before the rewrite.

If the exact canonical Git revision of the last checkpoint is later verified, record it in the Verification Evidence section without changing the semantic state above.

---

## 4. Consolidation Trigger

Phase-transition control **supplements, but does not replace**, applicable Learning & Change Review / Engagement Memory consolidation triggers after materially significant accepted work.

Set:

`CONSOLIDATION_STATE: DUE`

and

`SIGNIFICANT_ACCEPTED_WORK_SINCE_CHECKPOINT: YES`

when materially significant accepted / established Working State has accumulated after the last consolidation checkpoint.

### Trigger examples

Consolidation normally becomes `DUE` when one or more of the following materially occurs:

- a new architectural or business-model decision is accepted / established;
- an Open Issue is resolved, reopened, split, merged, or materially reclassified;
- an established concept, lifecycle, rule, boundary, authority, relationship, or terminology is corrected;
- an earlier decision is rejected or superseded;
- a material cross-Part dependency is created or changed;
- a material design defect is identified and its accepted correction is established;
- materially reusable learning is identified;
- an existing transferable candidate is materially refined by new evidence;
- a significant block of accepted Working State would otherwise remain only in chat / Working State.

A phase transition is **not required** for consolidation to become `DUE`.

### Required behavior while DUE

When `CONSOLIDATION_STATE = DUE`, ARCHITECT must:

1. initiate the applicable Learning & Change Review at the next reasonable checkpoint;
2. consolidate accepted / established Engagement knowledge into `memory/ENGAGEMENT_MEMORY.md`;
3. update `memory/LEARNING_CANDIDATES.md` where the review identifies new or materially refined candidates;
4. perform the required full-file consistency check when Engagement Memory was materially patched;
5. update this control artifact.

If the runtime has no verified canonical write path, it must not claim that these files were written. It must instead provide the proposed updated artifacts / patches and treat consolidation as incomplete until canonical persistence is confirmed.

### Returning to CURRENT

`CONSOLIDATION_STATE` may return to `CURRENT` only when the applicable review/consolidation is complete and the resulting controlled artifacts are canonically persisted and available to the active runtime as required.

---

## 5. Transition Rule

Completion of a local conversational plan or task sequence does **not** by itself establish readiness for the next material phase.

ARCHITECT must not recommend, declare ready for, or begin the `NEXT_PHASE` while:

- `NEXT_PHASE_GATE = NOT_READY`; or
- `CONSOLIDATION_STATE = DUE`.

Before changing `NEXT_PHASE_GATE` to `READY`, ARCHITECT must perform a **separate verification pass** against every applicable exit criterion below.

If any mandatory criterion is not satisfied or cannot be verified, the gate remains `NOT_READY`.

---

## 6. Exit Criteria — Ready for Full Rewrite / Synchronization of Parts 00–03

- [ ] Current reconciliation / question cycle is complete: all material items are classified as `RESOLVED`, `OPEN`, or explicitly `DEFERRED`.
- [ ] Learning & Change Review has been completed for the final significant design block.
- [ ] All accepted / established decisions from Working State have been consolidated into the current `memory/ENGAGEMENT_MEMORY.md`.
- [ ] The Open Issues / Conflicts register in Engagement Memory is synchronized with the latest accepted decisions.
- [ ] `memory/LEARNING_CANDIDATES.md` has been updated for all newly identified or materially refined transferable candidates, where applicable.
- [ ] Full-file consistency check of the updated Engagement Memory has been completed and no unresolved internal contradiction blocks the rewrite.
- [ ] Current Solution State / Readiness in Engagement Memory reflects the latest accepted architecture state.
- [ ] No unresolved ambiguity or conflict materially blocks the rewrite of Parts 00–03.
- [ ] Current canonical Engagement artifacts required for the rewrite have been persisted in the Engagement repository.
- [ ] Runtime-visible Project Sources have been verified against the intended canonical versions / revisions of the required Engagement artifacts.

---

## 7. Verification Evidence

Do not mark the transition gate `READY` merely because the checklist appears complete. Record enough evidence to make the readiness assertion inspectable.

### Gate Verification

- **GATE_VERIFIED_AT:** `NOT_VERIFIED`
- **GATE_VERIFIED_BY:** `NOT_VERIFIED`
- **CONTROL_REVISION / COMMIT:** `TO_RECORD_AFTER_CANONICAL_PERSISTENCE`
- **VERIFICATION_RESULT:** `NOT_READY`
- **VERIFICATION_EVIDENCE:** `PENDING`

### Artifact / Revision Pointers

| Artifact | Canonical pointer / revision | Runtime-visible pointer / revision | Sync status |
|---|---|---|---|
| `00_ENGAGEMENT_MANIFEST.md` | TO_RECORD | TO_VERIFY | UNVERIFIED |
| `runtime/ENGAGEMENT_CONTROL.md` | TO_RECORD | TO_VERIFY | UNVERIFIED |
| `memory/ENGAGEMENT_MEMORY.md` | v1.3 baseline; exact Git revision TO_RECORD | TO_VERIFY | STALE / CONSOLIDATION DUE |
| `memory/LEARNING_CANDIDATES.md` | TO_RECORD | TO_VERIFY | UNVERIFIED |
| `runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md` | TO_RECORD | TO_VERIFY | UNVERIFIED |
| Parts 00–03 current source versions | TO_RECORD | TO_VERIFY | UNVERIFIED |

### Runtime-Source Synchronization Semantics

`VERIFIED` means ARCHITECT can identify:

1. the intended canonical artifact/version/revision;
2. the version/revision visible to the active runtime; and
3. the basis for concluding that the runtime-visible artifact matches the intended canonical state.

A vague assertion such as “the latest file seems to be uploaded” is not sufficient.

Exact file hashes are optional unless needed; a reliable version, Git commit, artifact revision, or other inspectable pointer is sufficient.

---

## 8. Control State Changes

`CONSOLIDATION_STATE` and `NEXT_PHASE_GATE` are related but independent controls. They must not be collapsed into one state transition.

### 8.1 Consolidation State Change

When the consolidation requirements in Section 4 are satisfied:

- set `CONSOLIDATION_STATE: CURRENT`;
- set `SIGNIFICANT_ACCEPTED_WORK_SINCE_CHECKPOINT: NO`;
- update `LAST_CONSOLIDATION_CHECKPOINT`;
- record the relevant consolidation evidence / artifact revisions.

This state change does **not** imply that the next material phase is ready.

A valid intermediate state is:

`CONSOLIDATION_STATE: CURRENT`

with

`NEXT_PHASE_GATE: NOT_READY`

when consolidation is complete but one or more phase-transition exit criteria remain unsatisfied.

### 8.2 Phase Transition Gate Change

Only when all applicable phase-transition exit criteria in Section 6 also pass and the verification evidence in Section 7 is recorded:

- set `NEXT_PHASE_GATE: READY`;
- record `GATE_VERIFIED_AT`, `GATE_VERIFIED_BY`, `VERIFICATION_RESULT`, and evidence pointers.

No Maintainer approval is required merely to mark an ordinary Engagement phase transition `READY` when the applicable evidence passes.

Authority for NURA business decisions, confidentiality decisions, and permanent ARCHITECT changes remains role-specific and is not created by this gate.

---

## 9. Actual Phase Start

`READY` means the next phase **may begin**. It does not mean the next phase has already begun.

When work on the `NEXT_PHASE` actually starts, updating this control state is one of the **first required control actions** of that phase.

Immediately:

1. move the former `NEXT_PHASE` into `CURRENT_PHASE`;
2. define the next material `NEXT_PHASE`;
3. set the new `NEXT_PHASE_GATE: NOT_READY`;
4. define phase-appropriate exit criteria for the next transition;
5. preserve the previous gate verification evidence in Git history / prior revision.

Do not allow the runtime to continue materially in the new phase while this file still claims that the previous phase is current.

---

## 10. Current Expected Sequence

For the current NURA ERP state:

**Significant design work completed**
→ **Learning & Change Review**
→ **Engagement Memory consolidation**
→ **Learning Candidates update where applicable**
→ **full-file Memory consistency check**
→ **canonical persistence**
→ **runtime-source synchronization verification**
→ **transition gate verification**
→ **Full Rewrite / Synchronization of Parts 00–03**
→ **cross-Part V&V**

---

## 11. Persistence / Runtime Truth

Canonical persistence is determined by the canonical Engagement repository and its version history.

The active runtime must not claim that it performed a canonical write unless that write path is verified.

If the runtime identifies that this control file itself is stale but cannot write it canonically, it must:

- state the required control-state change;
- provide the proposed updated file / patch;
- behave conservatively according to the stricter state until persistence is confirmed.

This file does not override ARCHITECT Project Instructions, Cognitive Core, governing System Protocols, or the Engagement authority hierarchy.
