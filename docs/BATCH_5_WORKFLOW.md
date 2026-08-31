# Batch 5 Chapters Workflow — Promise-Only

## 1. Mục tiêu

Batch mặc định = **5 chương**. Mỗi chương là một transaction độc lập và chạy tuần tự.

Controller duy nhất của framework: **Story Promise Controller**.

Đọc bắt buộc:

- `AGENTS.md`;
- `docs/READER_EXPERIENCE_SYSTEM.md`;
- `docs/REFERENCE_STYLE_SYSTEM.md` nếu story bật Reference Style.

Không đọc/chạy các controller v3 đã retire.

## 2. Chapter transaction

```text
assemble context
→ scene plan
→ draft
→ Continuity Auditor
→ Story Promise Reviewer
→ Style Fingerprint Auditor
→ aggregate quality gate
→ rewrite if needed
→ critical re-QC
→ final
→ story memory update
→ promise memory update
```

Không plan/draft cả 5 trước rồi mới QC/memory.

## 3. Preflight

Trước chapter đầu batch:

1. xác nhận repo + branch + slug;
2. đọc `AGENTS.md`;
3. đọc manifest;
4. verify `batch_size: 5`;
5. đọc seed + bibles;
6. đọc 3–5 Story Promises trong master outline;
7. đọc arc hiện tại + planned PAY windows;
8. đọc `memory/current_state.md`;
9. đọc `memory/reader_experience.md`;
10. đọc ledgers/summaries/final gần nhất cần thiết;
11. verify previous batch audit nếu range trước đã hoàn tất;
12. xác định start/end range.

Preflight chỉ cần biết về controller:

- core promises;
- last PAY/magnitude;
- pay drought;
- planned payoff window.

Các dữ liệu continuity/style khác được đọc vì công việc viết/QC, không phải controller metric.

## 4. Story Promise Controller

Per chapter, với từng promise ghi:

- `UNTOUCHED`;
- `ADVANCE`;
- `PAY_MINOR`;
- `PAY_MAJOR`;
- `PAY_ARC`.

`ADVANCE ≠ PAY`.

PAY cần có kết quả/reveal/trải nghiệm/thay đổi trạng thái hữu hình. Setup hoặc lời hứa tương lai không được tự tính PAY.

Theo dõi:

- `last_touch_chapter`;
- `last_pay_chapter`;
- `last_major_pay_chapter`;
- `pay_drought`;
- `drought_warning`;
- next planned payoff window.

Nếu vượt drought warning, Story Promise Reviewer tạo finding. Không sửa bằng fake payoff; nếu chapter hiện tại không phù hợp thì điều chỉnh arc/future beat.

## 5. Scene plan

Planner chỉ cần:

- chapter objective;
- POV/time/place/cast;
- start state;
- conflict/pressure;
- key beats/turn;
- important choice/consequence;
- Story Promise target + intended payoff nếu có;
- end state;
- continuity constraints;
- style constraints;
- hook nếu organic.

Không lập Engine/Geometry/Heat/Xianxia/Competence/Aspiration/Binge target.

## 6. Draft

Writer viết theo scene plan, Character DNA, canon và Style Bible.

Writer không được nhìn hoặc tự tối ưu rolling metrics đã retire. Chất tiên hiệp, nhịp, cảm xúc, wonder, sai lầm và competence phải đến tự nhiên từ premise/world/character/scene.

## 7. QC

### Continuity Auditor

Kiểm canon, timeline, power/cultivation, knowledge, injury, item, relationship, POV.

### Story Promise Reviewer

Kiểm:

- promise target có được chạm thật không;
- ADVANCE/PAY classification có đúng không;
- magnitude có bị phóng đại không;
- false pay;
- drought;
- promise có bị đổi nghĩa so với contract không.

### Style Fingerprint Auditor

Kiểm AI-like fingerprints, câu/đoạn, rhetorical tics, dialogue sameness, exposition, house style và reference drift/overfit nếu bật.

## 8. Aggregate gate

`quality_report.md` tổng hợp ba reviewer.

- continuity BLOCKER/MAJOR → không final;
- Story Promise MAJOR → re-plan/rewrite nếu finding liên quan chapter hiện tại, hoặc cập nhật future plan nếu là drought cần payoff sắp tới;
- style MAJOR → rewrite;
- không có gate cho controller đã retire.

## 9. Rewrite discipline

Ưu tiên:

`CUT > COMPRESS > REORDER > REPLACE > ADD`.

Không thêm lore/mechanism/scene chỉ để làm chapter “có vẻ đạt metric”.

Mặc định rewrite không làm final dài hơn draft quá khoảng **25%**. Nếu cần thay cấu trúc lớn, tạo scene plan/draft mới rồi QC lại.

## 10. Final + memory

Sau PASS:

1. tạo `final/Chương X: <title>.txt`;
2. update story memory/ledgers;
3. update chapter summary;
4. update `memory/reader_experience.md` với Story Promise states;
5. update manifest `last_finalized_chapter` + `next_chapter`.

Không sang chapter kế trước khi memory cập nhật.

## 11. Batch audit

Sau chapter thứ 5 của requested range tạo:

`chapters/batch_NNNN_NNNN_audit.md`

Audit gồm:

- 5 finals/artifacts có đủ không;
- memory có current không;
- continuity handoff;
- Story Promise table và drought;
- payoff distribution;
- style issues xuyên batch nếu có;
- next-batch promise priorities;
- next chapter/arc handoff.

Không chạy rolling 3 audit hoặc controller khác.

## 12. Completion gate

Batch READY khi:

- đủ requested finals;
- per-chapter required artifacts đầy đủ;
- memory current through last chapter;
- batch audit tồn tại;
- không còn BLOCKER/MAJOR chưa xử lý;
- next-batch handoff rõ.

Thiếu → `INCOMPLETE`.
