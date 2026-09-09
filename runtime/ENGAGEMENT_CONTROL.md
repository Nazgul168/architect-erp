\
# ENGAGEMENT_CONTROL.md

- **ENGAGEMENT_ID:** `ENG-NURA-ERP-001`
- **CONTROL_VERSION:** `1.1`
- **CONTROL_STATUS:** ACTIVE
- **LAST_UPDATED:** `2026-09-10`

## 1. Purpose

This file is the canonical Engagement-side control artifact for:

1. consolidation pressure and consolidation state after material Engagement work;
2. System State Checkpoint / delta-reporting state;
3. readiness for material phase transitions;
4. verification evidence for those control states.

It externalizes control state so that ARCHITECT does not rely only on conversational continuity or on remembering a general rule at the correct moment.

This is a textual control artifact, not a hard technical platform lock.

It does not replace the Learning Protocol, Engagement Memory, applicable Engagement authority, or permanent ARCHITECT governance.

---

## 2. Claim-Relative Authority

`ENGAGEMENT_CONTROL.md` is authoritative within this Engagement for:

- `CURRENT_PHASE`;
- `NEXT_PHASE`;
- consolidation-control state;
- System State Checkpoint identity / status;
- current system-update state;
- reporting-window baseline;
- uncheckpointed-material-delta state;
- transition-readiness state;
- recorded verification evidence for those states.

It is **not** authoritative for NURA business truth or architectural decisions.

Established Engagement knowledge belongs in `memory/ENGAGEMENT_MEMORY.md`, subject to the applicable claim-relative Engagement authority hierarchy.

---

## 3. Current Control State

### 3.1 Phase State

- **CURRENT_PHASE:** Semantic Reconciliation / Question Cycle Complete — Consolidation Pending
- **NEXT_PHASE:** Full Rewrite / Synchronization of Parts 00–03
- **NEXT_PHASE_GATE:** `NOT_READY`

### 3.2 System State Checkpoint / Bootstrap State

- **LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID:** `NONE — BOOTSTRAP PENDING`
- **LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_GIT_REF:** `NONE`
- **LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_COMMIT:** `NONE`
- **SYSTEM_STATE_CHECKPOINT_STATUS:** `BOOTSTRAP_PENDING`
- **BOOTSTRAP_REVIEW_FROM:** `ENGAGEMENT_MEMORY.md v1.3`, 2026-09-09
- **BOOTSTRAP_BASELINE_BUNDLE_REVISION:** `UNVERIFIED`
- **PENDING_CHECKPOINT_ID:** `CP-NURA-001`
- **PENDING_CHECKPOINT_GIT_REF:** `refs/tags/nura-checkpoint/CP-NURA-001`
- **CHECKPOINT_FINALIZATION_STATE:** `NOT_STARTED`

Current NURA work already contains unreviewed material delta after the v1.3 Memory baseline.

Therefore no new System State Checkpoint may be established until the catch-up Learning & Change Review and the required system-state update cycle are complete.

### 3.3 Delta / Consolidation State

- **CURRENT_SYSTEM_UPDATE:** `IN_PROGRESS`
- **REPORTING_WINDOW_START:** `BOOTSTRAP_REVIEW_FROM`
- **UNCHECKPOINTED_MATERIAL_DELTA:** `YES`
- **UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK:** `YES`
- **CONSOLIDATION_STATE:** `DUE`

Reason: materially significant accepted design work accumulated after the current conservative bootstrap baseline and has not yet been consolidated into a completed verified system-state update.

### 3.4 Required State Invariant

`UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES`

implies both:

`UNCHECKPOINTED_MATERIAL_DELTA = YES`

and:

`CONSOLIDATION_STATE = DUE`

`UNCHECKPOINTED_MATERIAL_DELTA = YES` does **not** by itself imply `CONSOLIDATION_STATE = DUE`.

This distinction is intentional:

- uncheckpointed material delta may exist but remain below the consolidation threshold;
- unconsolidated significant accepted work means the semantic threshold has already been reached.

---

## 4. System State Bundle

For System State Checkpoint / delta-reporting purposes, the NURA ERP System State Bundle consists of:

- `00_ENGAGEMENT_MANIFEST.md`;
- `runtime/ENGAGEMENT_CONTROL.md`;
- `memory/ENGAGEMENT_MEMORY.md`;
- `memory/LEARNING_CANDIDATES.md`;
- `runtime/ARCHITECT_PROFESSIONAL_BACKGROUND.md`;
- pointer to the applicable Runtime Deployment Record where available.

If a formal Runtime Deployment Record is not yet available, the currently verified runtime-binding fields may be used as fallback evidence without creating a second independently maintained source of truth.

### Architecture Outputs

Parts 00–03 and other architecture outputs are **not** System State Bundle members.

Their canonical/runtime-visible revisions remain checkpoint dependency evidence so that the architecture-output baseline associated with a checkpoint can later be reconstructed.

---

## 5. System State Checkpoint Semantics

A System State Checkpoint is the latest **completed, coherent, canonically persisted and verified** baseline of controlled Engagement / professional state.

It is not:

- the most recent modification time of any one file;
- a Control-only edit;
- a partially completed persistence cycle;
- a newly created commit that has not completed checkpoint finalization.

### 5.1 Checkpoint Identity

Each checkpoint has an independent logical ID:

`CP-NURA-001`, `CP-NURA-002`, ...

Preferred Git reference:

`refs/tags/nura-checkpoint/CP-NURA-00X`

The checkpoint ID is independent of the Git commit hash.

### 5.2 No Git Self-Reference

Do not place the hash of the same Git commit inside the Control revision that creates that commit.

The resolved checkpoint commit hash is recorded only **after** the checkpoint commit already exists.

### 5.3 Checkpoint Git Reference Stability

Preferred repository control:

- use an annotated checkpoint tag;
- protect the tag pattern `nura-checkpoint/*` against update/deletion where repository controls allow it.

A Git tag is not assumed to be technically immutable unless repository controls establish that property.

Therefore checkpoint verification also records the **resolved commit hash** in a later, non-self-referential finalization record.

If a checkpoint tag later resolves to a different commit than the recorded resolved commit hash, treat this as a checkpoint-integrity failure.

---

## 6. Bootstrap Safeguard

The checkpoint mechanism is being introduced while unreviewed material delta already exists.

Required sequence:

1. keep `SYSTEM_STATE_CHECKPOINT_STATUS = BOOTSTRAP_PENDING`;
2. preserve the existing delta;
3. review from the earliest reliably identifiable baseline;
4. perform the catch-up Learning & Change Review;
5. update Engagement Memory;
6. update Learning Candidates where applicable;
7. explicitly assess Professional Background implications;
8. explicitly assess permanent ARCHITECT / governing implications;
9. complete required Manifest / Control updates;
10. canonically persist the coherent system-state bundle;
11. synchronize / verify required runtime-visible sources;
12. only then finalize `CP-NURA-001`.

If the exact historical coherent bundle cannot be reconstructed, do not invent it.

Use the earliest conservatively identifiable baseline and keep historical bundle precision explicitly `UNVERIFIED`.

---

## 7. Delta Reporting Window

Learning & Change Review reports **material delta from the current verified checkpoint**, or from the explicit conservative bootstrap baseline while the first checkpoint is pending.

Required review header:

```text
REVIEW_FROM_CHECKPOINT:
REVIEW_FROM_GIT_REF:
REVIEW_FROM_CANONICAL_REVISION:
REVIEW_TO:
CURRENT_PHASE:
REPORTING_SCOPE: MATERIAL DELTA ONLY
```

Previously checkpointed unchanged state is background, not new work.

Earlier state may be included only when it:

- changed;
- was corrected, rejected or superseded;
- became conflicted;
- gained materially new evidence;
- created a new dependency;
- is required to explain current delta.

---

## 8. Consolidation Pressure Sensor

The sensor is a **Consolidation Pressure Sensor based on observable proxies**.

ARCHITECT does not possess a reliable direct meter of actual context-window occupancy.

The sensor therefore uses:

1. approximate volume proxy;
2. semantic / decision pressure;
3. context-degradation symptoms.

The earliest applicable trigger controls.

### 8.1 Volume Proxy

Estimate substantive new user + ARCHITECT dialogue since the reporting baseline.

Initial NURA calibration:

- **GREEN:** below approximately 12,000 substantive words;
- **YELLOW:** approximately 12,000–20,000;
- **ORANGE:** approximately 20,000–25,000;
- **RED:** above approximately 30,000.

These are provisional operational heuristics, not hard model-capacity claims.

Required behavior:

- GREEN → normal work;
- YELLOW → explicit semantic-pressure assessment; briefly signal that a checkpoint may be approaching;
- ORANGE → normally set consolidation `DUE` unless intervening work is demonstrably low-materiality;
- RED → if the estimate is sufficiently reliable, treat consolidation as `DUE` and do not continue a material design block before review.

If the RED estimate is materially uncertain, treat it at minimum as ORANGE and perform an immediate semantic/degradation assessment rather than claiming a measured hard limit.

### 8.2 Semantic / Decision Pressure — Primary Signal

Set:

`UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = YES`

and therefore:

`CONSOLIDATION_STATE = DUE`

when materially accepted / established Working State reaches a level where leaving it unconsolidated creates material risk.

Recognition cues include:

- approximately 5 or more material accepted decisions;
- approximately 3 or more Open Issues resolved, reopened or materially reclassified;
- creation or material change of a lifecycle / state model;
- rejection or supersession of an established decision;
- material change to a relationship, authority rule, cardinality, boundary or cross-Part dependency;
- multiple new accepted decisions that now depend on one another;
- several current Engagement Memory claims becoming stale;
- material design defect followed by an accepted correction;
- materially reusable learning or a materially refined candidate;
- any single sufficiently consequential accepted decision.

These are recognition cues, not quotas.

### 8.3 Context-Degradation Symptoms — Lagging Backstop

Set:

`CONSOLIDATION_STATE = DUE`

immediately if ARCHITECT detects evidence that active-context reliability may already be degrading, for example:

- uncertainty about which accepted decision is current;
- reintroduction of superseded terminology or rejected alternatives;
- difficulty reconstructing established decisions without searching older dialogue;
- confusion between Working State and accepted Engagement state;
- previously resolved issues being treated as unresolved;
- contradictory recollection of earlier decisions;
- repeated need to recover information that should still be active;
- inability to state confidently what changed since the reporting baseline.

This is an emergency backstop, not the preferred primary trigger.

---

## 9. Material Delta State

Set:

`UNCHECKPOINTED_MATERIAL_DELTA = YES`

when at least one material reportable change exists after the reporting baseline.

This state may validly coexist with:

```text
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
```

when material delta exists but has not yet reached a consolidation trigger.

A phase transition is not required for delta or consolidation to become applicable.

---

## 10. Required Behavior While Consolidation Is DUE

When `CONSOLIDATION_STATE = DUE`, ARCHITECT must, at the next reasonable stopping point:

1. initiate the applicable Learning & Change Review;
2. identify material delta since the reporting baseline;
3. consolidate accepted / established Engagement knowledge into `memory/ENGAGEMENT_MEMORY.md`;
4. synchronize Open / Resolved / Deferred / Rejected / Superseded states;
5. update `memory/LEARNING_CANDIDATES.md` where applicable;
6. perform a full-file consistency check when Engagement Memory was materially patched;
7. explicitly assess Professional Background implications;
8. explicitly assess permanent ARCHITECT / governing implications;
9. update this Control state.

If the runtime has no verified canonical write path, it must not claim that canonical persistence occurred.

It must provide the required final artifacts / patches and keep the system update incomplete until persistence is confirmed.

---

## 11. Consolidation Completion

Consolidation completion and System State Checkpoint finalization are related but separate.

When the applicable Learning & Change Review and consolidation work are complete:

- set `UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK: NO`;
- set `CONSOLIDATION_STATE: CURRENT`;
- record the consolidation evidence / updated artifact versions.

If the coherent system-state update has **not yet been fully persisted and checkpoint-finalized**, keep:

- `UNCHECKPOINTED_MATERIAL_DELTA: YES`;
- `CURRENT_SYSTEM_UPDATE: IN_PROGRESS`.

Therefore the following intermediate state is valid:

```text
UNCHECKPOINTED_MATERIAL_DELTA = YES
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = NOT_READY
```

This resolves the distinction between:

- historical fact that significant work occurred; and
- current fact that significant accepted work remains unconsolidated.

---

## 12. Partial System-State Update Safeguard

Updating one System State Bundle artifact does not create a new checkpoint.

While required update/finalization work remains incomplete:

`CURRENT_SYSTEM_UPDATE = IN_PROGRESS`

The prior verified checkpoint / bootstrap baseline remains the reporting baseline.

Administrative, formatting or Control-only edits do not reset the reporting window while:

`UNCHECKPOINTED_MATERIAL_DELTA = YES`

---

## 13. Checkpoint Finalization — A → B → C → D

Checkpoint finalization must have atomic-like semantics.

A checkpoint is not operationally `VERIFIED` merely because a commit has been created.

### Phase A — Prepare Checkpoint Candidate

1. assign `PENDING_CHECKPOINT_ID`, e.g. `CP-NURA-001`;
2. assign planned tag `refs/tags/nura-checkpoint/CP-NURA-001`;
3. complete the coherent semantic System State Bundle;
4. set `CHECKPOINT_FINALIZATION_STATE = PREPARED`;
5. keep the previous `LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID` unchanged;
6. commit the coherent checkpoint candidate.

The checkpoint candidate commit must **not** itself claim that the pending checkpoint is already operationally VERIFIED.

### Phase B — External Finalization

After the checkpoint candidate commit exists:

1. create an annotated Git tag `nura-checkpoint/CP-NURA-001` pointing to that exact commit;
2. push the commit and tag to the canonical remote;
3. verify the remote tag resolves to the intended commit;
4. capture the resolved commit hash;
5. verify required runtime-visible system-state artifacts against the intended checkpoint bundle;
6. verify dependency pointers, including Parts 00–03 revisions;
7. verify tag-protection / immutability controls where available.

After all required Phase B steps pass:

`CHECKPOINT_FINALIZATION_STATE = EXTERNAL_VERIFICATION_PASSED`

This means the external checkpoint evidence has passed.

It does **not** mean the checkpoint is operationally or canonically `VERIFIED`.

Until Phase C succeeds:

- keep the previous `LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID` authoritative;
- keep the previous reporting baseline active;
- do not reset reporting / sensor counters;
- do not treat `CP-NURA-00X` as the current verified checkpoint.

### Phase C — Canonicalize VERIFIED State

After Phase B reaches `EXTERNAL_VERIFICATION_PASSED`, update the **current** Control in a later administrative commit to record:

```text
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID: CP-NURA-001
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_GIT_REF: refs/tags/nura-checkpoint/CP-NURA-001
LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_COMMIT: <resolved hash of the earlier checkpoint candidate commit>
SYSTEM_STATE_CHECKPOINT_STATUS: VERIFIED
CHECKPOINT_FINALIZATION_STATE: VERIFIED
```

This later Control update is **not** part of the earlier checkpoint snapshot and therefore does not create Git self-reference.

The checkpoint becomes operationally and canonically `VERIFIED` **only when this Phase C administrative Control commit succeeds in the canonical repository**.

At that successful canonicalization point:

- `LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID` advances to the new checkpoint;
- `SYSTEM_STATE_CHECKPOINT_STATUS` becomes `VERIFIED`;
- `CHECKPOINT_FINALIZATION_STATE` becomes `VERIFIED`;
- `REPORTING_WINDOW_START` advances to the new checkpoint;
- reporting / sensor counters reset as defined in Section 16.

Because the Phase C commit is a finalization record rather than new material Engagement delta, it does not create a second checkpoint or a new material reporting window.

If the Phase C canonical commit fails after Phase B evidence has passed:

- the pending checkpoint remains **not VERIFIED**;
- `CHECKPOINT_FINALIZATION_STATE` remains `EXTERNAL_VERIFICATION_PASSED` operationally, or is recorded as `FAILED` where a failure state can be persisted;
- the previous verified checkpoint and reporting baseline remain authoritative;
- no reporting / sensor counters reset;
- retry or repair Phase C before continuing checkpoint finalization.

### Phase D — Synchronize Current Control State to the Active Runtime

After the post-finalization administrative Control commit is canonically persisted:

1. replace / synchronize the active runtime / ChatGPT Project Source copy of `ENGAGEMENT_CONTROL.md` with this current post-finalization Control revision;
2. verify that the active runtime no longer sees the checkpoint-candidate state (`BOOTSTRAP_PENDING`, `PREPARED`, or equivalent stale state);
3. confirm that the runtime-visible Control reflects the finalized checkpoint identity/status and current `REPORTING_WINDOW_START`.

This is **administrative synchronization of current control state**.

It:

- does not create a new System State Checkpoint;
- does not change the identity or snapshot of `CP-NURA-00X`;
- does not reset the reporting window a second time;
- does not create new material Engagement delta.

After successful Phase C, the checkpoint is canonically valid and `VERIFIED`.

Phase D does not determine checkpoint validity; it propagates the current verified Control state to the active runtime.

The runtime is not fit for continued material work until that post-finalization Control state is visible there.

### Finalization Failure

If checkpoint-candidate commit creation, tag creation, remote push, tag resolution, checkpoint-bundle runtime/source verification, required integrity verification, or the Phase C canonical finalization commit fails before canonical verification:

- do not advance `LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID`;
- do not reset the reporting baseline;
- do not reset `UNCHECKPOINTED_MATERIAL_DELTA`;
- do not call the pending checkpoint `VERIFIED`;
- retain the latest truthful pre-verification state (`PREPARED`, `EXTERNAL_VERIFICATION_PASSED`, `PENDING`, or `FAILED`) where it can be persisted without overclaim;
- resolve the failed finalization before treating the checkpoint as verified.

If the later post-finalization Control revision cannot be synchronized to the active runtime / Project Sources:

- preserve the already verified checkpoint identity and snapshot;
- do not create another checkpoint merely to repair source synchronization;
- treat the active runtime as operationally stale for control state;
- do not begin a new material work block in that stale runtime until the current Control source is synchronized.

---

## 14. Checkpoint Integrity

Preferred integrity controls:

1. annotated checkpoint tag;
2. repository rule protecting `nura-checkpoint/*` from update/deletion;
3. resolved checkpoint commit hash recorded in the later non-self-referential finalization record.

If tag protection is unavailable or unverified, the recorded resolved commit hash remains required checkpoint evidence.

If the tag later resolves to a different commit than the recorded resolved hash:

`CHECKPOINT_INTEGRITY_FAILURE`

must be raised and the tag must not be trusted as the checkpoint pointer until reconciled.

---

## 15. Checkpoint Dependency Evidence

Retain checkpoint evidence for architecture outputs even though they are not bundle members.

| Dependency | Canonical revision / pointer | Runtime-visible revision / pointer | Status |
|---|---|---|---|
| Part 00 | TO_RECORD | TO_VERIFY | UNVERIFIED |
| Part 01 | TO_RECORD | TO_VERIFY | UNVERIFIED |
| Part 02 | TO_RECORD | TO_VERIFY | UNVERIFIED |
| Part 03 | TO_RECORD | TO_VERIFY | UNVERIFIED |

Also record the applicable Runtime Deployment Record ID / revision where available.

---

## 16. Counter Reset

Only successful **Phase C canonicalization of the VERIFIED checkpoint state** resets:

- substantive-volume estimate;
- material-decision count;
- Open-Issue delta count;
- uncheckpointed-learning-candidate count;
- other sensor counters tied to the reporting window.

Phase B external verification alone does not reset anything.

At successful Phase C canonicalization:

```text
CURRENT_SYSTEM_UPDATE = CLEAN
UNCHECKPOINTED_MATERIAL_DELTA = NO
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
REPORTING_WINDOW_START = LAST_VERIFIED_SYSTEM_STATE_CHECKPOINT_ID
```

Do not reset counters on:

- Control-only edits;
- Manifest-only edits;
- formatting changes;
- partial persistence;
- failed checkpoint finalization;
- unsynchronized runtime sources.

---

## 17. Phase Transition Rule

System State Checkpoint, Consolidation State and Next Phase Gate are distinct controls:

`System State Checkpoint`
≠
`Consolidation State`
≠
`Next Phase Gate`

Completion of a local conversational plan or task sequence does not by itself establish readiness for the next material phase.

ARCHITECT must not recommend, declare ready for, or begin the `NEXT_PHASE` while:

- `NEXT_PHASE_GATE = NOT_READY`; or
- `CONSOLIDATION_STATE = DUE`; or
- required pre-transition system-state finalization remains incomplete.

Before changing `NEXT_PHASE_GATE` to `READY`, ARCHITECT must perform a separate verification pass against every applicable exit criterion.

---

## 18. Exit Criteria — Ready for Full Rewrite / Synchronization of Parts 00–03

- [ ] Current reconciliation / question cycle is complete: all material items are classified as `RESOLVED`, `OPEN`, or explicitly `DEFERRED`.
- [ ] Catch-up Learning & Change Review has been completed.
- [ ] All accepted / established Working State has been consolidated into current Engagement Memory.
- [ ] Open Issues / Conflicts register is synchronized.
- [ ] Learning Candidates are updated where applicable.
- [ ] Full-file Engagement Memory consistency check is complete.
- [ ] Current Solution State / Readiness reflects latest accepted architecture state.
- [ ] Professional Background implications explicitly assessed.
- [ ] Permanent ARCHITECT / governing implications explicitly assessed.
- [ ] No unresolved ambiguity or conflict materially blocks rewrite.
- [ ] `CP-NURA-001` has been successfully finalized and verified.
- [ ] Required runtime-visible Project Sources are synchronized against the intended checkpoint state.
- [ ] Parts 00–03 dependency revisions are recorded.

---

## 19. Phase Gate Verification Evidence

- **GATE_VERIFIED_AT:** `NOT_VERIFIED`
- **GATE_VERIFIED_BY:** `NOT_VERIFIED`
- **VERIFICATION_RESULT:** `NOT_READY`
- **VERIFICATION_EVIDENCE:** `PENDING`

A vague assertion such as “the latest files seem to be uploaded” is insufficient.

---

## 20. Phase Gate State Change

`CONSOLIDATION_STATE` and `NEXT_PHASE_GATE` are independent.

A valid state is:

```text
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = NOT_READY
```

when consolidation is complete but one or more phase-transition exit criteria remain unsatisfied.

Only when all applicable exit criteria pass:

- set `NEXT_PHASE_GATE: READY`;
- record phase-gate verification evidence.

No ARCHITECT Maintainer approval is required merely to mark an ordinary Engagement phase transition `READY` when evidence passes.

Authority for NURA business decisions, confidentiality decisions and permanent ARCHITECT changes remains role-specific.

---

## 21. Actual Phase Start

`READY` means the next phase may begin. It does not mean it has begun.

When substantive work on `NEXT_PHASE` actually starts, updating this Control is one of the first required actions:

1. move former `NEXT_PHASE` into `CURRENT_PHASE`;
2. define the next material `NEXT_PHASE`;
3. set the new `NEXT_PHASE_GATE: NOT_READY`;
4. define phase-appropriate exit criteria;
5. preserve prior verification evidence in Git history.

Do not continue materially in the new phase while this file still claims the previous phase is current.

---

## 22. Current Expected Sequence

For current NURA ERP state:

**Catch-up delta review from v1.3 conservative baseline**
→ **Engagement Memory consolidation**
→ **Learning Candidates update where applicable**
→ **Professional Background / permanent ARCHITECT assessment**
→ **full-file Memory consistency check**
→ **prepare coherent checkpoint candidate**
→ **Phase A: checkpoint candidate commit**
→ **Phase B: annotated tag + remote/tag/runtime evidence verification**
→ **EXTERNAL_VERIFICATION_PASSED — checkpoint still not VERIFIED**
→ **Phase C: canonical administrative Control commit records VERIFIED + resolved candidate hash**
→ **CP-NURA-001 becomes canonically VERIFIED; reporting window/counters reset**
→ **Phase D: synchronize current Control to active runtime / Project Sources**
→ **CP-NURA-001 verified operational state visible to runtime**
→ **phase-gate verification**
→ **Full Rewrite / Synchronization of Parts 00–03**
→ **cross-Part V&V**

---

## 23. Persistence / Runtime Truth

Canonical persistence is determined by the canonical Engagement repository and its version history.

The active runtime must not claim canonical writes or checkpoint verification it cannot establish.

If this Control itself is stale and the runtime cannot write it canonically, ARCHITECT must:

- state the required state change;
- provide the proposed updated artifact / patch;
- behave conservatively according to the stricter state until persistence is confirmed.
