# Architecture — Atomic Promise-Only

## 1. Overview

Framework chạy trên ChatGPT Web + GitHub. GitHub giữ persistent state; ChatGPT thực thi pipeline.

Controller duy nhất: **Story Promise Controller**.

```text
Seed
→ Bibles
→ Master Outline + Story Promises
→ Arc Outline
→ Story + Promise Memory
→ Batch 5
    ├─ Ch.N atomic transaction
    ├─ Ch.N+1 atomic transaction
    ├─ ...
    └─ Ch.N+4 atomic transaction + batch audit
```

## 2. Minimal chapter transaction

```text
READ
→ PLAN
→ DRAFT
→ COMBINED QC
→ FINAL
→ MEMORY UPDATE
→ ATOMIC COMMIT
```

Persisted chapter artifacts:

- `scene_plan.md`
- `draft.txt`
- `combined_qc_report.md`
- final TXT
- memory/manifest updates

`rewrite.txt` không phải artifact mặc định. Rewrite chỉ thực hiện trong working memory khi Combined QC yêu cầu.

## 3. Combined QC

Một report duy nhất có ba phần:

- Continuity
- Story Promise
- Style

Continuity/Style là technical review. Story Promise là controller duy nhất.

## 4. Atomicity model

Mỗi chapter bắt đầu từ một branch HEAD cố định.

Toàn bộ output và memory updates được tạo trước. Sau đó GitHub write dùng:

```text
create_blob × changed files
→ create_tree(base_tree=chapter_start_tree)
→ create_commit(parent=chapter_start_HEAD)
→ update_ref once
```

Không dùng nhiều sequential `update_file` để tiến state chapter.

Nếu lỗi trước `update_ref`, branch vẫn ở chapter trước và transaction có thể chạy lại an toàn.

## 5. Rewrite behavior

Combined QC `PASS` → draft được dùng nguyên văn làm final.

Combined QC `REWRITE_REQUIRED` → sửa candidate trong working memory, quick recheck findings fail, ghi recheck vào cùng report, rồi persist final đã pass.

Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`.

## 6. Data layers

### Canon
Bibles, canon ledger, finals, Character DNA.

### Planning
Master outline, arc outline, Story Promise PAY windows.

### Runtime
Current state, timeline, characters, relationships, cultivation, inventory, factions/locations, knowledge, foreshadowing, unresolved threads, summaries.

### Promise runtime
`reader_experience.md` chỉ giữ Story Promise state/payoff/drought.

## 7. Batch 5

Batch là 5 atomic chapter commits tuần tự. Không có checkpoint chapter 3.

Batch audit được tạo sau chapter thứ 5 và đưa vào cùng commit chapter thứ 5.

## 8. Completion semantics

Chapter COMPLETE khi commit của nó đã được update vào branch và chứa:

- scene plan;
- draft;
- Combined QC PASS;
- final;
- memory/manifest current.

Batch COMPLETE khi đủ 5 commits/finals và batch audit tồn tại.

Framework tối ưu cho:

**continuity + promise delivery + prose quality + low tool overhead + recoverable atomic execution**.
