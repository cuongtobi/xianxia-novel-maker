# Legacy Story Migration → Framework v3.2

Áp dụng cho story branch cũ, batch-10 story hoặc story dùng controller/QC architecture cũ.

## Principles

1. Final đã phát hành là canon.
2. Không fake retroactive pre-final QC.
3. Historical batch/rolling/controller/separate-QC artifacts được giữ làm lịch sử.
4. Chỉ backfill Story Promise baseline nếu thiếu.
5. Default batch mới = 5.
6. Future chapters dùng Combined QC + atomic chapter commit.

## Migration

1. xác định `legacy_cutoff_chapter`;
2. giữ nguyên final + canon + historical audits;
3. khóa/backfill 3–5 Story Promises;
4. rút `memory/reader_experience.md` về Promise runtime state;
5. cập nhật future arc với Promise PAY windows;
6. cập nhật manifest sang v3.2;
7. set `qc_mode: combined_qc`;
8. set `chapter_transaction: atomic_git_commit`;
9. set `rewrite_mode: on_qc_failure` và `persist_rewrite_artifact: false`;
10. tiếp tục từ exact `next_chapter`.

## Manifest target

```yaml
pipeline:
  version: "3.2"
  batch_size: 5
  controllers:
    - story_promise
  qc_mode: "combined_qc"
  chapter_transaction: "atomic_git_commit"
  rewrite_mode: "on_qc_failure"
  persist_rewrite_artifact: false
```

## Do not fake

Không tạo giả historical:

- Combined QC;
- per-chapter QC cũ;
- rolling audits;
- controller scores;
- split batch audits.

Nếu story có `batch_0001_0010_audit.md`, giữ nguyên. Nếu final đến Ch.10 thì next default batch là Ch.11–15.
