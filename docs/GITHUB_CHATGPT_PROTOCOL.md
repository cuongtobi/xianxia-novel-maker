# ChatGPT Web + GitHub Protocol — v4.0 State + Example Driven

## 1. Defaults

Framework branch: `main`.
Story branch: `story/<slug>`.
Default batch: 5 chapters.

Native framework:

```yaml
pipeline:
  version: "4.0"
  creative_mode: "state_example"
  style_mode: "dynamic_examples"
  continuity_mode: "factual_only"
  prose_edit_mode: "light_example_driven"
  chapter_transaction: "atomic_git_commit"
```

## 2. New story

1. resolve slug;
2. create story branch from `main`;
3. build seed, Story Bible, Character Baselines, minimal Style Bible and Master Outline;
4. build project Style Example Bank or bootstrap from framework originals;
5. initialize Story State, Arc State, Character States and continuity ledgers;
6. run Genesis Consistency Audit;
7. mark `READY_TO_WRITE`.

## 3. Read protocol

Read exact story branch. GitHub is source of truth; chat recollection is not.

Before a chapter, read current state first, then only relevant canon/ledgers and recent finals/summaries needed to resolve ambiguity.

Do not feed the Writer every Bible, every ledger or every style document by default.

## 4. In-session chapter protocol

Do not persist intermediate chapter state while generation is incomplete.

In working memory:

1. derive Chapter State;
2. derive Scene State;
3. select 1–3 Style Examples;
4. draft;
5. factual Continuity Check;
6. patch contradictions only if needed;
7. light example-driven Prose Edit;
8. create final;
9. extract Story/Arc/Character State + ledger/summary/manifest updates;
10. prepare batch audit if closing requested batch.

## 5. Persisted files

Per chapter:

```text
chapters/NNNN/chapter_state.md
chapters/NNNN/scene_state.md
chapters/NNNN/draft.txt
chapters/NNNN/continuity_check.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

If chapter closes requested batch:

`chapters/batch_NNNN_NNNN_audit.md`.

No active requirement for:

- `combined_qc_report.md`;
- `continuity_report.md` legacy format;
- `reader_retention_report.md`;
- `style_fingerprint_report.md`;
- `quality_report.md`;
- `rewrite.txt`;
- `rolling_3_chapter_audit.md`.

## 6. Writer isolation

Writer sees only what helps fiction generation:

- local state;
- relevant character state;
- minimal canon anchors;
- selected examples.

Do not attach old QC rubrics, payoff matrices, anti-AI checklists or reviewer reasoning to Writer context.

## 7. Continuity isolation

Continuity Checker sees canon/state + draft and checks factual contradictions only.

It does not make taste judgments or prose rewrites.

## 8. Prose Editor isolation

Prose Editor sees continuity-safe draft + selected examples + minimal edit contract.

It does not see old QC findings or hidden Writer reasoning. It may leave the draft unchanged when prose already works.

## 9. Atomic chapter protocol

At chapter start, capture exact story branch HEAD/tree.

Persist once:

1. create blobs for every new/changed file;
2. create one tree from chapter-start base tree;
3. create one commit with chapter-start HEAD as parent;
4. update exact story branch ref once;
5. verify HEAD and state pointers.

## 10. State machine

```text
READY_TO_WRITE
→ STATE_DERIVED
→ DRAFTED
→ CONTINUITY_PASS
→ PROSE_EDITED
→ FINAL_READY
→ STATE_UPDATE_READY
→ ATOMIC_COMMIT_PREPARED
→ BRANCH_REF_UPDATED
→ CHAPTER_COMPLETE
→ READY_TO_WRITE
```

Intermediate states are session states, not persistent story truth.

## 11. Resume rules

If branch does not contain a complete atomic chapter commit, treat that chapter as incomplete and regenerate from current persistent state.

Do not resume from orphan blobs, verbal claims or partial local state.

If Final exists without matching current Story/Arc/Character State and manifest in the same logical commit, repair before continuing.

## 12. Batch protocol

`Viết batch tiếp theo` = five chapters unless user overrides.

Run five sequential atomic chapter commits. Batch audit exists only in fifth requested chapter commit.

## 13. Completion gate

Chapter complete when branch history contains:

- Chapter State;
- Scene State;
- Draft;
- Continuity PASS;
- Final;
- state/memory current through that final;
- manifest pointer advanced.

Batch complete when five requested chapter commits exist and batch audit is present in the final commit.
