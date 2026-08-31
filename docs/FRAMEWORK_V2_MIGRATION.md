# Framework v2 Migration — Legacy Story Branches

Tài liệu này áp dụng cho story branch được tạo trước khi pipeline v2 có:

- Story Promise Controller;
- Reader Experience Memory;
- split 3-mode QC;
- Rolling 3-Chapter Audit;
- Narrative Engine gate.

Mục tiêu: đưa truyện cũ sang v2 **mà không giả mạo artifact QC quá khứ và không retcon final**.

## 1. Nguyên tắc

1. Final đã phát hành là canon.
2. Không tạo retroactive `continuity_report.md`, `reader_retention_report.md`, `style_fingerprint_report.md` cho chapter cũ rồi giả vờ chúng đã chạy trước final.
3. Có thể audit lại chapter cũ để tạo **migration baseline** và batch audit vì đó là review hậu kỳ, không phải release gate giả.
4. Reader Experience Memory có thể được dựng từ final cũ.
5. Story Promises có thể được khóa từ seed/bibles/master outline hiện tại, nhưng phải ghi là migration, không giả rằng chúng đã tồn tại từ Genesis.
6. v2 per-chapter gate bắt đầu từ chapter **sau legacy cutoff**.

## 2. Migration inputs

Đọc:

- story `manifest.yaml`;
- seed;
- all bibles;
- master outline;
- current arc;
- all current memory;
- batch audit gần nhất nếu có;
- full final 10 chapter gần nhất hoặc toàn bộ final nếu truyện mới chỉ có khoảng 10 chapter;
- artifact tree chapter cũ.

## 3. Determine legacy cutoff

`legacy_cutoff_chapter = last finalized chapter trước migration`.

Ví dụ truyện đã có Ch.1–10:

```text
legacy_cutoff_chapter: 10
v2_enforced_from_chapter: 11
```

Không áp required split-QC artifacts ngược về Ch.1–10.

## 4. Backfill what is legitimate

### 4.1 Story Promise baseline

Cập nhật Master Outline:

- khóa 3–5 Story Promises;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation.

Sau đó audit finals cũ để đánh dấu historical ADVANCE/PAY.

### 4.2 Reader Experience baseline

Tạo:

`stories/<slug>/memory/reader_experience.md`

Dùng final cũ để ghi:

- last major payoff;
- promise last ADVANCE/PAY;
- recent Narrative Engines;
- dialogue geometry;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes;
- reader appetite/payoff debt.

### 4.3 Arc enrichment

Nếu arc hiện tại còn tiếp tục, bổ sung:

- Story Promise windows;
- Narrative Engine map cho **future chapters chưa final**;
- Xianxia Experience targets;
- Emotional Residue plan;
- costly mistake opportunities.

Không rewrite beat đã final thành plan mới.

### 4.4 Missing batch audit

Nếu một completed legacy range chưa có `batch_NNNN_NNNN_audit.md`, **phải tạo audit từ final hiện có trước khi resume production**.

Audit phải ghi rõ:

```text
Audit mode: LEGACY_MIGRATION_BASELINE
```

Không được ghi rằng per-chapter v2 QC đã PASS nếu các report đó không từng tồn tại.

Ví dụ branch có Ch.1–10 nhưng thiếu batch audit:

- tạo `chapters/batch_0001_0010_audit.md`;
- audit 10 final thật;
- ghi thiếu legacy QC artifacts là expected legacy state, không phải current corruption;
- dùng kết quả làm handoff Ch.11.

## 5. What must NOT be backfilled as if historical

Không tạo các file sau cho chapter cũ chỉ để thỏa gate:

- `continuity_report.md` giả lịch sử;
- `reader_retention_report.md` giả lịch sử;
- `style_fingerprint_report.md` giả lịch sử;
- `rolling_3_chapter_audit.md` với wording như đã chạy pre-final.

Nếu cần review past chapters, lưu dưới migration/batch audit wording rõ là **post-publication audit**.

## 6. Manifest migration fields

Story manifest sau migration nên có:

```yaml
pipeline:
  version: "2.0"

migration:
  from_version: "1.x"
  migrated_to: "2.0"
  legacy_cutoff_chapter: 10
  v2_enforced_from_chapter: 11
  migration_baseline: "chapters/migration_v2_baseline.md"
  legacy_batch_audits_backfilled: true
```

Với story mới tạo trực tiếp bằng v2:

```yaml
migration:
  from_version: null
  migrated_to: null
  legacy_cutoff_chapter: 0
  v2_enforced_from_chapter: 1
  migration_baseline: null
```

## 7. Migration baseline artifact

Tạo:

`stories/<slug>/chapters/migration_v2_baseline.md`

Format:

```md
# Pipeline v2 Migration Baseline

- Story:
- Migration date:
- Legacy cutoff chapter:
- v2 enforced from chapter:
- Final chapters treated as canon:
- Existing legacy batch audits:
- Backfilled batch audits:

## Story Promises
...

## Reader Experience baseline
...

## Narrative Engine risks from recent finals
...

## Xianxia Experience debt
...

## Emotional Residue state
...

## Style Fingerprint risks
...

## Required corrections starting next chapter
...
```

## 8. Completion gate after migration

Migration chỉ hoàn tất khi:

- master outline có 3–5 Story Promises;
- current/future arc có v2 reader-experience fields;
- `reader_experience.md` tồn tại và phản ánh legacy cutoff;
- missing completed-range batch audit đã được backfill;
- migration baseline tồn tại;
- manifest ghi `v2_enforced_from_chapter`;
- current_state vẫn khớp final;
- không retcon canon.

Sau đó, chapter mới đầu tiên phải chạy full v2 gate.

## 9. Existing stories in this repository

Khi user yêu cầu migrate một story cụ thể, **đọc artifact thật trước**. Không giả định số chapter hoặc missing audit chỉ từ tài liệu này.

Migration là thao tác trên story branch và chỉ thực hiện khi user yêu cầu sync/migrate story đó.