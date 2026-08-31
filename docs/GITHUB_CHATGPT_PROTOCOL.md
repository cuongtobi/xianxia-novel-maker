# ChatGPT Web + GitHub Protocol — Promise-Only

## 1. Purpose

Framework chạy qua ChatGPT + GitHub connector. Framework ở `main`; mỗi story ở `story/<slug>`; default batch = 5.

Controller duy nhất: **Story Promise Controller**.

## 2. New Story Protocol

1. resolve slug;
2. create `story/<slug>` from `main`;
3. create manifest/seed/bibles/outlines/memory tree;
4. Genesis: Seed → Story Bible → Style Bible → Characters Bible → Master Outline + 3–5 Story Promises → Arc 1 + Promise PAY windows → Story Memory + Promise Memory;
5. mark READY_TO_WRITE.

## 3. Framework defaults

```yaml
pipeline:
  version: "3.1"
  batch_size: 5
  batch_workflow: "docs/BATCH_5_WORKFLOW.md"
  controllers:
    - story_promise
  qc_modes:
    - continuity
    - story_promise
    - style_fingerprint
```

## 4. Read Protocol

Đọc framework contract và exact story branch. Không dùng chat memory làm source of truth khi GitHub artifact đã tồn tại.

Story session tối thiểu đọc manifest, seed, current state, promise memory, current arc, Story Promises, bibles/ledgers liên quan, recent summaries/finals khi cần.

## 5. Write Protocol

Framework changes → `main`. Story artifacts → matching `story/<slug>`.

## 6. Atomic Chapter Transaction

1. scene plan;
2. draft;
3. continuity report;
4. Story Promise review (`reader_retention_report.md` giữ tên vì compatibility);
5. style fingerprint report;
6. aggregate quality report;
7. rewrite nếu cần;
8. critical re-QC;
9. final;
10. update story memory;
11. update promise memory.

Không có mandatory rolling audit.

## 7. Batch Protocol

`Viết batch tiếp theo` mặc định = `next_chapter ... next_chapter+4`.

Run tuần tự. Sau chapter cuối tạo `chapters/batch_NNNN_NNNN_audit.md`.

## 8. State Machine

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
→ REWRITTEN_IF_NEEDED
→ FINALIZED
→ MEMORY_COMMITTED
→ READY_TO_WRITE
```

## 9. Resume Rules

Resume từ artifact thiếu gần nhất. Final có nhưng memory stale → update memory trước chapter mới. Không fake report lịch sử.

## 10. Completion Gate

Chapter native v3.1 cần scene plan, draft, continuity report, Story Promise review, style report, aggregate report, rewrite nếu required, final và memory current.

Batch cần requested finals + required artifacts + memory through last chapter + batch audit.

## 11. Legacy migration

Story branch không tự inherit framework. Khi sync, giữ final/canon/historical audits, không fake retroactive QC. Retired controller data có thể giữ historical nhưng không tiếp tục track.

## 12. Standard Commands

Genesis:

`Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.`

Batch:

`Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.`

Audit:

`Audit continuity, Story Promises và style fingerprint cho các chương gần nhất.`

Migration:

`Sync story này lên framework promise-only hiện tại, không retcon final.`
