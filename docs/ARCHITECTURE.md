# Architecture — v4.0 State + Example Driven

## 1. Overview

Framework chạy trên ChatGPT Web + GitHub. GitHub giữ persistent truth; ChatGPT derive state, viết fiction và update state.

Creative model:

```text
SEED
→ STORY BIBLE
→ CHARACTER BASELINES
→ MASTER OUTLINE
→ STORY STATE
→ ARC STATE
→ CHAPTER STATE
→ SCENE STATE
→ CHARACTER STATE + STYLE EXAMPLES
→ WRITER
→ DRAFT
→ CONTINUITY CHECK
→ PROSE EDIT
→ FINAL
→ STATE UPDATE
→ ATOMIC COMMIT
```

Không có creative controller bắt Writer thỏa checklist. Reader expectation/payoff chỉ là planning signal trong state.

## 2. Design principle

### State-driven

State trả lời: **hiện tại chuyện gì là thật?**

- who is where;
- what just happened;
- what each character wants/knows/believes;
- injury/fatigue/resource status;
- relationship tension;
- faction positions;
- arc pressure;
- unresolved obligations;
- likely directions now ripe.

### Example-driven

Examples trả lời: **prose tốt của project này có cảm giác thế nào?**

Examples calibrate execution, không quyết định plot.

### Rule-driven

Rules chỉ bảo vệ:

- canon;
- continuity;
- originality;
- content boundaries;
- persistence protocol.

Rules không trở thành prose recipe.

## 3. Data layers

### Stable canon

- Story Bible;
- Character Baselines;
- Canon Ledger;
- Final Chapters.

### Long direction

- Master Outline;
- saga direction;
- major reveals/relationships/progression;
- reader expectations.

### Runtime state

- `memory/story_state.md`;
- `memory/arc_state.md`;
- `memory/character_states.md`;
- timeline/knowledge/relationship/cultivation/inventory/faction/foreshadowing/unresolved ledgers.

### Local generation state

- Chapter State;
- Scene State;
- selected Style Examples.

Local generation state snapshots are evidence of what Writer received, but Final remains higher truth.

## 4. State derivation

```text
Final + Current Runtime State + Master Direction
                    ↓
                Arc State
                    ↓
              Chapter State
                    ↓
                Scene State
```

Derivation should compress reality, not invent a beat checklist.

A state may expose several plausible directions. Writer chooses through character desire + pressure + circumstance.

## 5. Character model

Character Bible stores stable baseline: identity, core motive, blind spots, voice anchors, relationship baselines, cultivation identity and forbidden contradictions.

Runtime Character State stores transient facts: immediate goal, emotion, belief, bias, knowledge, body, resources, relationships and recent consequential memories.

Writer receives only relevant baseline anchors + runtime state, not a full situation-response matrix.

## 6. Style model

Minimal Style Bible stores project-level boundaries only. Primary style signal is selected prose examples.

Selection priority:

1. user-approved project finals;
2. strong project-owned finals;
3. project curated examples;
4. framework original bootstrap examples.

Select by scene function, normally 1–3 examples. Avoid loading an entire style corpus.

## 7. Writer

Writer input:

```text
SCENE/CHAPTER STATE
+ RELEVANT CHARACTER STATE
+ CANON ANCHORS
+ 1–3 STYLE EXAMPLES
```

Writer is not given continuity/style/payoff checklists.

State is reality, not a command list. Writer lets characters act from current desire, knowledge, emotion, relationship and limitation.

## 8. Continuity Check

Continuity Check is factual only:

```text
canon / timeline / geography / power / resources /
injury / knowledge / relationship / faction / POV /
hard baseline contradiction
```

It does not review prose quality, pacing, emotional arc or reader payoff.

`PASS` or `FIX_REQUIRED`.

## 9. Prose Edit

After factual continuity passes, a light editor uses the same or nearby style examples.

The editor should preserve variation and leave good prose untouched. Main legitimate edits:

- remove redundant explanation;
- compress report-like reasoning;
- repair unnatural Vietnamese;
- repair awkward translation-like clauses;
- trim obvious repetition;
- improve local clarity without changing scene state.

No style report is required.

## 10. Atomicity model

Each chapter starts from fixed branch HEAD/tree.

All outputs are prepared before Git write:

```text
chapter_state
scene_state
draft
continuity_check
final
state/ledger updates
manifest
batch audit if needed
```

Then:

```text
create_blob × changed files
→ create_tree(base_tree=chapter_start_tree)
→ create_commit(parent=chapter_start_HEAD)
→ update_ref once
```

If failure occurs before `update_ref`, branch state remains at the prior complete chapter.

## 11. Batch 5

Batch = five sequential atomic chapter commits. No checkpoint at chapter 3. Batch audit is included in the fifth requested chapter commit.

## 12. Completion semantics

Chapter COMPLETE when its branch history contains an atomic commit with:

- Chapter State;
- Scene State;
- Draft;
- Continuity PASS;
- Final;
- current runtime state/manifest.

Batch COMPLETE when all five commits/finals exist, runtime state is current through the fifth chapter and batch audit exists.

## 13. Long-story scaling

Memory uses hierarchical compaction:

```text
recent chapter detail
→ batch summaries
→ completed arc summary
→ completed saga summary
```

Never compact away canon facts, unresolved obligations, active knowledge boundaries, resource ownership or relationship consequences.

Framework optimizes for:

**natural fiction + continuity + state coherence + prose calibration + low creative-rule pressure + recoverable atomic execution**.
