# Framework v2.1 Migration — Legacy Story Branches

Tài liệu này áp dụng cho story branch được tạo trước pipeline v2/v2.1 hoặc đang dùng batch size cũ.

Mục tiêu: migrate **không retcon final, không fake historical QC và không phá checkpoint cũ**.

## 1. Principles

1. Final đã phát hành là canon.
2. Không tạo retroactive `continuity_report.md`, `reader_retention_report.md`, `style_fingerprint_report.md` rồi giả rằng chúng đã chạy pre-final.
3. Có thể tạo migration baseline từ final thật.
4. Story Promises và Reader Experience có thể backfill như review hậu kỳ.
5. v2 per-chapter gate chỉ enforced từ chapter sau legacy cutoff.
6. Batch-size migration 10 → 5 không làm invalid historical batch audits.

## 2. Migration Inputs

Đọc:

- manifest;
- seed;
- all bibles;
- master outline;
- current arc;
- all memory;
- recent batch audit nếu có;
- recent/full finals đủ để dựng baseline;
- chapter artifact tree.

## 3. Legacy Cutoff

```text
legacy_cutoff_chapter = last finalized chapter before migration
v2_enforced_from_chapter = legacy_cutoff_chapter + 1
```

Ví dụ đã có Ch.1–10:

```text
legacy_cutoff_chapter: 10
v2_enforced_from_chapter: 11
```

## 4. Backfill Legitimate Baselines

### Story Promise baseline

Cập nhật master outline với 3–5 promises:

- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation.

Audit final cũ để ghi historical ADVANCE/PAY.

### Reader Experience baseline

Tạo/update:

`memory/reader_experience.md`

Ghi:

- last major payoff;
- promise history gần nhất;
- recent Narrative Engines;
- dialogue geometry;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes;
- reader appetite/payoff debt.

### Arc enrichment

Cho future chapters chưa final, bổ sung:

- Promise PAY windows;
- Narrative Engine distribution;
- Xianxia targets;
- Emotional Residue plan;
- costly mistake opportunities.

Không rewrite planned history của chapters đã final như thể chưa xảy ra.

## 5. Missing Legacy Batch Audit

Nếu completed legacy range chưa có batch audit, tạo audit hậu kỳ với:

```text
Audit mode: LEGACY_MIGRATION_BASELINE
```

Không được ghi rằng v2 per-chapter QC đã PASS nếu những report đó chưa từng tồn tại.

Ví dụ story đã final Ch.1–10 nhưng thiếu audit:

- có thể tạo `batch_0001_0010_audit.md` migration baseline;
- đây là historical audit hợp lệ;
- không cần chia thành 1–5 và 6–10 chỉ vì framework mới dùng batch 5.

## 6. Batch Size Migration: 10 → 5

Khi sync story sang v2.1:

```yaml
pipeline:
  version: "2.1"
  batch_size: 5
  batch_workflow: "docs/BATCH_5_WORKFLOW.md"

migration:
  prior_batch_size: 10
  batch_size_migrated_at_chapter: <legacy_cutoff>
```

Rules:

- giữ nguyên historical audit filenames/ranges;
- không fake retroactive split audit;
- `next_batch_start` = current `next_chapter`;
- next default batch gồm 5 chapters;
- ví dụ final through Ch.10 → next batch Ch.11–15;
- nếu final through Ch.17 → next batch Ch.18–22; không cần chờ mốc chia hết cho 5;
- user explicit range vẫn override default cho lần chạy đó.

## 7. Rolling Audit Compatibility

Rolling 3-Chapter Audit chạy theo chapter number toàn cục:

`3, 6, 9, 12, 15...`

Không reset khi đổi batch size.

Nếu migration enforcement bắt đầu Ch.11, rolling audit đầu tiên bắt buộc trong enforcement window là Ch.12.

Không backfill fake rolling audits cho Ch.3/6/9 nếu chúng chưa tồn tại pre-final.

## 8. What Must NOT Be Faked

Không tạo giả lịch sử:

- per-chapter 3-mode QC;
- rolling audit pre-final;
- reader memory timestamp giả;
- batch 1–5/6–10 giả nếu 1–10 historical checkpoint đã đủ.

Có thể tạo **migration review** nhưng phải label rõ hậu kỳ.

## 9. Manifest Update

Migration phải cập nhật tối thiểu:

- pipeline version;
- batch size 5;
- batch workflow path;
- legacy cutoff;
- v2 enforced from chapter;
- reader experience initialized;
- Story Promise initialized;
- next chapter;
- next batch start;
- migration notes.

## 10. Resume Gate

Trước production mới, verify:

- migration baseline exists;
- Reader Experience baseline exists;
- Story Promises locked;
- current arc enriched for future chapters;
- missing legacy batch audit repaired if needed;
- manifest says `batch_size: 5`;
- `next_chapter` accurate.

Then full v2.1 gate applies from `v2_enforced_from_chapter`.

## 11. Example

Story state:

```text
Finals: Ch.1–10
Historical audit: batch_0001_0010_audit.md
Legacy v2.0 batch size: 10
```

After migration:

```text
legacy_cutoff: 10
v2_enforced_from: 11
batch_size: 5
next_batch: Ch.11–15
```

Keep `batch_0001_0010_audit.md` unchanged as historical checkpoint.

After Ch.15 create:

`batch_0011_0015_audit.md`
