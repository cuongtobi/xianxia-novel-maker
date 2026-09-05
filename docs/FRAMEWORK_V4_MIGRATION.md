# Framework v4.0 Migration — State + Example Driven

v4.0 changes the creative generation model while preserving atomic Git persistence.

## 1. Why migrate

v3.2 reduced controller overhead but still exposed many prose and payoff rules to creative stages. In practice this can over-constrain the model and produce fiction that feels procedural, explanatory or report-like.

v4.0 moves creative control to:

```text
STATE + EXAMPLES
```

and keeps rules only as hard guardrails.

## 2. Major changes

1. Story Promise Controller is retired as an active controller.
2. Reader expectations may remain as planning signals inside Story/Arc State.
3. Combined QC is retired from active chapter production.
4. Scene Plan is replaced by Chapter State + Scene State.
5. Runtime Character State is separated from stable Character Baseline.
6. Writer receives local state + selected prose examples, not QC/style checklists.
7. Continuity Check becomes factual-only.
8. Prose Edit becomes a light example-driven pass after continuity.
9. Style Bible becomes minimal; primary style signal is dynamic examples.
10. Atomic per-chapter Git transaction remains unchanged in principle.
11. Memory becomes explicitly state-centric and gains hierarchical compaction guidance.

## 3. New active chapter artifacts

```text
chapters/NNNN/chapter_state.md
chapters/NNNN/scene_state.md
chapters/NNNN/draft.txt
chapters/NNNN/continuity_check.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

Batch close also includes:

`chapters/batch_NNNN_NNNN_audit.md`

## 4. Retired active artifacts

Do not create new:

- `scene_plan.md`;
- `combined_qc_report.md`;
- `continuity_report.md` old rubric format;
- `reader_retention_report.md`;
- `style_fingerprint_report.md`;
- `quality_report.md`;
- `rewrite.txt`;
- `rolling_3_chapter_audit.md`.

Historical files remain valid evidence of old pipeline execution.

## 5. Story branch migration

For an existing v3.x story:

1. preserve finals, canon, bibles and historical chapter artifacts;
2. update manifest `version: 4.0`;
3. set `creative_mode: state_example`;
4. set `style_mode: dynamic_examples`;
5. set `continuity_mode: factual_only`;
6. set `prose_edit_mode: light_example_driven`;
7. keep `chapter_transaction: atomic_git_commit`;
8. initialize `memory/story_state.md` from current truth;
9. initialize `memory/arc_state.md` from current arc reality, not old planned beats alone;
10. normalize `memory/character_states.md` into runtime state form;
11. preserve continuity ledgers;
12. create `examples/style/index.md` and seed it with project-owned/user-approved samples when available;
13. if project samples are insufficient, temporarily use framework original examples;
14. from `next_chapter` onward use v4.0 workflow;
15. do not backfill v4 state snapshots for old chapters as if they had existed pre-generation.

## 6. Reader expectation migration

Old Story Promises do not need to be deleted.

Convert useful information into soft state signals:

```text
promise → reader expectation
last pay → last meaningful delivery
next payoff window → likely future opportunity
```

Remove per-chapter status enforcement and drought-clearing pressure.

## 7. Style migration

Old Style Bible rules should be compressed into a minimal stable contract.

Move actual prose calibration to examples.

Do not automatically convert old style rules into dozens of example-selection tags. Keep selection functional and simple.

## 8. Character migration

Keep stable identity, motives, blind spots, voice anchors, relationship baselines, cultivation identity and hard contradictions in Character Baseline.

Move transient conditions into Character State:

- current goals;
- emotions;
- knowledge;
- body/injury/fatigue;
- resources;
- relationship context;
- recent consequential memories;
- current bias under pressure.

Do not carry forward deterministic response tables as Writer instructions.

## 9. Atomicity

Future chapters remain atomic:

```text
prepare all files in session
→ create blobs
→ create tree from chapter-start tree
→ create commit with chapter-start HEAD parent
→ update story branch ref once
```

If failure occurs before branch ref update, chapter is incomplete and persistent story state remains at the prior valid commit.

## 10. Compatibility

Historical v2/v3 reports, rewrites and audits may remain in story branches. They are not completion requirements for v4 chapters.

`docs/READER_EXPERIENCE_SYSTEM.md` and `docs/REFERENCE_STYLE_SYSTEM.md` remain as compatibility documents but no longer define active creative controllers.
