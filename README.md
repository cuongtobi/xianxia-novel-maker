# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt** trên ChatGPT Web + GitHub.

Framework hiện hành: **v4.0 — State + Example Driven**.

## 1. Creative model

```text
SEED
→ STORY BIBLE
→ CHARACTER BASELINES
→ MASTER OUTLINE
→ STORY / ARC STATE
→ CHAPTER STATE
→ SCENE STATE
→ CHARACTER STATE + STYLE EXAMPLES
→ WRITER
→ DRAFT
→ CONTINUITY CHECK
→ PROSE EDIT
→ FINAL
→ STATE UPDATE
→ ONE ATOMIC GIT COMMIT
```

Triết lý:

```text
Rules giữ hard boundaries.
State giữ reality hiện tại.
Examples calibrate prose.
Writer viết fiction từ state, không viết theo checklist.
```

Rule-driven không biến mất hoàn toàn, nhưng chỉ còn ở lớp hệ thống: canon precedence, factual continuity, originality, file protocol và Git safety. Creative core không dùng checklist dài để ép Writer.

---

## 2. v4.0 khác v3.2

- Story Promise không còn là controller; reader expectations chỉ là planning signal trong state.
- Combined QC được bỏ khỏi active pipeline.
- Writer không nhận style/QC checklist dài.
- Scene Plan được thay bằng **Chapter State + Scene State**.
- Character Bible là baseline; runtime dùng **Character State**.
- Prose style chuyển từ rule-driven sang **dynamic Style Examples**.
- Continuity Check chỉ kiểm factual/state contradiction.
- Prose Edit là pass nhẹ, example-driven, không rewrite toàn chapter theo checklist.
- Atomic Git transaction của mỗi chapter vẫn được giữ nguyên.

---

## 3. Quick Start

### Bước 1 — Kết nối repo

Trong ChatGPT, làm việc với repo:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker
```

Framework nằm trên branch:

```text
main
```

Mỗi truyện nên có branch riêng:

```text
story/<slug>
```

Ví dụ:

```text
story/dan-de-trong-sinh
```

Không viết chapter trực tiếp lên `main`.

### Bước 2 — Cung cấp ý tưởng truyện

Có thể đưa ý tưởng tự nhiên, không cần tự viết đúng schema.

Ví dụ:

```text
Dựa vào seed template, tạo truyện:

Một Đan Đế lúc đột phá bị ám hại, trọng sinh về thời niên thiếu.
Hắn giữ ký ức đan đạo đời trước nhưng tu vi phải tu lại từ đầu.
Có arc thi đấu tông môn, bí cảnh, chiến đấu thập tử nhất sinh,
phản diện thông minh, romance và happy ending.
Main không được nghiền ép mọi đối thủ; phải tính toán mới thắng.
```

Seed chỉ ghi **creative intent**. Canon và runtime state được xây ở Genesis.

### Bước 3 — Chạy Genesis

Sau khi seed ổn:

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis
đến khi READY_TO_WRITE.
```

Genesis sẽ tạo:

```text
Seed
→ Story Bible
→ Character Baselines
→ Minimal Style Bible
→ Master Outline
→ Style Example Bank
→ Initial Story State
→ Initial Arc State
→ Initial Character States
→ Continuity Ledgers
→ Genesis Consistency Audit
→ READY_TO_WRITE
```

Genesis không micro-outline toàn bộ hàng trăm chương. Master Outline chỉ khóa direction dài hạn; production sử dụng State để quyết định diễn biến hiện tại.

---

## 4. Cách dùng Style Examples

v4.0 dùng **example-driven prose** thay vì bắt Writer tuân thủ hàng chục prose rules.

### Calibration hiện có

Framework hiện có calibration được rút từ **6 user-supplied samples**, nhưng raw source text không được lưu trong repo và không được feed trực tiếp cho Writer.

Các calibrated examples gốc của framework:

```text
CAL-TACT-01   survival / tactical reasoning
CAL-DISC-01   cultivation / artifact / formation discovery
CAL-COMB-01   high-intensity combat escalation
CAL-DIAL-01   pragmatic negotiation / status dialogue
CAL-WORLD-01  local event → wider world consequence
CAL-REL-01    family / close relationship / personal stakes
CAL-QUIET-01  quiet life / training / recovery / travel
CAL-POL-01    faction / institutional decision cascade
```

Index:

```text
examples/calibration/index.md
```

Calibration profile:

```text
examples/calibration/PROFILE.md
```

### Cách selector chọn example

Mặc định:

```text
1 scene → 1 primary example
```

Chỉ thêm example thứ hai nếu scene thực sự trộn hai prose functions lớn. Dùng tối đa 3 examples cho chapter mixed-mode dài.

Không load tất cả examples cùng lúc.

Priority:

```text
1. user-approved project final
2. strong project-owned curated example
3. calibrated original
4. generic framework bootstrap
```

Khi story đã có prose tốt của chính nó, các final được user duyệt nên dần thay thế framework examples.

### Khi muốn thêm sample mới

Có thể upload TXT/DOCX hoặc dán prose vào chat rồi yêu cầu:

```text
Thêm sample này vào calibration của pipeline.
Không lưu raw sample vào repo.
Chỉ rút high-level prose mechanics và tạo calibrated example gốc nếu cần.
```

Sample mới chỉ nên thêm khi nó đại diện cho **một prose function còn thiếu hoặc chưa đủ tốt**.

Không cần tích lũy hàng chục sample giống nhau.

### Raw sample không phải Writer input

Pipeline không dùng:

```text
raw reference chapter
→ Writer
```

Mà dùng:

```text
raw sample
→ curator distills mechanics
→ original calibrated example
→ dynamic selector
→ Writer
```

Không học/copy:

- wording;
- distinctive imagery/metaphor;
- rhetorical frame;
- paragraph sequence;
- scene structure;
- plot beat;
- character/world identity;
- lỗi dịch/convert;
- connector spam;
- spectator spam;
- onomatopoeia spam.

---

## 5. Production — viết một chapter

Per-chapter flow:

```text
READ CURRENT STATE
→ DERIVE CHAPTER STATE
→ DERIVE SCENE STATE
→ SELECT STYLE EXAMPLE
→ WRITE DRAFT
→ CONTINUITY CHECK
→ FACTUAL FIX IF NEEDED
→ LIGHT PROSE EDIT
→ FINAL
→ EXTRACT + UPDATE STATE
→ ATOMIC COMMIT
```

### Chapter State

Chapter State trả lời:

```text
Hiện tại chuyện đang ở đâu?
Pressure nào đang active?
Ai có mặt / ai biết gì?
Resource, injury, relationship đang thế nào?
Tension/opportunity nào đang ripe?
Những state change nào có thể xảy ra tự nhiên?
```

Nó **không** phải beat checklist.

### Scene State

Scene State là snapshot sống:

```text
POV / time / place / cast
what just happened
physical state
emotional state
relationship state
immediate desire
knowledge / suspicion / wrong belief
pressure
resources / limits
possible directions
expected state-change type
```

`possible directions` là affordance, không phải mandatory beats.

### Writer input

Writer chỉ nên nhận:

```text
Chapter State
+ Scene State
+ relevant Character State
+ minimal canon anchors
+ selected Style Example(s)
```

Không feed Writer:

```text
Combined QC cũ
Story Promise matrix
anti-AI checklist
full calibration profile
raw user samples
mọi Bible/ledger của story
```

### Writer principle

Writer phải coi State là reality, không phải outline checklist.

Nhân vật hành động từ:

```text
desire
+ knowledge
+ emotion
+ relationship
+ body condition
+ resources
+ current pressure
```

Prose ưu tiên fiction movement:

```text
fact / action
→ effect
→ response
→ changed situation
→ next action / decision
```

Đây là tendency của calibration, không phải công thức bắt buộc cho từng paragraph.

---

## 6. Continuity Check

Sau Draft chỉ kiểm **factual/state contradiction**:

- canon;
- timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction state;
- POV identity;
- hard Character Baseline contradiction.

Decision:

```text
PASS
hoặc
FIX_REQUIRED
```

Nếu `FIX_REQUIRED`, chỉ sửa contradiction nhỏ nhất cần thiết rồi recheck fact đó.

Continuity Checker không chấm:

- prose hay/dở;
- payoff quota;
- pacing formula;
- style score;
- retention score.

---

## 7. Prose Edit

Sau Continuity PASS, chạy một prose edit nhẹ với cùng selected example(s).

Editor được phép:

- bỏ explanation mà scene đã tự thể hiện;
- nén reasoning bị biến thành report;
- sửa tiếng Việt gượng/convert-like;
- cắt repetition rõ ràng;
- làm rõ quan hệ nhân-quả hoặc không gian hành động.

Editor phải:

```text
Prefer leaving good prose untouched.
```

Không:

- rewrite toàn chapter chỉ để prose “đẹp hơn”;
- đồng nhất độ dài paragraph;
- tạo punchline/aphorism hàng loạt;
- thêm plot/state mới;
- copy example.

Không cần persist prose-edit report.

---

## 8. State Update

Final là truth.

Sau Final, State Extractor cập nhật khi cần:

```text
memory/story_state.md
memory/arc_state.md
memory/character_states.md
memory/canon_ledger.md
memory/timeline.md
memory/knowledge_ledger.md
memory/cultivation_ledger.md
memory/inventory_artifacts.md
memory/relationships.md
chapter summaries
manifest.yaml
```

Chỉ update fact/event thực sự tồn tại trong Final.

Outline không được ghi đè chuyện đã xảy ra.

---

## 9. Persisted chapter artifacts

Mỗi chapter hoàn chỉnh tối thiểu có:

```text
chapters/NNNN/chapter_state.md
chapters/NNNN/scene_state.md
chapters/NNNN/draft.txt
chapters/NNNN/continuity_check.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

Nếu chapter đóng requested batch:

```text
chapters/batch_NNNN_NNNN_audit.md
```

Không còn active requirement cho:

```text
combined_qc_report.md
continuity_report.md legacy
reader_retention_report.md
style_fingerprint_report.md
quality_report.md
rewrite.txt
rolling_3_chapter_audit.md
```

---

## 10. Atomic Git transaction

Mỗi chapter là một transaction độc lập.

```text
chapter-start HEAD/tree
↓
generate everything in session
↓
Final + State Update ready
↓
create blobs
↓
create one tree
↓
create one commit
↓
update story branch ref once
↓
verify
```

Nếu lỗi xảy ra trước branch ref update, chapter chưa hoàn tất và persistent story state không được thay đổi.

Không persist lần lượt từng artifact trong lúc chapter đang viết.

---

## 11. Viết một chapter

Ví dụ request:

```text
Viết chương tiếp theo theo pipeline v4.
Dùng current Story/Arc/Character State,
chọn Style Example phù hợp scene,
chạy Continuity Check, Prose Edit,
State Update và atomic commit.
```

Nếu muốn test prose trước khi chạy batch dài:

```text
Viết thử 1 chương bằng pipeline v4 hiện tại.
Sau khi hoàn tất, cho tôi biết example function nào đã được chọn.
```

---

## 12. Batch 5

Default batch:

```text
5 chapters
```

Request:

```text
Viết batch 5 chương tiếp theo theo pipeline v4,
tuần tự và cập nhật state sau từng chương.
```

Execution:

```text
Chapter N
→ atomic commit + verify
→ Chapter N+1
→ atomic commit + verify
→ ...
→ Chapter N+4 + batch audit
```

Chapter tiếp theo chỉ bắt đầu sau khi chapter trước commit và verify thành công.

Batch audit chỉ tạo ở chapter thứ 5 của requested range.

---

## 13. Tiếp tục story đang viết

Request:

```text
@GitHub tiếp tục story <slug>.
Đọc branch story/<slug>, current state và manifest,
rồi viết chapter tiếp theo theo pipeline v4.
```

Khi resume:

1. đọc branch thực tế, không dựa vào trí nhớ chat;
2. đọc current Story/Arc/Character State trước;
3. chỉ load canon/ledger/final cần thiết để giải ambiguity;
4. nếu chapter cuối không có atomic state handoff hoàn chỉnh, xem nó là incomplete;
5. không resume từ orphan blob hoặc verbal claim.

---

## 14. Migrate story v3.x → v4.0

Story lịch sử có thể còn:

```text
scene_plan.md
combined_qc_report.md
rewrite.txt
reader_experience.md
old Story Promise memory
```

Không cần xóa lịch sử.

Khi muốn tiếp tục bằng v4:

```text
Migrate story branch <slug> từ v3.x sang v4.0.
Giữ historical artifacts,
khởi tạo Story State / Arc State / Character States / example bank,
verify consistency rồi mới viết chapter tiếp theo.
```

Xem:

```text
docs/FRAMEWORK_V4_MIGRATION.md
```

---

## 15. Recommended workflow

Cho story mới:

```text
1. Idea
2. Seed
3. Genesis
4. READY_TO_WRITE
5. Viết thử 1–3 chapters
6. User đánh giá prose
7. Promote final tốt vào project example bank
8. Viết Batch 5
9. Tiếp tục state-driven production
10. Compact memory ở arc/saga boundaries khi cần
```

Nếu prose vẫn “AI hóa”, ưu tiên kiểm tra theo thứ tự:

```text
1. State có quá nhiều explanation không?
2. Scene State có biến thành beat checklist không?
3. Example được chọn có đúng prose function không?
4. Có đang load quá nhiều examples không?
5. Prose Editor có over-edit không?
```

Không phản xạ bằng cách thêm một danh sách prose rules mới vào Writer.

---

## 16. Source of truth

```text
1. Canon Ledger
2. Final Chapters
3. Bibles
4. Current Story/Arc/Character State
5. Continuity Ledgers
6. Master Outline
7. Seed
8. Chapter/Scene State snapshots
9. Draft
```

Master Outline = direction.

State = present reality.

Final + Canon Ledger = chuyện đã thực sự xảy ra.

---

## 17. Repository structure

Framework-level:

```text
AGENTS.md
docs/
examples/
  calibration/
  default/
memory/
prompts/
templates/
stories/
README.md
```

Story-level điển hình:

```text
stories/<slug>/
├── manifest.yaml
├── seed/
├── bible/
├── outline/
├── examples/
│   └── style/
├── chapters/
├── final/
└── memory/
```

---

## 18. Core docs

- `AGENTS.md` — operating contract.
- `docs/ARCHITECTURE.md` — architecture tổng thể.
- `docs/STATE_EXAMPLE_SYSTEM.md` — State + Example model.
- `docs/BATCH_5_WORKFLOW.md` — batch workflow.
- `docs/GITHUB_CHATGPT_PROTOCOL.md` — branch/read/write/atomic Git protocol.
- `docs/FRAMEWORK_V4_MIGRATION.md` — migrate story cũ.
- `memory/MEMORY_SYSTEM.md` — memory/state strategy.
- `prompts/PIPELINE_PROMPTS.md` — role prompts.
- `examples/calibration/PROFILE.md` — prose calibration profile.
- `examples/calibration/index.md` — calibrated example registry.

---

## 19. Principle

```text
GitHub giữ persistent truth.
Bible giữ stable world/character baseline.
State giữ hiện tại.
Examples giữ cảm giác prose.
Writer sáng tác từ reality, không từ checklist.
Continuity Check giữ factual correctness.
Prose Edit chỉ sửa khi prose thật sự cần.
Atomic commit giữ transaction sạch.
Final giữ tác phẩm.
```
