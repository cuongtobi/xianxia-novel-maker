# Architecture

## 1. Overview

Xianxia Novel Maker chạy trên **ChatGPT Web + GitHub connector**. GitHub là persistent state; ChatGPT là execution engine.

Pipeline v2.1:

```text
Human Seed
↓
Genesis
  ├─ Story Bible
  ├─ Style Bible
  ├─ Characters Bible
  ├─ Master Outline + 3–5 Story Promises
  ├─ Arc Outline
  └─ Story + Reader Experience Memory
↓
Sequential Chapter Transaction
  ├─ Context Assembly
  ├─ Scene Plan
  ├─ Draft
  ├─ Continuity Auditor
  ├─ Reader Retention Editor
  ├─ Style Fingerprint Auditor
  ├─ Aggregate Quality Gate
  ├─ Rewrite + Critical Re-QC
  ├─ Rolling 3-Chapter Audit when due
  ├─ Final TXT
  └─ Memory Commit
↓
Batch Audit every 5 default chapters
```

## 2. Data layers

### Canon / slow-changing

- bibles;
- canon ledger;
- Character DNA;
- Story Promise contract;
- final chapters.

### Planning

- master outline;
- arc outlines;
- planned Promise PAY windows;
- planned Narrative Engine distribution;
- planned Xianxia/Emotional targets.

Planning can change; final/canon wins.

### Runtime story state

- current state;
- timeline;
- character states;
- relationships;
- cultivation;
- inventory;
- faction/location;
- knowledge;
- foreshadowing;
- unresolved threads;
- chapter summaries.

### Reader Experience state

`memory/reader_experience.md` tracks:

- Story Promise ADVANCE/PAY;
- last major payoff;
- recent Narrative Engines;
- dialogue geometries;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes;
- reader appetite/payoff debt.

## 3. Story branch lifecycle

### Create

From `main` create `story/<slug>`.

### Bootstrap

```text
stories/<slug>/
  manifest.yaml
  seed/
  bible/
  outline/arcs/
  chapters/
  final/
  memory/
```

### Genesis

1. validate seed;
2. story bible;
3. style bible;
4. characters bible;
5. master outline + Story Promises;
6. opening arc;
7. initialize story memory;
8. initialize reader experience.

### Production

Chapter transactions are sequential.

### Default batch checkpoint

Every 5 requested chapters:

`chapters/batch_NNNN_NNNN_audit.md`

Typical ranges: 1–5, 6–10, 11–15...

Existing historical 10-chapter audits remain valid after migration.

## 4. Context Assembly

Always read:

- seed;
- story/style bible;
- Story Promises;
- arc;
- current state;
- reader experience;
- canon;
- recent summaries.

Scene-specific reads:

- Character DNA;
- cultivation/knowledge/relationships;
- factions/locations;
- foreshadowing/unresolved threads.

Historical full final reads when:

- callback needs exact text;
- continuity is uncertain;
- Reader Retention/Style/Rolling Audit needs pattern comparison.

## 5. Story Promise system

Every story locks 3–5 reader promises.

A promise records:

- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

Each final updates promise state in Reader Experience Memory.

## 6. Narrative Engine system

Narrative Engine describes **how movement happens**, not topic.

Examples: audit, negotiation, hypothesis-test, training calibration, chase, reveal, ritual, domestic, combat, grief, wonder, investigation.

Hard rolling rule:

**3/4 recent chapters with same primary engine = MAJOR pacing risk.**

This window crosses batch boundaries.

## 7. Xianxia Experience

Track independently from world logic:

- cultivation payoff;
- wonder/awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- magical craft;
- world-scale glimpse.

## 8. Character engine

Two layers:

### Core DNA

Values, fears, wounds, decision logic, speech, irrationality, costly mistake tendency.

### Runtime state

Location, goal, emotion, injury, relationships, secrets, resources.

Characters may be intelligent but should not become perfect optimizers.

## 9. Scene architecture

Scene planning is intentionally relaxed.

### Conflict/transaction scene

May use goal/obstacle/stakes/turn/choice/consequence.

### Quiet/discovery/emotional scene

May use focal tension/curiosity + sensory anchor + knowledge boundary + meaningful movement/residue.

Not every scene must be a mini-plot.

## 10. QC architecture

Three independent reviewers:

### Continuity Auditor

Data/canon/state/knowledge/power/POV.

### Reader Retention Editor

Promise delivery, Narrative Engine, pacing/drag, agency, Xianxia Experience, Emotional Residue.

### Style Fingerprint Auditor

Rhetorical patterns, Q&A cleanliness, hypothesis-loop, aphorism density, cadence, calibration.

Aggregate gate cannot PASS with reviewer BLOCKER/MAJOR.

## 11. Rolling 3-Chapter Audit

Runs globally on chapter numbers divisible by 3:

`3, 6, 9, 12, 15...`

It is independent of batch size.

Reads full N-2 + N-1 + candidate N and checks cross-chapter experience/style patterns before final.

## 12. Batch 5 architecture

Default batch size is 5.

```text
Batch start
→ Preflight
→ Chapter N full transaction
→ Chapter N+1 reads updated memory
→ ...
→ Chapter N+4 full transaction
→ Batch Audit
→ Next-batch handoff
```

Do not draft all 5 in parallel.

Batch boundaries are operational, not story-arc boundaries.

Arc may end in the middle of a batch; new arc must be initialized before writing beyond the boundary.

## 13. Atomic chapter transaction

```text
READ
→ PLAN
→ DRAFT
→ 3 REVIEWERS
→ AGGREGATE
→ REWRITE
→ CRITICAL RE-QC
→ ROLLING AUDIT IF DUE
→ FINAL
→ UPDATE STORY MEMORY
→ UPDATE READER EXPERIENCE
```

If either memory update fails, transaction is incomplete.

## 14. Completion semantics

`PASS/READY` is an artifact state, not a verbal judgment.

Per chapter required in enforcement window:

- scene plan;
- draft;
- 3 reviewer reports;
- aggregate quality report;
- rewrite when required;
- rolling audit when due;
- final;
- current story + reader memory.

Per default batch:

- 5 requested finals;
- memory current through last chapter;
- batch audit;
- next-batch handoff.

Missing required artifact → `INCOMPLETE`.

## 15. Legacy compatibility

Changing default batch size from 10 to 5 does not invalidate old story history.

If a story already has `batch_0001_0010_audit.md`, keep it.

When synced to v2.1:

- set `pipeline.batch_size: 5`;
- set `batch_workflow: docs/BATCH_5_WORKFLOW.md`;
- continue from current `next_chapter` for 5 chapters;
- do not fake retroactive split audits.

## 16. Design principle

Pipeline optimizes for:

**continuity + reader experience + prose quality + controllability**.

Batch 5 intentionally shortens the feedback loop so outline/pacing/style can adapt twice as often as the old batch-10 workflow.
