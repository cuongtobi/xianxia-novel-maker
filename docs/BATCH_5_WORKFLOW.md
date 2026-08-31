# Batch 5 Chapters Workflow

## 1. Mục tiêu

Batch mặc định của pipeline là **5 chương**.

Lệnh chuẩn:

> Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.

Batch chỉ là đơn vị điều phối + audit. Mỗi chương vẫn là một transaction độc lập và bắt buộc chạy tuần tự.

Framework v3 còn bắt buộc đọc:

- `docs/RETENTION_CONTROLLERS_V3.md`.

Core rule:

**PASS kỹ thuật ≠ PASS trải nghiệm đọc.**

## 2. Chapter transaction

Với mỗi chương N:

```text
assemble context
→ scene plan
→ draft
→ Continuity Auditor
→ Reader Retention Editor + Retention Controllers v3
→ Style Fingerprint Auditor
→ aggregate quality gate: Technical Gate + Reader-Reward Gate
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
3. đọc `docs/RETENTION_CONTROLLERS_V3.md`;
4. đọc manifest và xác nhận `pipeline.batch_size: 5` + retention v3 nếu story đã sync framework;
5. đọc seed + ba bible;
6. đọc Story Promises trong master outline;
7. đọc arc hiện tại;
8. đọc `memory/current_state.md`;
9. đọc `memory/reader_experience.md`;
10. đọc ledgers liên quan;
11. đọc summaries gần nhất;
12. đọc full final gần nhất;
13. đọc thêm 2–3 full final nếu cần kiểm repetition/style/geometry;
14. verify batch audit trước tồn tại nếu range trước đã hoàn tất;
15. xác định start/end chapter của 5 chương tiếp theo.

Preflight phải biết:

- core Story Promise + last PAY magnitude;
- `pay_drought` + `major_payoff_debt`;
- recent Narrative Engines;
- recent Dramatic Geometry signatures;
- recent competence outcomes;
- recent aspiration beats;
- recent heat sequence + last H2+;
- recent Binge Test results;
- recent dialogue geometries;
- recent ending shapes;
- recent rhetorical tics;
- last Xianxia Experience;
- last Emotional Residue;
- reader appetite/payoff debt;
- cultivation/power constraints;
- active deadlines/threads;
- character drift/human irrationality risks.

## 5. Story Promise Controller + Payoff Magnitude

Mỗi chapter đánh dấu promise là:

- `UNTOUCHED`;
- `ADVANCE`;
- `PAY_MINOR`;
- `PAY_MAJOR`;
- `PAY_ARC`.

`ADVANCE ≠ PAY`.

Reward score:

- `PAY_MINOR = 1`;
- `PAY_MAJOR = 2`;
- `PAY_ARC = 3`.

Theo dõi hai debt riêng:

- `pay_drought` = số chapter từ bất kỳ PAY thật gần nhất;
- `major_payoff_debt` = số chapter từ PAY_MAJOR/PAY_ARC gần nhất cho core promise.

Nếu 2–3 chapter liên tiếp không PAY bất kỳ core promise nào, Reader Retention Editor phải cảnh báo. Nếu cùng lúc các chapter chủ yếu là setup/administration/logistics, có thể nâng thành `MAJOR`.

Chuỗi PAY_MINOR không được dùng để giả rằng core promise đã được trả đủ nếu major payoff debt vượt planned window.

Trong batch 5, phải nhìn rõ:

- promise nào đang được trả;
- payoff ở mức nào;
- promise nào đang tạo debt;
- có batch nào toàn PAY_MINOR nhưng thiếu cảm giác “đã” hay không.

Không ép fake payoff chỉ để đủ quota.

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

Hard warning toàn cục:

**Trong rolling window 4 chapter, 3/4 cùng primary engine = MAJOR pacing risk.**

Batch boundary không reset rule này. Ví dụ Ch.4–7 vẫn phải được xét cùng nhau dù cắt qua hai batch.

## 7. Dramatic Geometry Controller

Engine khác tên không tự động tạo variety.

Mỗi chapter theo dõi:

- pressure source;
- decision locus;
- movement mode;
- information flow;
- opposition shape;
- resolution mode;
- reversal type;
- kinetic level.

Rules:

- 3 consecutive near-same geometry → WATCH;
- 3/4 cùng core geometry → **MAJOR pacing risk**;
- topic/bối cảnh khác không xóa finding nếu conflict vẫn vận hành giống nhau.

Ví dụ cần bắt:

`facts được trình bày → MC hỏi → MC chẩn đoán → test → MC kết luận`

lặp qua audit, training và negotiation.

Fix phải đổi structure/decision/information/resolution, không synonym-spin.

## 8. Competence Friction Meter

Mỗi competence conversion chính của MC gắn nhãn:

- `CLEAN_WIN`;
- `COSTLY_WIN`;
- `PARTIAL`;
- `WRONG_MODEL`;
- `DEPENDENT_ON_OTHER`;
- `FAILURE`;
- `NO_CONVERSION`.

Rules:

- 3 CLEAN_WIN conversions liên tiếp → WATCH;
- 4/5 recent competence conversions = CLEAN_WIN → **MAJOR flattening risk**;
- nếu người khác sửa MC trước khi hậu quả thật xảy ra, không được giả đó là costly mistake;
- chosen cost biết trước không tự động là mistake.

Không làm MC ngu để giảm meter. Friction phải đến từ:

- kiến thức lỗi thời;
- consent/timing;
- politics;
- resource constraint;
- incomplete data;
- supporting-cast expertise;
- thắng local nhưng tạo cost mới.

## 9. Aspiration Controller

Tách:

- `scarcity`: đang thiếu/sợ mất gì;
- `aspiration`: thứ nhân vật + độc giả muốn có vì mạnh/đẹp/hiếm/mở khóa tương lai/đổi địa vị.

Mỗi aspiration beat có thể ghi:

- object_of_desire;
- why_desirable;
- sensory/status proof;
- distance to acquire;
- gate/cost;
- future use image;
- status.

Rule progression xianxia:

**Rolling 5 chapter chỉ có scarcity/admin/problem-fixing mà không có aspiration beat đáng nhớ hoặc wonder đủ mạnh = MAJOR appetite risk.**

Resource chỉ được tính aspiration nếu prose làm nó đáng thèm, không phải chỉ có tên trong inventory.

## 10. Heat Curve

Heat không chỉ là combat.

Heat có thể đến từ:

- danger;
- wonder;
- power display;
- emotional rupture;
- reversal;
- threshold crossing;
- high-stakes choice;
- reveal mạnh;
- chase/combat/survival.

Mỗi chapter ghi `peak_heat`:

- `H0` quiet/setup/decompression;
- `H1` active tension;
- `H2` strong memorable beat;
- `H3` batch/arc peak.

Rule:

**Rolling 5 chapter phải có ít nhất một H2+. Nếu max heat < H2 → MAJOR flatness risk.**

Không ép mọi chapter H2/H3. Quiet chapter vẫn hợp lệ nếu tạo contrast, emotion, meaning hoặc decompression có chức năng.

Cũng cảnh báo saturation nếu quá nhiều H3 liên tiếp.

## 11. Scene planning — không over-plan

Planner xác định chapter-level:

- primary/secondary Narrative Engine;
- Dramatic Geometry signature;
- Story Promise target + Payoff Magnitude;
- intended competence outcome nếu relevant;
- Aspiration target nếu rolling debt yêu cầu;
- peak heat target;
- POV + knowledge boundary;
- Xianxia Experience target nếu organic;
- Emotional movement nếu có;
- human irrationality/blind spot nếu relevant;
- intrinsic reward trước ending hook;
- ending shape.

Conflict/transaction scene có thể dùng goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene không bắt buộc đủ các ô đó; chỉ cần focal tension/curiosity, sensory anchor, knowledge boundary và movement/residue có ý nghĩa.

Pre-check Binge Test trước draft:

1. Khoảnh khắc sướng nhất dự kiến là gì?
2. Nếu bỏ ending hook, chapter có đủ giá trị nội tại không?

Nếu không có concrete intrinsic reward và không có valid structural waiver, redesign plan.

## 12. Three-mode QC

Mỗi chapter trong v3 enforcement window phải có:

- `continuity_report.md`;
- `reader_retention_report.md`;
- `style_fingerprint_report.md`;
- `quality_report.md` aggregate.

Không aggregate PASS nếu một reviewer còn BLOCKER/MAJOR.

### Continuity Auditor

Canon, timeline, geography, cultivation/power, technique/item, injury/fatigue, knowledge, relationship/faction, POV boundary, hard DNA/state contradiction.

### Reader Retention Editor

Bắt buộc kiểm:

- Story Promise magnitude/drought;
- Narrative Engine;
- Dramatic Geometry;
- Competence Friction;
- Aspiration;
- Heat Curve;
- Binge Test;
- drag;
- agency;
- costly mistakes;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

### Style Fingerprint Auditor

Rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph/sentence shape, dialogue sameness, positive prose texture, calibration drift.

### Aggregate

Phải tách:

- **Technical Gate**;
- **Reader-Reward Gate**.

Technical Gate PASS không override Reader-Reward Gate MAJOR.

## 13. Binge Test — bắt buộc

Ở cuối Reader Retention QC phải trả lời riêng:

### Câu 1

**Khoảnh khắc sướng nhất chương là gì?**

Phải là concrete moment đã xảy ra trong chapter.

Không được dùng:

- hook chapter sau;
- setup chưa có result;
- “worldbuilding tốt” chung chung.

Nếu không có: `NONE` → ít nhất MAJOR trừ decompression chapter có emotional payoff rất rõ.

### Câu 2

**Nếu bỏ ending hook, bản thân chương này có đủ đáng đọc không?**

Kết quả:

- `YES`;
- `WEAK`;
- `NO`.

`NO` → MAJOR + rewrite, trừ explicit structural waiver trong Arc Outline. Waiver không dùng hai chapter liên tiếp.

Bingeability không đồng nghĩa cliffhanger.

## 14. Rolling 3-Chapter Audit

Vẫn chạy **trước final mọi chapter chia hết cho 3**:

`3, 6, 9, 12, 15, 18...`

Đọc full final N-2, final N-1 và rewrite candidate N.

Audit:

- opening;
- Narrative Engine;
- Dramatic Geometry;
- dialogue geometry;
- conflict solution;
- ending;
- rhetorical tics;
- Promise magnitude;
- competence friction trend;
- aspiration trend;
- heat trend;
- Binge Test trend;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes.

Heat official rule vẫn rolling 5; rolling-3 dùng để cảnh báo sớm.

Batch size 5 không thay đổi cadence này.

Nếu audit phát hiện MAJOR ở candidate N, rewrite N rồi rerun reviewer/aggregate/rolling audit cần thiết trước final.

## 15. Xianxia Experience + Emotional Residue

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

## 16. Dynamic outline adaptation

Sau mỗi final + memory update:

- kiểm beat kế tiếp còn hợp state mới không;
- không ép nhân vật quay lại plan cũ;
- cập nhật future beat chưa final nếu cần;
- cập nhật Promise PAY windows + magnitude debt;
- cập nhật Narrative Engine distribution;
- cập nhật Dramatic Geometry map;
- cập nhật competence-friction need;
- cập nhật Aspiration debt;
- cập nhật Heat Curve;
- cập nhật Binge risk;
- cập nhật Xianxia/Emotional debt;
- ghi revision log khi deviation đáng kể.

Nếu arc kết thúc giữa batch 5, phải tạo/đọc arc tiếp theo trước chapter vượt boundary. Không kéo/kết arc chỉ để khớp batch.

## 17. End-of-Batch Audit

Sau chapter thứ 5 của requested batch, tạo:

`stories/<slug>/chapters/batch_NNNN_NNNN_audit.md`

Ví dụ:

- `batch_0001_0005_audit.md`
- `batch_0006_0010_audit.md`
- `batch_0011_0015_audit.md`

Audit dùng `templates/batch_audit.template.md` và kiểm:

- artifact completion;
- arc progress;
- Story Promise magnitude + pay/major-payoff debt;
- Narrative Engine distribution, kể cả rolling window cắt batch boundary;
- Dramatic Geometry distribution;
- Competence Friction distribution;
- Aspiration coverage;
- rolling-5 Heat Curve;
- Binge Test health;
- Xianxia Experience;
- Emotional Residue;
- continuity;
- character agency/human irrationality;
- cultivation/power/resource economy;
- style fingerprints;
- setup/payoff/threads;
- Reader Experience Memory consistency;
- next-batch handoff.

## 18. Completion gate

Batch 5 chỉ được báo `PASS/READY` khi:

- đủ 5 final theo requested range, trừ khi user yêu cầu range khác hoặc truyện kết thúc;
- mỗi chapter trong enforcement window đủ artifact QC;
- rolling audit tồn tại ở các chapter đến hạn;
- story memory phản ánh chapter cuối;
- `memory/reader_experience.md` phản ánh chapter cuối;
- batch audit tồn tại;
- không còn BLOCKER/MAJOR chưa xử lý;
- **Reader-Reward Gate sạch**;
- next-batch handoff rõ.

Thiếu bất kỳ artifact bắt buộc nào → `INCOMPLETE`.

Retention-controller MAJOR còn tồn tại → `REPAIR_REQUIRED`.

## 19. Legacy / migration

Các story cũ có batch 10 không cần xóa hoặc chia lại audit lịch sử.

Ví dụ `batch_0001_0010_audit.md` cũ vẫn hợp lệ historical checkpoint.

Khi sync sang batch 5/v3:

- đặt `pipeline.batch_size: 5`;
- đặt `pipeline.version: 3.0` khi migration hoàn tất;
- bật `retention_v3_required`;
- không retroactively fake per-chapter v3 QC;
- có thể dựng v3 baseline từ recent finals + Reader Experience thật;
- batch kế tiếp bắt đầu tại `next_chapter` hiện tại và lấy 5 chapter;
- historical audit cũ vẫn giữ nguyên.

## 20. Resume ở chat mới

Đọc tối thiểu:

1. `AGENTS.md`;
2. `docs/BATCH_5_WORKFLOW.md`;
3. `docs/RETENTION_CONTROLLERS_V3.md`;
4. manifest;
5. seed;
6. current state;
7. reader experience;
8. batch audit gần nhất;
9. arc hiện tại;
10. bible/ledgers liên quan;
11. recent summaries/final.

Lệnh ngắn hợp lệ:

> Tiếp tục branch story/<slug> và viết batch 5 chương tiếp theo đúng pipeline.