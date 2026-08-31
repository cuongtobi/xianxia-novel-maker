# Framework v3.2 Migration — Atomic Combined QC

v3.2 giữ kiến trúc promise-only của v3.1 nhưng tối ưu transaction để Batch 5 nhẹ hơn.

## Changes

1. Controller active duy nhất vẫn là Story Promise Controller.
2. Ba report QC + aggregate được thay bằng một `combined_qc_report.md`.
3. `rewrite.txt` không còn là artifact mặc định.
4. Rewrite chỉ chạy khi Combined QC có BLOCKER/MAJOR cần sửa.
5. Mỗi chapter persist bằng one Git tree/commit + one branch ref update.
6. Batch audit được đưa vào commit của chapter cuối requested batch.
7. Không có rolling audit/checkpoint Ch.3.

## Retired active artifacts

Không tạo mới:

- `continuity_report.md`
- `reader_retention_report.md`
- `style_fingerprint_report.md`
- `quality_report.md`
- `rewrite.txt`
- `rolling_3_chapter_audit.md`

Historical copies được giữ nguyên trên story cũ.

## Migration steps for a story branch

1. giữ nguyên canon/finals/history;
2. update manifest `version: 3.2`;
3. set `qc_mode: combined_qc`;
4. set `chapter_transaction: atomic_git_commit`;
5. set `rewrite_mode: on_qc_failure`;
6. set `persist_rewrite_artifact: false`;
7. giữ `controllers: [story_promise]`;
8. bỏ requirement separate QC/rolling audit;
9. từ `next_chapter` trở đi dùng BATCH_5_WORKFLOW v3.2;
10. không backfill Combined QC cho final cũ như thể nó đã chạy pre-final.

## Atomicity rule

Mỗi future chapter phải được chuẩn bị đầy đủ trước khi write GitHub. Tất cả chapter artifacts, final, changed memory và manifest nằm trong cùng một commit.

Nếu lỗi trước branch `update_ref`, chapter chưa complete và có thể chạy lại từ HEAD cũ.

## Compatibility

Historical report files có thể tồn tại nhưng không phải completion requirement của v3.2.

Batch audit cũ vẫn có giá trị historical. Không cần rewrite/chia lại audit cũ.
