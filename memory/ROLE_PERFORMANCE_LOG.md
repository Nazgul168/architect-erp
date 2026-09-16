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
