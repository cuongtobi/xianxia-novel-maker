# Framework v3 Migration

Dùng cho story branch đã có final/memory trước khi `Retention Controllers v3` được thêm vào framework.

Mục tiêu: áp dụng 6 controller mới từ chapter tiếp theo mà **không fake retroactive per-chapter QC**.

Đọc cùng:

- `AGENTS.md`
- `docs/RETENTION_CONTROLLERS_V3.md`
- `docs/BATCH_5_WORKFLOW.md`

---

# 1. Nguyên tắc

- Final + canon ledger vẫn là source of truth.
- Không rewrite lịch sử chỉ để làm đẹp metric v3.
- Không tạo giả `reader_retention_report.md` v3 cho chapter đã final nếu trước đó chưa chạy v3.
- Có thể dựng **v3 migration baseline** từ 3–5 recent finals thật + existing reader memory.
- Historical batch audit cũ vẫn hợp lệ như checkpoint của version cũ.
- V3 enforcement bắt đầu từ `next_chapter` trừ khi user explicit yêu cầu re-audit/rewrite lịch sử.

---

# 2. Sync framework files

Story branch cần có version mới của tối thiểu:

- `AGENTS.md`
- `docs/RETENTION_CONTROLLERS_V3.md`
- `docs/BATCH_5_WORKFLOW.md`
- `prompts/PIPELINE_PROMPTS.md`
- `templates/chapter_scene.template.md`
- `templates/reader_retention_report.template.md`
- `templates/quality_report.template.md`
- `templates/rolling_3_chapter_audit.template.md`
- `templates/batch_audit.template.md`
- `templates/reader_experience.template.md`
- `templates/master_outline.template.md`
- `templates/arc_outline.template.md`

Không ghi story artifact lên `main`.

---

# 3. Manifest migration

Update story `manifest.yaml`:

```yaml
pipeline:
  version: "3.0"
  batch_size: 5
  retention_spec: "docs/RETENTION_CONTROLLERS_V3.md"
  retention_v3_required: true
  retention_controllers:
    dramatic_geometry: true
    payoff_magnitude: true
    competence_friction: true
    aspiration: true
    heat_curve: true
    binge_test: true

completion_gate:
  require_reader_reward_gate: true
  v3_enforced_from_chapter: <next_chapter>

migration:
  from_version: "<old>"
  migrated_to: "3.0"
  legacy_cutoff_chapter: <last_finalized_chapter>
  v3_enforced_from_chapter: <next_chapter>
  migration_baseline: "memory/reader_experience.md"
```

Giữ các field lịch sử khác đang có.

---

# 4. Build v3 Reader Experience baseline

Đọc full 3–5 recent finals, existing batch audit và `memory/reader_experience.md`.

Không gọi đây là retroactive official QC. Ghi rõ:

`Migration baseline inferred from existing finals; per-chapter v3 QC begins at Ch.N.`

Baseline cần đủ để chapter tiếp theo tính rolling rules.

## 4.1 Payoff Magnitude

Với recent finals, chỉ classify mức đủ chắc:

- UNTOUCHED
- ADVANCE
- PAY_MINOR
- PAY_MAJOR
- PAY_ARC

Nếu không chắc magnitude, chọn mức thấp hơn và ghi NOTE.

Tính:

- `pay_drought`
- `major_payoff_debt`

Không upgrade old PAY chỉ để metric đẹp.

## 4.2 Dramatic Geometry

Cho 3–5 recent finals, ghi short signature:

- pressure source
- decision locus
- movement mode
- information flow
- opposition
- resolution
- reversal
- kinetic level

Mục tiêu là bắt repetition khi viết chapter mới, không phán xét lại final cũ.

## 4.3 Competence Friction

Classify competence conversions đủ rõ:

`CLEAN_WIN / COSTLY_WIN / PARTIAL / WRONG_MODEL / DEPENDENT_ON_OTHER / FAILURE / NO_CONVERSION`

Nếu một chapter có nhiều conversion, chỉ ghi conversion chi phối trải nghiệm.

## 4.4 Aspiration

Ghi recent:

- object of desire
- why desirable
- proof/image
- status

Tách khỏi scarcity.

## 4.5 Heat

Ghi `peak_heat` H0–H3 cho recent finals đủ để rolling 5 tiếp tục.

Không inflate quiet chapter thành H2 chỉ để pass.

## 4.6 Binge baseline

Có thể ghi migration estimate:

- concrete best reward moment
- intrinsic value without ending hook: YES/WEAK/NO

Đây là baseline, không phải thay thế official v3 Reader Retention Report.

---

# 5. Arc/outline migration

Không rewrite toàn bộ outline nếu không cần.

Update phần future beats chưa final:

- Story Promise target → thêm magnitude;
- thêm Dramatic Geometry shorthand/map;
- thêm competence-friction opportunities;
- thêm aspiration beats;
- thêm Heat Curve;
- thêm intrinsic reward/Binge risk cho bridge chapters.

Past beat rows có thể giữ nguyên để bảo toàn history.

Nếu planned future sequence tạo violation v3 rõ ràng, sửa future beats trước khi viết.

---

# 6. First v3 chapter

Trước chapter đầu enforcement:

1. đọc migration baseline;
2. tính rolling engine/geometry;
3. tính competence clean-win streak;
4. tính aspiration drought;
5. tính rolling heat;
6. tính payoff + major payoff debt;
7. scene plan phải pre-check Binge Test;
8. chạy full v3 Reader Retention QC;
9. aggregate phải có Technical Gate + Reader-Reward Gate.

Nếu N%3==0, Rolling 3-Chapter Audit được phép dùng hai final legacy + candidate v3, nhưng phải ghi rõ boundary version. Không fake old reviewer artifacts.

---

# 7. Historical batch compatibility

Ví dụ story đã có:

`batch_0001_0005_audit.md` từ v2.1.

Không cần thay thế file đó bằng v3 audit.

Sau migration, batch kế tiếp dùng v3 đầy đủ.

Nếu muốn re-audit historical batch để nghiên cứu, tạo file mới có tên rõ như:

`batch_0001_0005_v3_reaudit.md`

và ghi `diagnostic only`, không overwrite historical checkpoint.

---

# 8. Completion gate

Migration chỉ hoàn tất khi:

- framework files v3 đã sync;
- manifest version/flags đã update;
- reader-experience migration baseline tồn tại;
- future arc beats đủ dữ liệu v3 để plan chapter tiếp;
- `v3_enforced_from_chapter` rõ;
- không có giả lập retroactive QC.

Sau đó mới viết chapter tiếp theo theo BATCH_5_WORKFLOW v3.