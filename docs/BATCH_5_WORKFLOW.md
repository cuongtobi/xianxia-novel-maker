# Batch 5 Chapters Workflow

## 1. Mục tiêu

Batch mặc định của pipeline là **5 chương**.

Lệnh chuẩn:

> Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.

Batch chỉ là đơn vị điều phối + audit. Mỗi chương vẫn là một transaction độc lập và bắt buộc chạy tuần tự.

## 2. Chapter transaction

Với mỗi chương N:

```text
assemble context
→ scene plan
→ draft
→ Continuity Auditor
→ Reader Retention Editor
→ Style Fingerprint Auditor
→ aggregate quality gate
→ rewrite
→ critical re-QC
→ Rolling 3-Chapter Audit nếu N % 3 == 0
→ final
→ story memory update
→ Reader Experience Memory update
```

Không được plan/draft cả 5 chương trước rồi mới QC hoặc update memory.

## 3. Batch range

Batch mặc định có 5 chương:

- 1–5
- 6–10
- 11–15
- 16–20
- ...

Nếu user chỉ định range khác, dùng range user yêu cầu. Batch size 5 là default, không phải giới hạn cứng cho lệnh đặc biệt.

## 4. Preflight

Trước chương đầu batch:

1. xác nhận repo + `story/<slug>`;
2. đọc `AGENTS.md`;
3. đọc manifest và xác nhận `pipeline.batch_size: 5` nếu story đã sync framework;
4. đọc seed + ba bible;
5. đọc Story Promises trong master outline;
6. đọc arc hiện tại;
7. đọc `memory/current_state.md`;
8. đọc `memory/reader_experience.md`;
9. đọc ledgers liên quan;
10. đọc summaries gần nhất;
11. đọc full final gần nhất;
12. đọc thêm 2–3 full final nếu cần kiểm repetition/style;
13. verify batch audit trước tồn tại nếu range trước đã hoàn tất;
14. xác định start/end chapter của 5 chương tiếp theo.

Preflight phải biết:

- core Story Promise + last PAY/drought;
- recent Narrative Engines;
- recent dialogue geometries;
- recent ending shapes;
- recent rhetorical tics;
- last Xianxia Experience;
- last Emotional Residue;
- reader appetite/payoff debt;
- cultivation/power constraints;
- active deadlines/threads;
- character drift/human irrationality risks.

## 5. Story Promise Controller

Mỗi chapter đánh dấu promise là:

- `UNTOUCHED`;
- `ADVANCE`;
- `PAY`.

`ADVANCE ≠ PAY`.

Nếu 2–3 chapter liên tiếp không PAY bất kỳ core promise nào, Reader Retention Editor phải cảnh báo. Nếu cùng lúc các chapter chủ yếu là setup/administration/logistics, có thể nâng thành `MAJOR`.

Trong batch 5, ít nhất phải nhìn rõ promise nào đang được trả, promise nào đang tạo debt. Không ép fake payoff chỉ để đủ quota.

## 6. Narrative Engine Controller

Theo dõi primary/secondary engine, ví dụ:

- Q&A meeting
- audit
- negotiation
- hypothesis-test
- training calibration
- chase
- reveal
- ritual
- domestic
- combat
- grief
- wonder
- investigation
- survival task
- repair/build
- travel discovery
- aftermath
- rescue
- moral choice
- competition

Hard warning toàn cục vẫn giữ:

**Trong rolling window 4 chapter, 3/4 cùng primary engine = MAJOR pacing risk.**

Batch boundary không reset rule này. Ví dụ Ch.4–7 vẫn phải được xét cùng nhau dù cắt qua hai batch.

## 7. Scene planning — không over-plan

Planner xác định chapter-level:

- primary/secondary Narrative Engine;
- Story Promise target;
- POV + knowledge boundary;
- Xianxia Experience target nếu organic;
- Emotional movement nếu có;
- human irrationality/blind spot nếu relevant;
- ending shape.

Conflict/transaction scene có thể dùng goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene không bắt buộc đủ các ô đó; chỉ cần focal tension/curiosity, sensory anchor, knowledge boundary và movement/residue có ý nghĩa.

## 8. Three-mode QC

Mỗi chapter trong v2 enforcement window phải có:

- `continuity_report.md`;
- `reader_retention_report.md`;
- `style_fingerprint_report.md`;
- `quality_report.md` aggregate.

Không aggregate PASS nếu một reviewer còn BLOCKER/MAJOR.

### Continuity Auditor

Canon, timeline, geography, cultivation/power, technique/item, injury/fatigue, knowledge, relationship/faction, POV boundary, hard DNA/state contradiction.

### Reader Retention Editor

Story Promise PAY/drought, Narrative Engine, drag, agency, costly mistake, Xianxia Experience, Emotional Residue, ending/reason-to-continue.

### Style Fingerprint Auditor

Rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph/sentence shape, dialogue sameness, positive prose texture, calibration drift.

## 9. Rolling 3-Chapter Audit

Vẫn chạy **trước final mọi chapter chia hết cho 3**:

`3, 6, 9, 12, 15, 18...`

Đọc full final N-2, final N-1 và rewrite candidate N.

Batch size 5 không thay đổi cadence này.

Nếu audit phát hiện MAJOR repetition/drought ở candidate N, rewrite N rồi rerun reviewer/aggregate/rolling audit cần thiết trước final.

## 10. Xianxia Experience + Emotional Residue

Theo dõi xuyên batch:

### Xianxia Experience

- cultivation payoff;
- wonder/awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- dao/cultivation insight có consequence;
- magical craft;
- world-scale glimpse.

### Emotional Residue

Trong rolling 3–5 chapter cần có thay đổi có bằng chứng về một hoặc nhiều:

- emotional state;
- relationship meaning;
- self-image;
- attachment/grief/joy/shame/fear;
- object/memory meaning;
- costly mistake scar.

Không tạo melodrama giả để tick checklist.

## 11. Dynamic outline adaptation

Sau mỗi final + memory update:

- kiểm beat kế tiếp còn hợp state mới không;
- không ép nhân vật quay lại plan cũ;
- cập nhật future beat chưa final nếu cần;
- cập nhật Promise PAY windows;
- cập nhật Narrative Engine distribution;
- cập nhật Xianxia/Emotional debt;
- ghi revision log khi deviation đáng kể.

Nếu arc kết thúc giữa batch 5, phải tạo/đọc arc tiếp theo trước chapter vượt boundary. Không kéo/kết arc chỉ để khớp batch.

## 12. End-of-Batch Audit

Sau chapter thứ 5 của requested batch, tạo:

`stories/<slug>/chapters/batch_NNNN_NNNN_audit.md`

Ví dụ:

- `batch_0001_0005_audit.md`
- `batch_0006_0010_audit.md`
- `batch_0011_0015_audit.md`

Audit dùng `templates/batch_audit.template.md` và kiểm:

- artifact completion;
- arc progress;
- Story Promise ADVANCE/PAY/drought;
- Narrative Engine distribution, kể cả rolling window cắt batch boundary;
- Xianxia Experience;
- Emotional Residue;
- continuity;
- character agency/human irrationality;
- cultivation/power/resource economy;
- style fingerprints;
- setup/payoff/threads;
- Reader Experience Memory consistency;
- next-batch handoff.

## 13. Completion gate

Batch 5 chỉ được báo `PASS/READY` khi:

- đủ 5 final theo requested range, trừ khi user yêu cầu range khác hoặc truyện kết thúc;
- mỗi chapter trong enforcement window đủ artifact QC;
- rolling audit tồn tại ở các chapter đến hạn;
- story memory phản ánh chapter cuối;
- `memory/reader_experience.md` phản ánh chapter cuối;
- batch audit tồn tại;
- không còn BLOCKER/MAJOR chưa xử lý;
- next-batch handoff rõ.

Thiếu bất kỳ artifact bắt buộc nào → `INCOMPLETE`.

## 14. Legacy / batch-size migration

Các story cũ có batch 10 không cần xóa hoặc chia lại audit lịch sử.

Ví dụ `batch_0001_0010_audit.md` cũ vẫn hợp lệ historical checkpoint.

Khi sync sang batch 5:

- đặt `pipeline.batch_size: 5`;
- không retroactively tạo batch 1–5 và 6–10 nếu 1–10 đã có audit hợp lệ;
- batch kế tiếp bắt đầu tại `next_chapter` hiện tại và lấy 5 chapter;
- ví dụ story đã final Ch.10 → batch mới là Ch.11–15;
- nếu legacy range đã final nhưng chưa từng có audit, tạo migration baseline theo `docs/FRAMEWORK_V2_MIGRATION.md` trước resume.

## 15. Resume ở chat mới

Đọc tối thiểu:

1. `AGENTS.md`;
2. `docs/BATCH_5_WORKFLOW.md`;
3. manifest;
4. seed;
5. current state;
6. reader experience;
7. batch audit gần nhất;
8. arc hiện tại;
9. bible/ledgers liên quan;
10. recent summaries/final.

Lệnh ngắn hợp lệ:

> Tiếp tục branch story/<slug> và viết batch 5 chương tiếp theo đúng pipeline.
