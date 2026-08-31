# AGENTS.md — Operating Contract

Tài liệu này là luật vận hành bắt buộc cho mọi phiên ChatGPT làm việc với repository này.

## 1. Nguyên tắc kiến trúc

Framework hiện hành dùng **một controller duy nhất: Story Promise Controller**.

Không tạo, không chạy, không chấm quota và không dùng làm hard gate các controller đã loại bỏ: Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration, Heat Curve, Binge Test, Xianxia Experience, Xianxia Density, Emotional Residue hoặc Human Irrationality Controller.

Các khái niệm như nhịp, cảm xúc, chất tiên hiệp, sai lầm, ham muốn, combat, wonder vẫn có thể xuất hiện tự nhiên trong Story Bible, Character DNA, Style Bible và prose. Chúng **không phải controller, không có rolling quota và không được ép Writer tối ưu metric**.

## 2. Vai trò

- **Orchestrator** — xác định stage, đọc source of truth, điều phối workflow, verify artifact gate.
- **World Architect** — xây world/cultivation có luật, giới hạn, tài nguyên và hệ quả.
- **Story Architect** — master outline, arc, progression dài hạn.
- **Story Promise Controller** — khóa 3–5 reader promises và theo dõi trạng thái payoff.
- **Reference Style Director** — chuyển high-level style traits thành house style riêng khi story bật Reference Style.
- **Character Director** — Character DNA, động cơ, mâu thuẫn, agency.
- **Scene Planner** — plan chapter gọn: mục tiêu, xung đột, payoff, promise target, continuity/style constraints.
- **Writer** — viết prose tiếng Việt tự nhiên theo story Style Bible.
- **Continuity Auditor** — canon/state/knowledge/power/POV.
- **Story Promise Reviewer** — kiểm ADVANCE/PAY/false-pay/drought của Story Promise; không chấm controller khác.
- **Style Fingerprint Auditor** — kiểm prose AI-like, cadence, dialogue sameness, reference drift/overfit.
- **Rewriter** — sửa findings cụ thể, không trang trí để pass checklist.
- **Memory Keeper** — cập nhật story memory + promise state sau mỗi final.

## 3. Source of truth

Khi dữ liệu xung đột, ưu tiên:

1. `memory/canon_ledger.md`
2. final chapters
3. `bible/*.md`
4. `memory/*.md`
5. `outline/arcs/*.md`
6. `outline/master_outline.md`
7. seed
8. draft/scene plan

Outline là kế hoạch. Final + Canon Ledger là chuyện đã xảy ra.

`memory/reader_experience.md` chỉ giữ **Story Promise runtime state** và ghi chú payoff gần đây; không override canon.

### Style hierarchy

1. story-specific `bible/style_bible.md`;
2. project-owned final/calibration samples đã duyệt;
3. seed style intent;
4. Reference Style Profile nếu bật;
5. framework defaults.

## 4. Branch contract

- Framework ở `main`.
- Mỗi truyện ở `story/<slug>`.
- Không ghi story artifact lên `main`.
- Framework change không tự áp vào story branch cũ; phải sync/migrate có chủ đích.

## 5. Read-before-write

Trước chapter mới, đọc tối thiểu:

- manifest + seed;
- story/style/characters bible phần liên quan;
- Story Promises trong master outline;
- arc hiện tại;
- `memory/current_state.md`;
- `memory/reader_experience.md`;
- ledgers cần thiết;
- ít nhất 3 recent summaries;
- full final gần nhất khi continuity trực tiếp.

Không yêu cầu Writer đọc hoặc tối ưu metric/controller đã loại bỏ.

## 6. Story Promise Controller

Genesis khóa **3–5 Story Promises**. Mỗi promise có:

- stable ID;
- reader promise;
- vì sao reader quan tâm;
- `PAY` definition;
- `ADVANCE` definition;
- false-pay examples;
- drought warning;
- escalation path.

Sau mỗi final, mỗi promise được ghi một trạng thái:

- `UNTOUCHED`;
- `ADVANCE`;
- `PAY_MINOR`;
- `PAY_MAJOR`;
- `PAY_ARC`.

Payoff magnitude là **thuộc tính của Story Promise Controller**, không phải controller riêng.

Rules:

- setup ≠ PAY;
- lời hứa tương lai ≠ PAY;
- PAY phải có kết quả/reveal/trải nghiệm/thay đổi trạng thái độc giả cảm nhận được;
- theo dõi `last_pay_chapter`, `last_major_pay_chapter`, `pay_drought` cho từng core promise;
- vượt drought warning → reviewer cảnh báo;
- không ép fake payoff chỉ để xóa drought;
- nếu promise đang đói nhưng chapter hiện tại không phù hợp để PAY, sửa outline/arc kế tiếp thay vì nhồi payoff giả vào prose.

## 7. World + cultivation contract

Worldbuilding phải có causal logic tự nhiên: luật → tài nguyên/giới hạn → tổ chức/hành vi → xung đột.

Mỗi realm quan trọng cần có thay đổi định tính, giới hạn, yêu cầu đột phá, failure mode, social meaning và cross-realm logic.

Không có Xianxia Density quota. Chất tiên hiệp được bảo vệ bằng Story Bible + Style Bible + premise, không bằng X0/X1/X2/X3 hoặc replaceability score.

## 8. Character contract

Nhân vật quan trọng cần desire, fear, value, wound, blind spot, contradiction, decision logic, speech fingerprint, relationship behavior, cultivation/combat identity và arc vector.

Nhân vật có thể sai, thiên vị, sĩ diện hoặc hành động cảm tính nếu hợp DNA. Đây là **character design**, không phải Human Irrationality Controller và không có quota sai lầm.

Không cố làm MC thất bại chỉ để cân bằng competence. Core fantasy competence được phép tạo clean wins nếu hợp premise.

## 9. Scene planning contract

Scene plan chỉ cần đủ để Writer biết:

- chapter objective;
- POV/time/place/cast;
- starting state;
- conflict/pressure;
- key beats/turn;
- character choice nếu có;
- Story Promise target;
- intended payoff nếu có;
- ending state;
- continuity constraints;
- style constraints;
- ending hook nếu organic.

Không plan Narrative Engine, Geometry signature, competence outcome label, heat level, xianxia peak, replaceability, aspiration quota hoặc binge score.

## 10. Writing contract

Writer ưu tiên truyện trước checklist:

- action/character desire trước giải thích khi hợp cảnh;
- worldbuilding qua tình huống và hậu quả;
- dialogue theo DNA, không Q&A quá sạch;
- prose Việt tự nhiên, Hán Việt vừa đủ;
- câu trung bình làm trục, câu ngắn dùng có chủ đích;
- không biến cultivation/craft thành manual nếu scene không cần;
- không tạo micro-mechanism chỉ để chứng minh “chất tiên hiệp”;
- không copy reference wording/rhetorical frame/plot beat.

## 11. QC architecture

Ba reviewer độc lập:

### Continuity Auditor
Kiểm canon, timeline, geography, power/cultivation, item, injury, knowledge, relationship, POV.

### Story Promise Reviewer
Chỉ kiểm Story Promise: target có đúng không, ADVANCE/PAY có thật không, magnitude có bị phóng đại không, drought có vượt contract không.

### Style Fingerprint Auditor
Kiểm dấu AI, nhịp câu/đoạn, rhetorical tics, dialogue sameness, exposition, calibration và Reference Style drift/overfit nếu bật.

Aggregate gate chỉ tổng hợp ba reviewer này. Không có Reader-Reward/Xianxia Density/Heat/Binge/Engine gate.

## 12. Rewrite discipline

Rewrite sửa findings cụ thể, ưu tiên:

`CUT > COMPRESS > REORDER > REPLACE > ADD`.

Không thêm lore, cơ chế, faction, scene hoặc explanation chỉ để “clear” một metric.

Mặc định final không nên dài hơn draft quá khoảng **25%**. Nếu lỗi cấu trúc không sửa được trong budget này, quay lại scene plan và tạo draft mới thay vì vá dài.

## 13. Atomic chapter transaction

```text
READ
→ PLAN
→ DRAFT
→ CONTINUITY AUDIT
→ STORY PROMISE REVIEW
→ STYLE AUDIT
→ AGGREGATE
→ REWRITE IF NEEDED
→ CRITICAL RE-QC
→ FINAL
→ UPDATE STORY MEMORY
→ UPDATE PROMISE MEMORY
```

Không có Rolling 3-Chapter Audit bắt buộc.

## 14. Batch 5

Mặc định viết 5 chương tuần tự. Sau mỗi chương phải update memory trước khi sang chương kế.

Cuối batch tạo `batch_NNNN_NNNN_audit.md` để kiểm:

- artifact completeness;
- continuity handoff;
- Story Promise delivery/drought;
- style problems đáng chú ý;
- next-batch priorities.

Batch Audit không chạy controller khác.

## 15. Completion semantics

Chapter chỉ COMPLETE khi có scene plan, draft, continuity report, Story Promise review, style report, aggregate report, rewrite nếu cần, final và memory hiện tại.

Batch chỉ COMPLETE khi đủ requested finals, memory qua chapter cuối và batch audit tồn tại.

Thiếu artifact → `INCOMPLETE`, không verbal-pass.
