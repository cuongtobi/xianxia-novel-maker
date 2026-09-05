# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt** trên ChatGPT Web + GitHub.

Framework hiện hành: **v4.0 — State + Example Driven**.

## Creative model

```text
SEED
→ STORY BIBLE
→ CHARACTER BASELINES
→ MASTER OUTLINE
→ STORY / ARC STATE
→ CHAPTER STATE
→ SCENE STATE
→ CHARACTER STATE + STYLE EXAMPLES
→ WRITER
→ DRAFT
→ CONTINUITY CHECK
→ PROSE EDIT
→ FINAL
→ STATE UPDATE
→ ONE ATOMIC GIT COMMIT
```

Triết lý:

```text
Rules giữ hard boundaries.
State giữ reality hiện tại.
Examples calibrate prose.
Writer viết fiction từ state, không viết theo checklist.
```

## v4.0 khác v3.2

- Story Promise không còn là controller; reader expectations chỉ là planning signal trong state.
- Combined QC được bỏ khỏi active pipeline.
- Writer không nhận style/QC checklist dài.
- Scene Plan được thay bằng **Chapter State + Scene State**.
- Character Bible là baseline; runtime dùng **Character State**.
- Prose style chuyển từ rule-driven sang **dynamic Style Examples**.
- Continuity Check chỉ kiểm factual/state contradiction.
- Prose Edit là pass nhẹ, example-driven, không rewrite toàn chapter theo checklist.
- Atomic Git transaction của mỗi chapter vẫn được giữ.

## Genesis

```text
Seed
→ Story Bible
→ Character Baselines
→ Minimal Style Bible
→ Master Outline
→ Style Example Bank
→ Initial Story State
→ Initial Arc State
→ Initial Character States
→ Genesis Consistency Audit
→ READY_TO_WRITE
```

## Per chapter

```text
READ CURRENT STATE
→ DERIVE CHAPTER STATE
→ DERIVE SCENE STATE
→ SELECT 1–3 STYLE EXAMPLES
→ WRITE DRAFT
→ CONTINUITY CHECK
→ FACTUAL FIX IF NEEDED
→ LIGHT PROSE EDIT
→ FINAL
→ EXTRACT + UPDATE STATE
→ ATOMIC COMMIT
```

Persisted chapter artifacts:

```text
chapters/NNNN/chapter_state.md
chapters/NNNN/scene_state.md
chapters/NNNN/draft.txt
chapters/NNNN/continuity_check.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

Nếu chapter đóng requested batch, cùng commit thêm `chapters/batch_NNNN_NNNN_audit.md`.

## Batch 5

Default batch = 5 chapters. Mỗi chapter = một atomic commit. Chapter N+1 chỉ bắt đầu sau khi commit N verify thành công. Batch audit chỉ tạo ở chapter thứ 5 của requested range.

## Style examples

Writer chọn 1–3 examples phù hợp function của scene:

- quiet/narration;
- dialogue/relationship;
- combat/action;
- cultivation/craft;
- mystery/tension;
- emotional aftermath.

Ưu tiên project-owned/user-approved finals. Khi story chưa có sample tốt, dùng original bootstrap examples của framework. Không copy wording, rhetorical frame, imagery hoặc scene structure.

## Source of truth

```text
1. Canon Ledger
2. Final Chapters
3. Bibles
4. Current Story/Arc/Character State
5. Continuity Ledgers
6. Master Outline
7. Seed
8. Chapter/Scene State snapshots
9. Draft
```

## Core docs

- `AGENTS.md`
- `docs/ARCHITECTURE.md`
- `docs/STATE_EXAMPLE_SYSTEM.md`
- `docs/BATCH_5_WORKFLOW.md`
- `docs/GITHUB_CHATGPT_PROTOCOL.md`
- `docs/FRAMEWORK_V4_MIGRATION.md`
- `memory/MEMORY_SYSTEM.md`
- `prompts/PIPELINE_PROMPTS.md`

## Principle

```text
GitHub giữ persistent truth.
Bible giữ stable world/character baseline.
State giữ hiện tại.
Examples giữ cảm giác prose.
Continuity Check giữ factual correctness.
Prose Edit chỉ sửa khi prose thật sự cần.
Atomic commit giữ transaction sạch.
Final giữ tác phẩm.
```
