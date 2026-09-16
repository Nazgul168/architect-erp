# ENGAGEMENT_CONTROL.md

- **ENGAGEMENT_ID:** `ENG-NURA-ERP-001`
- **CONTROL_VERSION:** `1.6`
- **CONTROL_STATUS:** ACTIVE
- **LAST_UPDATED:** `2026-09-12`

## 1. Purpose

This file is the canonical Engagement-side control artifact for:

1. consolidation pressure and consolidation state after material Engagement work;
2. System State Checkpoint / delta-reporting state;
3. readiness for material phase transitions;
4. verification evidence for those control states.

It externalizes control state so that ARCHITECT does not rely only on conversational continuity or on remembering a general rule at the correct moment.

This is a textual control artifact, not a hard technical platform lock.

It does not replace the Learning Protocol, Engagement Memory, applicable Engagement authority, or the clean ARCHITECT / Role Updater governance boundary.

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

- **CURRENT_PHASE:** Part 04 — Data Architecture — initiation / design
- **NEXT_PHASE:** Part 05 — Data Model
- **NEXT_PHASE_GATE:** `NOT_READY`
- **NEXT_PHASE_USER_CONTINUATION_DECISION:** `PENDING`
- **INFRASTRUCTURE_DEFERMENT:** `GITHUB_CANONICAL_WRITE / CHECKPOINT FINALIZATION TECHNICALLY UNAVAILABLE`
- **PARTS_00_03_SYNC_STATUS:** `CURRENT WORKING BASELINES / MATERIAL TRANSITION V&V PASS`
- **CONTENT_SYNC_STATUS:** `PENDING — CURRENT CONTENT.pdf STILL SHOWS PRE-SOLUTION-ARCHITECTURE MASTER INDEX`

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

The post-v1.3 material delta has now been reviewed and semantically consolidated, but the first System State Checkpoint remains pending canonical persistence, source verification and checkpoint finalization.

`CP-NURA-001` must remain pending until the required system-state update/finalization cycle is complete. Its pending state does **not** by itself block architecture work after semantic consolidation when the only blocker is technical unavailability of GitHub/canonical checkpoint infrastructure. In that case the continuation policy in Sections 17–21 applies.

### 3.3 Delta / Consolidation State

- **CURRENT_SYSTEM_UPDATE:** `IN_PROGRESS`
- **REPORTING_WINDOW_START:** `BOOTSTRAP_REVIEW_FROM`
- **UNCHECKPOINTED_MATERIAL_DELTA:** `YES`
- **UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK:** `NO`
- **CONSOLIDATION_STATE:** `CURRENT`

Reason: the Part 03 rewrite and final Parts 00–03 normalization have been reviewed and consolidated into proposed `ENGAGEMENT_MEMORY.md v1.9`; the current Parts 00–03 are treated as synchronized working baselines for Data Architecture. No new permanent-ARCHITECT change is proposed by this transition and no new transferable learning candidate is required solely to begin Part 04. `LEARNING_CANDIDATES.md` remains the applicable candidate backlog. Canonical checkpoint persistence/finalization is still pending, so the system update remains `IN_PROGRESS` and material delta remains uncheckpointed.

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
8. explicitly assess clean ARCHITECT / Role Updater implications;
9. complete required Manifest / Control updates;
10. canonically persist the coherent system-state bundle;
11. synchronize / verify required runtime-visible sources;
12. only then finalize `CP-NURA-001`.

This sequence governs **checkpoint finalization**, not semantic permission to continue architecture design. If GitHub/canonical persistence is technically unavailable after complete semantic consolidation, keep the checkpoint pending and apply the controlled infrastructure-deferment path in Sections 17–21 rather than blocking architecture work indefinitely.

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
8. explicitly assess clean ARCHITECT / Role Updater implications;
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

Therefore the following intermediate states are valid:

```text
UNCHECKPOINTED_MATERIAL_DELTA = YES
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = NOT_READY
```

when a **semantic or source-integrity blocker** still exists; or:

```text
UNCHECKPOINTED_MATERIAL_DELTA = YES
UNCONSOLIDATED_SIGNIFICANT_ACCEPTED_WORK = NO
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = READY_WITH_DEFERRED_CHECKPOINT
NEXT_PHASE_USER_CONTINUATION_DECISION = PENDING
```

when semantic consolidation is complete and the only remaining blocker is technical unavailability of canonical GitHub/checkpoint infrastructure.

This distinguishes:

- whether accepted state is semantically consolidated;
- whether checkpoint persistence/finalization has completed; and
- whether the user has explicitly chosen to continue architecture work while checkpoint infrastructure is deferred.

---

### 11.1 Consolidation Evidence — 2026-09-10

- Catch-up Learning & Change Review from conservative baseline `ENGAGEMENT_MEMORY.md v1.3`: COMPLETE.
- `ENGAGEMENT_MEMORY.md v1.4`: runtime-visible and byte-identical to the accepted final v1.4 artifact; SHA-256 `c3e7fca1ad420b57452281f1129b550e9a036b2f7c6dea878720ea1affb30549`.
- `LEARNING_CANDIDATES.md`: runtime-visible and byte-identical to the accepted updated candidate artifact; SHA-256 `edb12c3bfa846fb4535640ae53b9498913ddcbc0b9343cde41216cb4e3ca51b4`.
- Open / Resolved / Deferred register: synchronized in Engagement Memory. Issues #3/#16, #4, #5, #6 and #8 are resolved at architecture-concept level; detailed Part 04–05 modeling/cardinality work is carried by Issue #17 and deferred Authorizing Basis mapping by Issue #32.
- Full-file Engagement Memory consistency check: PASS. Established Architectural Decisions are sequential `1–65`; stale formulations occur only in explicit rejected/superseded or stale-Part descriptions; no blocking internal contradiction was found.
- Professional Background implication: `NO CHANGE`.
- Clean ARCHITECT / Role Updater implication: `NO GOVERNING CHANGE NEEDED`; candidates remain Engagement-side `CANDIDATE` unless separately reclassified through the RF lifecycle.
- Runtime-source verification completed for the current Memory and Learning Candidates artifacts; canonical repository equivalence remains UNVERIFIED until repository access/write and read-back verification succeed.

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
| Part 00 | TO_RECORD — canonical repository currently inaccessible from this runtime | SHA-256 `b3feda08091715f50a9b004e951539bd0b818f113be8cffc1bcf4bc423647d9c` | RUNTIME_VERIFIED / CANONICAL_UNVERIFIED |
| Part 01 | TO_RECORD — canonical repository currently inaccessible from this runtime | SHA-256 `4da41931ea8149f62d45311e2ebaf19bf57c1a356c0609456b0e950e583b46af` | RUNTIME_VERIFIED / CANONICAL_UNVERIFIED |
| Part 02 | TO_RECORD — canonical repository currently inaccessible from this runtime | SHA-256 `733be3c92e057d9cff69e915ad532c3163b56221887f8f7c67d49da4c0a593c5` | RUNTIME_VERIFIED / CANONICAL_UNVERIFIED |
| Part 03 | TO_RECORD — canonical repository currently inaccessible from this runtime | SHA-256 `95c8c55a42572b948d426370a321ac21f123f379de4cb6fdfba35df6c2d8607f` | RUNTIME_VERIFIED / CANONICAL_UNVERIFIED |

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
`Next Phase Gate`.

Completion of a local conversational plan or task sequence does not by itself establish readiness for the next material phase.

A material next phase is **semantically blocked** while:

- `CONSOLIDATION_STATE = DUE`; or
- a required semantic/source-integrity exit criterion is not satisfied; or
- an unresolved ambiguity/conflict materially blocks the next phase.

Pending canonical GitHub persistence or checkpoint finalization is normally an important control-state deficiency, but it is **not by itself a semantic blocker** when all of the following are true:

1. the applicable Learning & Change Review is complete;
2. accepted Working State is fully consolidated into the current runtime-visible Engagement Memory;
3. Open / Resolved / Deferred / Rejected / Superseded states are synchronized;
4. required runtime-visible source artifacts for the next architecture work are verified as the intended consolidated artifacts;
5. no semantic/source-integrity conflict blocks the next phase; and
6. checkpoint completion is blocked solely by technical unavailability of GitHub/canonical persistence infrastructure rather than by uncertainty about the intended state.

In that condition ARCHITECT must:

- disclose that GitHub/canonical checkpoint infrastructure is technically unavailable;
- record the checkpoint as deferred/pending, never as completed or verified;
- set `NEXT_PHASE_GATE = READY_WITH_DEFERRED_CHECKPOINT`;
- ask the user whether to continue the architecture work despite the deferred checkpoint; and
- begin the next phase only after an explicit user decision to continue.

This is a controlled continuation path, not a waiver of semantic consolidation.

---

## 18. Historical Exit Criteria — Gate Used to Start Full Rewrite / Synchronization of Parts 00–03

### 18.1 Semantic readiness criteria — blocking

- [x] Current reconciliation / question cycle is complete: all material items are classified as `RESOLVED`, `OPEN`, or explicitly `DEFERRED`.
- [x] Catch-up Learning & Change Review has been completed.
- [x] All accepted / established Working State has been consolidated into current Engagement Memory.
- [x] Open Issues / Conflicts register is synchronized.
- [x] Learning Candidates are updated where applicable.
- [x] Full-file Engagement Memory consistency check is complete.
- [x] Current Solution State / Readiness reflects latest accepted architecture state.
- [x] Professional Background implications explicitly assessed.
- [x] Clean ARCHITECT / Role Updater implications explicitly assessed.
- [x] No unresolved ambiguity or conflict materially blocks rewrite.
- [x] Runtime-visible `ENGAGEMENT_MEMORY.md` and `LEARNING_CANDIDATES.md` are verified as the intended consolidated artifacts for the next phase.

Failure of any applicable criterion in 18.1 keeps `NEXT_PHASE_GATE = NOT_READY`.

### 18.2 Persistence / checkpoint criteria — required for verified checkpoint, conditionally non-blocking for architecture continuation

- [ ] `CP-NURA-001` has been successfully finalized and verified.
- [ ] Canonical Git persistence/read-back has been verified.
- [ ] Canonical dependency revisions for Parts 00–03 are recorded.

These criteria remain required before claiming a **verified System State Checkpoint**.

If they cannot be completed solely because GitHub/canonical persistence infrastructure is technically unavailable, they may be marked `DEFERRED — INFRASTRUCTURE UNAVAILABLE` for phase-continuation purposes. They must not be marked PASS and the checkpoint must remain pending.

If failure instead indicates uncertainty about which artifact/revision is correct, source mismatch, unresolved semantic conflict, or loss of required evidence, it remains blocking and `NEXT_PHASE_GATE` stays `NOT_READY`.

---

## 19. Historical Phase Gate Verification Evidence for Current Rewrite Phase

- **GATE_VERIFIED_AT:** `2026-09-10`
- **GATE_VERIFIED_BY:** `ARCHITECT runtime — semantic/source verification only`
- **VERIFICATION_RESULT:** `READY_WITH_DEFERRED_CHECKPOINT`
- **SEMANTIC_READINESS:** `PASS`
- **CHECKPOINT_READINESS:** `DEFERRED — GITHUB/CANONICAL PERSISTENCE TECHNICALLY UNAVAILABLE`
- **NEXT_PHASE_USER_CONTINUATION_DECISION:** `APPROVED`
- **VERIFICATION_EVIDENCE:** `Semantic consolidation requirements passed and the user explicitly approved continuation of architecture work despite deferred GitHub/canonical checkpoint infrastructure. The Full Rewrite / Synchronization phase therefore started under the controlled infrastructure-deferment path. Parts 00–02 are now complete working baselines and Part 03 is pending. CP-NURA-001 and canonical dependency revisions remain unverified; no checkpoint completion is claimed.`

A vague assertion such as “the latest files seem to be uploaded” is insufficient.

---


### 19.1 Rewrite completion / transition evidence — 2026-09-12

- Part 00 — Scope & Architecture Principles: rewritten / synchronized current working baseline.
- Part 01 — Business Analysis: rewritten / synchronized current working baseline.
- Part 02 — Process Architecture: rewritten / synchronized current working baseline.
- Part 03 — System Analysis: rewritten / synchronized current working baseline.
- Accepted Calendar Plan / Milestone / Planned Result / Research Output / TRL / AI-assisted extraction, lead/co-executor, Contract Financial Direction and Incoming / Outgoing Contract route refinements are propagated across the applicable Parts.
- Final route scoping correction is propagated: `Target Duration`, Legal reminder, `Critical Escalation Threshold`, `Not Concluded` timing stop and related Post-Award / COO / Director notifications belong to the Legal-led Incoming / Authorizing Agreement route and do not automatically govern Outgoing Contracts.
- Final Project Closure wording is propagated: Closure-Blocking Conditions use Project Obligations / Planned Results and include Deliverables only where an applicable Programme Rule or Agreement uses that term.
- A material transition check across Parts 00–03 found no known semantic contradiction that blocks Part 04. Remaining Issues #15, #17 and #31–34 are intentionally carried into Parts 04–05; institutional / technical verification items remain deferred to the layer where they become decision-relevant.
- Current `CONTENT.pdf` is still stale as a master index: it lists `07. Enterprise Architecture` and does not yet reflect the approved distinct `07. Solution Architecture` + `08. Enterprise Architecture` structure. This is classified as a document-control synchronization delta, not a semantic blocker to Part 04.

The previously approved infrastructure-deferred continuation remains valid for architecture work. It does not convert the pending System State Checkpoint into a verified checkpoint.

---

## 20. Phase Gate State Change

`CONSOLIDATION_STATE` and `NEXT_PHASE_GATE` are independent.

Allowed transition-readiness states for the current Engagement control are:

- `NOT_READY` — one or more blocking semantic/source-integrity criteria fail;
- `READY_WITH_DEFERRED_CHECKPOINT` — semantic readiness passes, checkpoint infrastructure is technically unavailable, and explicit user continuation decision is still required;
- `READY` — semantic readiness passes and applicable persistence/checkpoint requirements needed for the intended transition have also passed.

A valid infrastructure-deferred state is:

```text
CONSOLIDATION_STATE = CURRENT
NEXT_PHASE_GATE = READY_WITH_DEFERRED_CHECKPOINT
NEXT_PHASE_USER_CONTINUATION_DECISION = PENDING
SYSTEM_STATE_CHECKPOINT_STATUS = BOOTSTRAP_PENDING
```

When `READY_WITH_DEFERRED_CHECKPOINT`, ARCHITECT must inform the user of the technical GitHub/canonical persistence limitation and ask whether to continue architecture work.

If the user explicitly chooses to continue:

```text
NEXT_PHASE_USER_CONTINUATION_DECISION = APPROVED
```

The architecture phase may then start while checkpoint state remains pending.

If the user chooses not to continue, keep the phase unchanged and wait for infrastructure recovery / checkpoint completion.

No RF Owner / clean-ROLE approval is required merely for this ordinary Engagement phase continuation. Authority for NURA business decisions, confidentiality decisions, candidate approval-for-review and clean ARCHITECT releases remains role-specific.

---

## 21. Actual Phase Start

`READY` or `READY_WITH_DEFERRED_CHECKPOINT + NEXT_PHASE_USER_CONTINUATION_DECISION = APPROVED` means the next architecture phase may begin. It does not mean it has already begun.

When substantive work on `NEXT_PHASE` actually starts, updating this Control is one of the first required actions:

1. move former `NEXT_PHASE` into `CURRENT_PHASE`;
2. define the next material `NEXT_PHASE`;
3. set the new phase's gate according to its own readiness criteria;
4. preserve `CP-NURA-001` and canonical persistence as `PENDING / DEFERRED` until actually completed;
5. preserve prior verification evidence and user continuation decision in canonical history when GitHub becomes available.

Do not claim checkpoint finalization merely because architecture work continued under the deferred-infrastructure path.

### 21.1 Current phase-start record — 2026-09-12

The user has explicitly stated that Parts 00–03 in the current project sources are updated and directed ARCHITECT to proceed to Part 04.

Transition assessment:

- semantic consolidation of the current Parts 00–03 baseline: `PASS`;
- material cross-Part transition V&V: `PASS` for starting Data Architecture;
- Part 04 blocking ambiguity: `NONE IDENTIFIED`;
- current `CONTENT.pdf` master-index synchronization: `PENDING / NON-BLOCKING FOR PART 04`;
- canonical Git/checkpoint finalization: `DEFERRED — INFRASTRUCTURE UNAVAILABLE`;
- current phase start authorization from the Engagement user: `APPROVED`.

Accordingly, `Part 04 — Data Architecture` is the active architecture phase. `Part 05 — Data Model` remains the next material phase and its gate is `NOT_READY` until Part 04 is sufficiently complete and its relevant open data-architecture decisions are consolidated.

No canonical write or verified System State Checkpoint is claimed by this update.

---

## 22. Current Expected Sequence

Current NURA ERP progress is:

**semantic consolidation complete**
→ **infrastructure-deferred continuation explicitly approved by user**
→ **Part 00 rewritten / synchronized**
→ **Part 01 rewritten / synchronized**
→ **Part 02 rewritten / synchronized**
→ **Part 03 rewritten / synchronized**
→ **material cross-Part transition V&V PASS**
→ **CURRENT: Part 04 Data Architecture**
→ **NEXT: Part 05 Data Model**
→ **Part 06 Information Architecture**
→ **Part 07 Solution Architecture**
→ **Part 08 Enterprise Architecture**.

`CONTENT.pdf` synchronization to the approved master structure remains pending and must be completed before a later publication/checkpoint claims the master contents are synchronized. It does not currently block Part 04 semantic work.

Canonical GitHub/checkpoint infrastructure remains technically unavailable. Therefore `CP-NURA-001` remains pending and must not be described as verified or complete.

When GitHub becomes available, resume canonical persistence / checkpoint finalization and record the actual dependency revisions. Architecture work performed during the infrastructure-deferred period must remain traceable to the runtime-visible consolidated baseline used for that work.

---

## 23. Persistence / Runtime Truth

Canonical persistence is determined by the canonical Engagement repository and its version history.

The active runtime must not claim canonical writes or checkpoint verification it cannot establish.

If this Control itself is stale and the runtime cannot write it canonically, ARCHITECT must:

- state the required state change;
- provide the proposed updated artifact / patch;
- keep canonical persistence / checkpoint status explicitly `PENDING / DEFERRED`, never falsely `VERIFIED`;
- if semantic consolidation or source integrity is incomplete, remain blocked;
- if semantic consolidation is complete and GitHub/canonical persistence is the only technical blocker, apply Sections 17–21: inform the user, ask whether to continue architecture work, and proceed only after explicit user approval while preserving the deferred checkpoint state.
