# Batch 5 Chapters Workflow

## 1. Mục tiêu

Batch mặc định của pipeline là **5 chương**.

Lệnh chuẩn:

> Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.

Batch chỉ là đơn vị điều phối + audit. Mỗi chương vẫn là một transaction độc lập và bắt buộc chạy tuần tự.

Framework v3 bắt buộc đọc:

- `docs/RETENTION_CONTROLLERS_V3.md`;
- `docs/XIANXIA_DENSITY_CONTROLLER.md`;
- `docs/REFERENCE_STYLE_SYSTEM.md` khi story bật Reference Style.

Core rules:

**PASS kỹ thuật ≠ PASS trải nghiệm đọc.**

**PASS retention ≠ PASS genre density.**

**Reference Style = high-level Style DNA; Writer viết theo story Style Bible, không sao chép reference.**

## 2. Chapter transaction

Với mỗi chương N:

```text
assemble context
→ scene plan
→ draft
→ Continuity Auditor
→ Reader Retention Editor + Retention Controllers v3 + Xianxia Density
→ Style Fingerprint Auditor + Reference drift/overfit check if enabled
→ aggregate quality gate: Technical Gate + Reader-Reward Gate + Xianxia Density Gate
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
4. đọc `docs/XIANXIA_DENSITY_CONTROLLER.md` nếu story là truyện mới v3 hoặc manifest bật `xianxia_density_required`;
5. nếu manifest/seed bật Reference Style, đọc `docs/REFERENCE_STYLE_SYSTEM.md`, xác nhận profile path hợp lệ và Style Bible đã có `Reference Style Adaptation Contract`;
6. đọc manifest và xác nhận `pipeline.batch_size: 5` + các controller bắt buộc;
7. đọc seed + ba bible;
8. đọc Story Promises trong master outline;
9. đọc arc hiện tại;
10. đọc `memory/current_state.md`;
11. đọc `memory/reader_experience.md`;
12. đọc ledgers liên quan;
13. đọc summaries gần nhất;
14. đọc full final gần nhất;
15. đọc thêm 2–3 full final nếu cần kiểm repetition/style/geometry/density;
16. verify batch audit trước tồn tại nếu range trước đã hoàn tất;
17. xác định start/end chapter của 5 chương tiếp theo.

Preflight phải biết:

- core Story Promise + last PAY magnitude;
- `pay_drought` + `major_payoff_debt`;
- recent Narrative Engines;
- recent Dramatic Geometry signatures;
- recent competence outcomes;
- recent aspiration beats;
- recent heat sequence + last H2+;
- recent `xianxia_peak` sequence + last X2+/X3;
- recent replaceability sequence;
- current `genre_density_debt`;
- recent Binge Test results;
- recent dialogue geometries;
- recent ending shapes;
- recent rhetorical tics;
- last Xianxia Experience;
- last Emotional Residue;
- reader appetite/payoff debt;
- cultivation/power constraints;
- active deadlines/threads;
- character drift/human irrationality risks;
- story Style Bible direct contract;
- Reference Style enabled/profile nếu có;
- project-owned calibration maturity;
- recent reference `drift-away / overfit / weakness leakage` findings nếu có.

Writer **không cần reread toàn reference work** trong mỗi chapter. Direct style source là Style Bible + project-owned calibration.

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

Batch boundary không reset rule này.

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

Không làm MC ngu để giảm meter. Friction phải đến từ knowledge/world/consent/politics/resource/other-character agency.

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

Heat có thể đến từ danger, wonder, power display, emotional rupture, reversal, threshold crossing, high-stakes choice, reveal mạnh, chase/combat/survival.

Mỗi chapter ghi `peak_heat`:

- `H0` quiet/setup/decompression;
- `H1` active tension;
- `H2` strong memorable beat;
- `H3` batch/arc peak.

Rule:

**Rolling 5 chapter phải có ít nhất một H2+. Nếu max heat < H2 → MAJOR flatness risk.**

Không ép mọi chapter H2/H3. Quiet chapter vẫn hợp lệ nếu tạo contrast, emotion, meaning hoặc decompression có chức năng.

## 11. Xianxia Density Controller

Controller này **binding mặc định cho truyện mới framework v3**. Không tự áp/migrate story branch cũ nếu user không yêu cầu.

Mục tiêu: tránh truyện chỉ có “skin tu tiên”.

### Ba tầng

- `Ambient Xianxia`: môi trường sống vận hành như tu tiên giới;
- `Active Xianxia`: supernatural law/state trực tiếp đổi constraint, choice hoặc consequence;
- `Aspirational Xianxia`: cảnh giới/tài nguyên/năng lực/địa điểm khiến độc giả thật sự muốn đạt tới.

### Peak

Mỗi chapter ghi:

- `X0` skin only;
- `X1` ambient;
- `X2` active;
- `X3` strong memorable xianxia beat.

### Replaceability Test

Hỏi:

> Nếu đổi `linh thạch→tiền`, `linh điền→ruộng`, `công pháp→kỹ thuật`, `tông môn→tổ chức phàm`, causal logic còn gần nguyên vẹn không?

Ghi `LOW / MEDIUM / HIGH_REPLACEABILITY`.

### Rolling rules

- rolling 3 phải có ít nhất **1 chapter X2+**;
- 3 consecutive `HIGH_REPLACEABILITY` → **MAJOR genre dilution risk**;
- rolling 5 phải có ít nhất **2 chapter X2+**;
- rolling 5 phải có ít nhất **1 chapter X3**;
- rolling 5 phải có aspiration/wonder desire đủ rõ.

Waiver chỉ dùng cho intentional decompression/grief/aftermath window có lý do rõ và không được kéo dài vô hạn.

### Fix rule

Không clear finding bằng cách thêm danh từ `linh khí / đạo vận / pháp bảo`.

Phải sửa causal structure:

`supernatural law/state → constraint/opportunity → decision → observable consequence`.

## 12. Reference Style System

Chỉ áp nếu seed/manifest bật `reference_style_enabled`.

Flow:

`Reference Profile → story Style Bible adaptation → Writer → project-owned calibration → Style Fingerprint QC`.

### Direct writing rule

Writer viết theo **story Style Bible**. Không dùng tên tác giả/tác phẩm reference như direct prompt.

Không copy:

- câu chữ;
- rhetorical frame;
- hình ảnh đặc trưng;
- scene/plot beat;
- convert syntax;
- stock gesture của nguồn.

### Default xianxia traits nếu story dùng profile framework

Style Bible có thể adapt:

- prose trực diện/event-forward;
- câu trung bình làm trục, câu ngắn tại impact;
- cultivation qua constraint/mechanism/body/perception/resource/consequence;
- combat tôn trọng power gap/resource/timing/cost;
- Dao/insight từ lived experience/concrete image lên abstraction;
- mortal/immortal contrast;
- emotional restraint → rupture → persistent scar;
- world scale mở theo tầng.

### Weakness filter

Không học:

- exposition/recap dài;
- cú pháp dịch cứng;
- stock `sắc mặt/ánh mắt/hít sâu`;
- connector lặp;
- slow pacing không intrinsic reward;
- aphorism không có trải nghiệm đỡ phía dưới.

### Calibration takeover

Khi story có 4–6 final samples thuộc ít nhất 4 engine và đủ chất lượng, project-owned calibration được ưu tiên hơn Reference Profile.

Style Auditor phải bắt:

- `drift-away`: prose trở lại AI/generic, cultivation khô, combat log, Dao slogan;
- `overfit`: prose cố giống source qua cú pháp/cụm/frame/stock gesture;
- `weakness leakage`: bê nhược điểm serialization/dịch cũ vào story mới.

## 13. Scene planning — không over-plan

Planner xác định chapter-level:

- primary/secondary Narrative Engine;
- Dramatic Geometry signature;
- Story Promise target + Payoff Magnitude;
- intended competence outcome nếu relevant;
- Aspiration target nếu rolling debt yêu cầu;
- peak heat target;
- `xianxia_peak` + replaceability target;
- Ambient/Active/Aspirational Xianxia target;
- POV + knowledge boundary;
- Xianxia Experience target nếu organic;
- Emotional movement nếu có;
- human irrationality/blind spot nếu relevant;
- intrinsic reward trước ending hook;
- ending shape;
- style mode: everyday / cultivation / combat / wonder / Dao / emotional rupture / other.

Planner bắt buộc hỏi:

1. **Yếu tố nào khiến chapter này chỉ có thể tồn tại trong tu tiên giới?**
2. **Supernatural law/state nào có causal consequence?**
3. **Nếu chapter là X0/X1, rolling 3/5 có còn hợp lệ không?**
4. **Style mode cần giữ trait nào từ Style Bible và phải tránh Reference weakness nào?**

Conflict/transaction scene có thể dùng goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene không bắt buộc đủ các ô đó; chỉ cần focal tension/curiosity, sensory anchor, knowledge boundary và movement/residue có ý nghĩa.

Pre-check Binge Test trước draft:

1. Khoảnh khắc sướng nhất dự kiến là gì?
2. Nếu bỏ ending hook, chapter có đủ giá trị nội tại không?

Nếu không có concrete intrinsic reward và không có valid structural waiver, redesign plan.

## 14. Three-mode QC

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
- Xianxia Density;
- Replaceability Test;
- Binge Test;
- drag;
- agency;
- costly mistakes;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

### Style Fingerprint Auditor

Rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph/sentence shape, dialogue sameness, positive prose texture, calibration drift.

Nếu Reference Style bật, bắt buộc kiểm high-level alignment, drift-away, overfit/imitation risk, weakness leakage và calibration takeover.

### Aggregate

Phải tách:

- **Technical Gate**;
- **Reader-Reward Gate**;
- **Xianxia Density Gate**.

Technical Gate PASS không override Reader-Reward/Xianxia Density MAJOR. Reference Style overfit/drift MAJOR làm Technical Gate FAIL qua Style reviewer.

## 15. Binge Test — bắt buộc

Ở cuối Reader Retention QC phải trả lời riêng:

### Câu 1

**Khoảnh khắc sướng nhất chương là gì?**

Phải là concrete moment đã xảy ra trong chapter.

Không được dùng hook chapter sau, setup chưa có result hoặc “worldbuilding tốt” chung chung.

Nếu không có: `NONE` → ít nhất MAJOR trừ decompression chapter có emotional payoff rất rõ.

### Câu 2

**Nếu bỏ ending hook, bản thân chương này có đủ đáng đọc không?**

Kết quả `YES / WEAK / NO`.

`NO` → MAJOR + rewrite, trừ explicit structural waiver trong Arc Outline. Waiver không dùng hai chapter liên tiếp.

Bingeability không đồng nghĩa cliffhanger.

## 16. Rolling 3-Chapter Audit

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
- Xianxia Density + Replaceability;
- Binge Test trend;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes;
- story-style consistency / reference overfit when enabled.

Heat official rule vẫn rolling 5. Xianxia Density có rolling 3 hard rule và rolling 5 hard rule.

Batch size 5 không thay đổi cadence này.

Nếu audit phát hiện MAJOR ở candidate N, rewrite N rồi rerun reviewer/aggregate/rolling audit cần thiết trước final.

## 17. Xianxia Experience + Emotional Residue

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

Trong rolling 3–5 chapter cần có thay đổi có bằng chứng về emotional state, relationship meaning, self-image, attachment/grief/joy/shame/fear, object/memory meaning hoặc costly mistake scar.

Không tạo melodrama giả để tick checklist.

## 18. Dynamic outline adaptation

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
- cập nhật Xianxia Density peak/replaceability + genre_density_debt;
- cập nhật Binge risk;
- cập nhật Xianxia/Emotional debt;
- cập nhật style correction nếu recent finals drift khỏi Style Bible hoặc overfit reference;
- ghi revision log khi deviation đáng kể.

Nếu arc kết thúc giữa batch 5, phải tạo/đọc arc tiếp theo trước chapter vượt boundary. Không kéo/kết arc chỉ để khớp batch.

## 19. End-of-Batch Audit

Sau chapter thứ 5 của requested batch, tạo:

`stories/<slug>/chapters/batch_NNNN_NNNN_audit.md`

Audit dùng `templates/batch_audit.template.md` và kiểm:

- artifact completion;
- arc progress;
- Story Promise magnitude + pay/major-payoff debt;
- Narrative Engine distribution, kể cả rolling window cắt batch boundary;
- Dramatic Geometry distribution;
- Competence Friction distribution;
- Aspiration coverage;
- rolling-5 Heat Curve;
- Xianxia Density peak sequence;
- Active `X2+` count + Strong `X3` count;
- Replaceability distribution;
- genre_density_debt;
- Binge Test health;
- Xianxia Experience;
- Emotional Residue;
- continuity;
- character agency/human irrationality;
- cultivation/power/resource economy;
- style fingerprints;
- Reference Style drift/overfit + calibration maturity nếu enabled;
- setup/payoff/threads;
- Reader Experience Memory consistency;
- next-batch handoff.

## 20. Completion gate

Batch 5 chỉ được báo `PASS/READY` khi:

- đủ 5 final theo requested range, trừ khi user yêu cầu range khác hoặc truyện kết thúc;
- mỗi chapter trong enforcement window đủ artifact QC;
- rolling audit tồn tại ở các chapter đến hạn;
- story memory phản ánh chapter cuối;
- `memory/reader_experience.md` phản ánh chapter cuối;
- batch audit tồn tại;
- không còn BLOCKER/MAJOR chưa xử lý;
- **Reader-Reward Gate sạch**;
- **Xianxia Density Gate sạch** đối với story bật controller này;
- Style reviewer sạch Reference drift/overfit MAJOR nếu Reference Style bật;
- next-batch handoff rõ.

Thiếu artifact bắt buộc → `INCOMPLETE`.

Retention/Xianxia-Density/Style MAJOR còn tồn tại → `REPAIR_REQUIRED`.

## 21. Legacy / migration

Các story cũ có batch 10 không cần xóa hoặc chia lại audit lịch sử.

**Không tự migrate story cũ sang Xianxia Density hoặc default Reference Style.** Chỉ áp cho story mới v3 theo manifest, hoặc khi user explicit yêu cầu migrate/update một story cũ.

Nếu user yêu cầu sync story cũ sang batch 5/v3:

- đặt `pipeline.batch_size: 5`;
- đặt `pipeline.version: 3.0` khi migration hoàn tất;
- bật `retention_v3_required` theo phạm vi migration;
- bật `xianxia_density_required` chỉ khi user yêu cầu controller này cho story đó;
- bật Reference Style chỉ khi user yêu cầu style migration/update;
- không retroactively fake per-chapter v3 QC;
- có thể dựng baseline từ recent finals + Reader Experience thật;
- batch kế tiếp bắt đầu tại `next_chapter` hiện tại và lấy 5 chapter;
- historical audit cũ vẫn giữ nguyên.

## 22. Resume ở chat mới

Đọc tối thiểu:

1. `AGENTS.md`;
2. `docs/BATCH_5_WORKFLOW.md`;
3. `docs/RETENTION_CONTROLLERS_V3.md`;
4. `docs/XIANXIA_DENSITY_CONTROLLER.md` nếu manifest bật controller;
5. `docs/REFERENCE_STYLE_SYSTEM.md` + profile nếu Reference Style bật và đang ở Genesis/Style/QC drift repair;
6. manifest;
7. seed;
8. current state;
9. reader experience;
10. batch audit gần nhất;
11. arc hiện tại;
12. bible/ledgers liên quan;
13. recent summaries/final.

Lệnh ngắn hợp lệ:

> Tiếp tục branch story/<slug> và viết batch 5 chương tiếp theo đúng pipeline.