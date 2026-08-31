# ChatGPT Web + GitHub Protocol — Atomic Combined QC

## 1. Defaults

Framework branch: `main`.
Story branch: `story/<slug>`.
Default batch: 5 chapters.
Controller duy nhất: Story Promise Controller.

Native framework:

```yaml
pipeline:
  version: "3.2"
  batch_size: 5
  controllers:
    - story_promise
  qc_mode: combined_qc
  chapter_transaction: atomic_git_commit
  rewrite_mode: on_qc_failure
```

## 2. New story

1. resolve slug;
2. create story branch from `main`;
3. build seed/bibles/master outline/arc/memory;
4. lock 3–5 Story Promises;
5. initialize promise memory;
6. mark READY_TO_WRITE.

## 3. Read protocol

Đọc exact story branch. Không dùng chat memory thay GitHub source of truth.

Trước chapter đọc manifest, seed, current state, promise memory, arc, Story Promises, bibles/ledgers liên quan, recent summaries/final khi cần.

## 4. Atomic chapter protocol

Không persist intermediate artifacts trong quá trình xử lý.

In-session:

1. scene plan;
2. draft;
3. combined QC;
4. rewrite only if QC requires;
5. final;
6. calculate memory/ledger/summary/manifest updates;
7. prepare batch audit nếu đây là chapter cuối batch.

Persist once:

1. read chapter-start branch HEAD/tree;
2. create blobs for every new/changed file;
3. create one tree from chapter-start base tree;
4. create one commit with chapter-start HEAD as parent;
5. update story branch ref once;
6. verify HEAD.

## 5. Required persisted files

Per chapter:

```text
chapters/NNNN/scene_plan.md
chapters/NNNN/draft.txt
chapters/NNNN/combined_qc_report.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

Nếu chapter đóng requested batch, cùng commit thêm:

`chapters/batch_NNNN_NNNN_audit.md`.

Không tạo active:

- continuity_report.md
- reader_retention_report.md
- style_fingerprint_report.md
- quality_report.md
- rewrite.txt

## 6. Combined QC

`combined_qc_report.md` gồm:

- Continuity;
- Story Promise;
- Style;
- Decision;
- Rewrite Recheck nếu có.

`PASS` → draft trở thành final nguyên văn.

`REWRITE_REQUIRED` → sửa trong working memory, quick recheck và chỉ persist candidate cuối đã pass.

## 7. State machine

```text
READY_TO_WRITE
→ WORKING_IN_MEMORY
→ QC_PASS
→ ATOMIC_COMMIT_PREPARED
→ BRANCH_REF_UPDATED
→ CHAPTER_COMPLETE
→ READY_TO_WRITE
```

Intermediate in-memory stages không phải persistent story state.

## 8. Resume rules

Nếu branch chưa có commit chapter N hoàn chỉnh, coi N chưa hoàn tất và chạy lại transaction từ source of truth hiện tại.

Không resume dựa trên orphan blob hoặc verbal statement.

Nếu final tồn tại nhưng manifest/memory không cùng commit/state, transaction chưa hợp lệ và phải repair trước chapter tiếp.

## 9. Batch protocol

`Viết batch tiếp theo` = 5 chapters nếu user không override.

Chạy 5 atomic chapter commits tuần tự. Không dừng ở Ch.3. Chỉ tạo batch audit ở chapter cuối requested range.

## 10. Completion gate

Chapter complete khi branch HEAD history chứa atomic chapter commit với scene plan, draft, combined QC PASS, final và current memory/manifest.

Batch complete khi đủ 5 chapter commits + batch audit trong commit cuối.
