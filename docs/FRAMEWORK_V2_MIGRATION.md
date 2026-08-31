# Legacy Story Migration → Promise-Only Framework

Áp dụng cho story branch cũ hoặc story từng dùng batch 10/controller cũ.

## Principles

1. Final đã phát hành là canon.
2. Không fake retroactive pre-final QC.
3. Historical batch/rolling/controller artifacts được giữ làm lịch sử nhưng không tiếp tục enforced.
4. Chỉ backfill Story Promise baseline nếu story chưa có.
5. Default batch mới = 5.

## Migration

1. xác định `legacy_cutoff_chapter`;
2. giữ nguyên final + canon + historical audits;
3. khóa/backfill 3–5 Story Promises từ premise/finals;
4. tạo hoặc rút gọn `memory/reader_experience.md` thành Promise runtime state;
5. cập nhật future arc chỉ với Promise PAY windows cần thiết;
6. cập nhật manifest sang v3.1 promise-only;
7. tiếp tục từ `next_chapter`.

## Manifest target

```yaml
pipeline:
  version: "3.1"
  batch_size: 5
  controllers:
    - story_promise
  qc_modes:
    - continuity
    - story_promise
    - style_fingerprint
```

Xóa/ignore active flags liên quan retention_v3, xianxia_density, rolling audit và controller đã retire.

## What not to fake

Không tạo giả:

- historical per-chapter QC;
- historical rolling audits;
- historical controller scores;
- fake split batch audits.

Nếu story có `batch_0001_0010_audit.md`, giữ nguyên. Nếu final đến Ch.10 thì next default batch là Ch.11–15.
