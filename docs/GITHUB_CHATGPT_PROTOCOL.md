# ChatGPT Web + GitHub Protocol

## 1. Purpose

Framework runs through ChatGPT + GitHub connector. GitHub is persistent state; ChatGPT executes the pipeline in-session.

Framework branch: `main`.
Story branch: `story/<slug>`.

Default production batch: **5 chapters**.

## 2. New Story Protocol

### Step 1 — Resolve slug

Use `meta.slug` or derive kebab-case slug.

### Step 2 — Create story branch

Create `story/<slug>` from `main`.

### Step 3 — Create story tree

At minimum:

```text
manifest.yaml
seed/seed.yaml
bible/story_bible.md
bible/style_bible.md
bible/characters_bible.md
outline/master_outline.md
outline/arcs/arc_001.md
memory/current_state.md
memory/canon_ledger.md
memory/timeline.md
memory/character_states.md
memory/relationships.md
memory/cultivation_ledger.md
memory/inventory_artifacts.md
memory/factions_locations.md
memory/knowledge_ledger.md
memory/foreshadowing.md
memory/unresolved_threads.md
memory/chapter_summaries.md
memory/reader_experience.md
```

### Step 4 — Genesis

1. validate seed;
2. Story Bible;
3. Style Bible;
4. Characters Bible;
5. Master Outline + 3–5 Story Promises;
6. Arc 1 + Promise/Narrative Engine/Xianxia/Emotional plan;
7. initialize story memory;
8. initialize Reader Experience Memory.

## 3. Framework defaults

Native v2.1 manifest:

```yaml
pipeline:
  version: "2.1"
  batch_size: 5
  batch_workflow: "docs/BATCH_5_WORKFLOW.md"
  rolling_audit_every: 3
```

If user explicitly asks for another range or batch size for one run, follow that request. Otherwise “next batch” = 5 chapters.

## 4. Read Protocol

### Framework session

Read:

- `AGENTS.md`;
- relevant workflow docs.

### Story session

Read from exact story branch:

- manifest;
- seed;
- current state;
- reader experience;
- current arc;
- relevant bibles/ledgers;
- recent batch audit;
- recent summaries/finals as needed.

Do not rely on old chat memory as source of truth.

## 5. Write Protocol

Framework changes → `main`.
Story artifacts → matching `story/<slug>`.

Before every write confirm repo, branch, slug, path.

## 6. Atomic Chapter Transaction

For chapter N:

1. scene plan;
2. draft;
3. continuity report;
4. reader retention report;
5. style fingerprint report;
6. aggregate quality report;
7. rewrite;
8. critical re-QC;
9. rolling audit if `N % 3 == 0`;
10. final;
11. update story memory;
12. update reader experience.

Do not move to N+1 before both memories reflect final N.

## 7. Batch 5 Protocol

When user says:

> Viết batch tiếp theo.

Resolve default range:

`next_chapter ... next_chapter + 4`

Typical ranges:

- 1–5
- 6–10
- 11–15
- 16–20

Run chapter transactions sequentially.

After fifth requested chapter create:

`chapters/batch_NNNN_NNNN_audit.md`

Use `docs/BATCH_5_WORKFLOW.md` + `templates/batch_audit.template.md`.

## 8. Rolling Audit vs Batch Boundary

Rolling 3-Chapter Audit is global and independent of batch size.

Trigger on:

`3, 6, 9, 12, 15...`

A rolling window may cross batch boundaries. Example: Ch.4–6 includes chapters from batch 1–5 and batch 6–10; this is expected.

## 9. State Machine

```text
NO_STORY
→ SEED_SAVED
→ STORY_BIBLE_READY
→ STYLE_BIBLE_READY
→ CHARACTERS_BIBLE_READY
→ MASTER_OUTLINE_READY
→ ARC_READY
→ MEMORY_READY
→ READY_TO_WRITE
→ SCENE_PLANNED
→ DRAFTED
→ THREE_QC_COMPLETE
→ AGGREGATE_GATE
→ REWRITTEN
→ ROLLING_AUDITED_IF_DUE
→ FINALIZED
→ MEMORY_COMMITTED
→ READY_TO_WRITE
```

State is inferred from GitHub artifacts.

## 10. Resume Rules

- scene plan exists, no draft → resume Draft.
- draft exists, missing reviewer reports → resume QC.
- reviewers done, aggregate missing → aggregate.
- aggregate requires rewrite, rewrite missing → rewrite.
- rewrite exists, rolling audit due but missing → rolling audit.
- final exists, memory stale → update memory before new chapter.
- memory says N but final only N-1 → repair inconsistency before production.

## 11. Completion Gate

Native v2.1 chapter requires:

- scene plan;
- draft;
- 3 reviewer reports;
- aggregate quality report;
- rewrite when required/configured;
- rolling audit when due;
- final;
- story + reader memory current.

Default batch requires:

- requested 5 finals;
- all required per-chapter artifacts;
- memory through last chapter;
- batch audit;
- next-batch handoff.

If missing → `INCOMPLETE`, not PASS.

## 12. Legacy / Migration Protocol

Story branches do not automatically inherit framework updates.

For pre-v2 or batch-10 stories:

- follow `docs/FRAMEWORK_V2_MIGRATION.md`;
- never fake retroactive pre-final QC;
- historical 10-chapter batch audits remain valid;
- when batch-size migration is applied, set `batch_size: 5`;
- continue next batch from current `next_chapter` for 5 chapters;
- do not split valid historical `batch_0001_0010_audit.md` into fake retroactive 1–5/6–10 audits.

## 13. Standard User Commands

### Genesis

`Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.`

### One chapter

`Viết chương tiếp theo qua đủ pipeline.`

### Batch

`Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW.`

or

`Viết batch tiếp theo đúng pipeline.`

### Audit

`Audit các chương gần nhất: continuity, promises, Narrative Engine, Xianxia Experience, Emotional Residue, power và style fingerprint.`

### Migration

`Sync story này lên framework hiện tại và chuyển default batch sang 5, không retcon final.`

## 14. Automatic Means In-Session

“Automatic” means ChatGPT executes the required stages in the current interaction without asking approval at every step.

It does not mean background execution, daemon work, or pretending unfinished tasks are complete.
