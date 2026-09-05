# Batch 5 Chapters Workflow — v4.0 State + Example Driven

## 1. Goal

Default batch = **5 chapters**. Run sequentially; each chapter is one atomic Git transaction.

Creative generation is state-driven and example-driven. Do not reintroduce retired creative controllers/checklists.

## 2. Preflight batch

Before first chapter:

1. confirm repo / exact story branch / slug;
2. read `AGENTS.md` + manifest;
3. verify `pipeline.version: 4.0`, `batch_size: 5`, `creative_mode: state_example` and `chapter_transaction: atomic_git_commit`;
4. read seed, Story Bible, Character Baselines, minimal Style Bible and Master Outline;
5. read current Story State, Arc State, relevant Character States and continuity ledgers;
6. read recent summaries/final only as needed;
7. resolve exact requested range `start ... start+4` unless user overrides;
8. verify prior batch audit if previous requested range is complete.

## 3. Per-chapter context

Read enough reality to derive the next chapter without rereading everything:

- current story state;
- current arc state;
- relevant character states;
- relevant timeline/knowledge/relationship/cultivation/inventory/faction/foreshadowing/unresolved ledgers;
- recent 3 chapter summaries;
- latest full final when direct continuity needs it;
- master direction only for long-range orientation.

## 4. Derive Chapter State

Create `chapters/NNNN/chapter_state.md` in working memory.

It should capture:

- entry reality;
- active pressures;
- relevant cast/knowledge/body/resource/relationship conditions;
- unresolved tensions currently ripe;
- plausible meaningful state changes;
- continuity anchors;
- any long-direction signal currently relevant.

Do not prescribe a beat-by-beat route unless a hard canon obligation requires it.

## 5. Derive Scene State

Create `chapters/NNNN/scene_state.md` in working memory.

For each scene capture:

- POV / time / place / cast;
- what just happened;
- immediate desires;
- emotional/body/relationship state;
- knowledge/suspicion/wrong belief;
- pressure/resources/limitations;
- possible directions if useful;
- exit expectation as meaningful **state change**.

Scene State is reality, not prose instruction.

## 6. Select Style Examples

Choose 1–3 examples by scene function.

Priority:

1. user-approved project examples/finals;
2. strong project-owned finals;
3. curated project examples;
4. framework bootstrap examples.

Do not choose examples because their plot resembles the target scene. Choose by prose function: dialogue, quiet narration, combat, cultivation/craft, mystery/tension, aftermath, etc.

## 7. Draft

Writer receives:

- Chapter/Scene State;
- relevant Character State;
- minimal canon anchors;
- selected Style Examples.

Writer does **not** receive the old Combined QC checklist, Story Promise status matrix or long Style Bible rule list.

Write fiction naturally from current state.

## 8. Continuity Check

Create one factual report:

`chapters/NNNN/continuity_check.md`

Check only:

- canon;
- timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction state;
- POV identity;
- hard character-baseline contradiction.

Decision:

- `PASS`;
- `FIX_REQUIRED`.

If FIX_REQUIRED, patch only contradictions and recheck them. Do not rewrite prose for taste.

## 9. Prose Edit

After Continuity PASS, run a light example-driven edit.

Input: continuity-safe draft + selected examples.

Editor must:

- preserve event/decision/dialogue intent/scene shape;
- leave good prose untouched;
- remove redundant explanation;
- compress report-like reasoning;
- repair unnatural Vietnamese or convert-like clause order;
- trim obvious repetition;
- avoid standardizing cadence/paragraph shape;
- avoid adding aphorisms/punchlines/plot.

No separate prose-edit report is required. Edited candidate becomes final.

## 10. Prepare state updates

Read final as truth, then calculate:

- canon changes if new facts are locked;
- story state;
- arc state;
- relevant character states;
- timeline;
- relationships;
- cultivation;
- inventory/artifacts;
- factions/locations;
- knowledge;
- foreshadowing;
- unresolved threads;
- chapter summary;
- manifest pointers.

Never persist state inferred from draft text removed during prose edit.

## 11. One atomic Git commit

Hold chapter-start HEAD/tree as parent/base.

After all content is ready:

1. create blobs for Chapter State, Scene State, Draft, Continuity Check, Final and all changed state/memory/manifest files;
2. if chapter closes requested batch, include batch audit blob;
3. `create_tree(base_tree=<chapter-start tree>)`;
4. `create_commit(parent=<chapter-start HEAD>)`;
5. `update_ref` story branch exactly once;
6. verify HEAD + manifest/state.

Suggested commit:

`story: finalize chapter N with state-driven pipeline`

Batch close:

`story: finalize chapter N and batch A-B`

If failure happens before `update_ref`, chapter is not complete.

## 12. Sequential guarantee

Start N+1 only after:

- commit N is branch HEAD/history;
- final exists;
- Continuity result = PASS;
- Story/Arc/Character State reflects final N;
- manifest points to N+1.

## 13. Batch audit

After fifth requested chapter, create `chapters/batch_NNNN_NNNN_audit.md` in that same atomic commit.

Audit only:

- five chapter commits/finals complete;
- continuity checks PASS;
- story/arc/character states current;
- continuity handoff clean;
- unresolved obligations/knowledge/resource state coherent;
- example selection not collapsing into copied scene patterns;
- next-batch handoff.

No per-chapter payoff quota, style score, rolling audit or chapter-3 checkpoint.

## 14. Completion gate

Batch READY when:

- all 5 requested finals exist;
- each chapter has Chapter State + Scene State + Draft + Continuity Check + Final;
- every Continuity Check = PASS;
- each chapter has one atomic commit;
- runtime state is current through last chapter;
- batch audit is present in the fifth commit.
