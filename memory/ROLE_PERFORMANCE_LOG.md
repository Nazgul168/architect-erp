# ROLE Performance Log — NURA ERP Architecture

Engagement: `ENG-NURA-ERP-001`  
Target ROLE: `architect`  
Status: ACTIVE

Purpose: preserve user feedback about **ARCHITECT behavior/performance** observed in this Engagement.

This file is not authoritative for NURA business/domain truth and must not be used as a substitute for `ENGAGEMENT_MEMORY.md`.

## What belongs here

Examples:

- ARCHITECT repeatedly missed a required verification step;
- ARCHITECT over-produced detail when a compact answer was required;
- ARCHITECT correctly detected a modeling failure pattern;
- ARCHITECT failed to retrieve/apply relevant Expert Memory;
- ARCHITECT violated or followed an important professional protocol.

## What does not belong here

- NURA architecture decisions;
- business requirements;
- institutional facts;
- source-document facts;
- ordinary project progress;
- transferable professional principles themselves (those belong in `LEARNING_CANDIDATES.md`).

## Entry schema

```yaml
feedback_id:
recorded_at:
source: USER | OBSERVED_BEHAVIOR_REVIEW
scope:
feedback:
evidence_ref:
severity: LOW | MEDIUM | HIGH
repeat_pattern: YES | NO | UNKNOWN
candidate_implication: NONE | CONSIDER_LEARNING_CANDIDATE | CONSIDER_ROLE_CHANGE
status: OPEN | RESOLVED | SUPERSEDED
```

## Entries

No RF v4.5 ROLE-performance entries recorded at migration baseline.

### RPL-NURA-001 — Active source-set boundary was not established before consistency claims

```yaml
feedback_id: RPL-NURA-001
recorded_at: 2026-09-16
source: USER
scope: Source verification / consistency audit / artifact generation
feedback: >
  ARCHITECT twice failed to bound the review to the actual current Project Sources before claiming
  source consistency. It first treated an older/historical CONTENT.pdf reference as a current source
  and generated an unnecessary replacement artifact; on the next pass it still did not explicitly
  verify all 25 active source files before reporting the result. The user required a single complete
  pass over the real active source set instead of piecemeal corrections.
evidence_ref: Current Engagement chat, 2026-09-16
severity: HIGH
repeat_pattern: YES
candidate_implication: CONSIDER_LEARNING_CANDIDATE
status: RESOLVED
```

**Corrective behavior applied:** before the replacement set below was prepared, the runtime-visible source boundary was explicitly established as the 25 active Project Source files. References to absent artifacts are no longer treated as supplied sources, and `ENGAGEMENT_CONTROL.md` now records the source-set verification discipline for future chats.
