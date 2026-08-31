# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt**, vận hành trực tiếp bằng **ChatGPT Web + GitHub**.

GitHub là **persistent memory + source of truth**. ChatGPT là orchestrator + architect + writer + editor + auditor.

Pipeline v2 không chỉ giữ canon/continuity. Nó còn theo dõi **trải nghiệm độc giả** để tránh truyện dài bị đúng logic nhưng lặp, lạnh hoặc mất chất tiên hiệp.

---

# 1. Pipeline v2 làm gì?

```text
Seed
  ↓
Story Bible
  ↓
Style Bible
  ↓
Characters Bible
  ↓
Master Outline
  └─ lock 3–5 Story Promises
  ↓
Arc Outline
  ├─ Promise PAY windows
  ├─ Narrative Engine map
  ├─ Xianxia Experience map
  └─ Emotional Residue plan
  ↓
Initialize Story Memory + Reader Experience Memory
  ↓
Chapter Scene Plan
  ↓
Draft
  ↓
Continuity Auditor
  ↓
Reader Retention Editor
  ↓
Style Fingerprint Auditor
  ↓
Aggregate Quality Gate
  ↓
Rewrite
  ↓
Critical Re-QC
  ↓
Rolling 3-Chapter Audit on Ch. 3/6/9/...
  ↓
Final TXT
  ↓
Story Memory + Reader Experience Memory Update
  ↓
Chương tiếp theo
```

Mục tiêu:

- giữ canon và continuity hàng trăm chương;
- văn tiếng Việt tự nhiên, không văn mẫu AI;
- Character DNA riêng, có agency và human irrationality;
- kiểm power scaling, cảnh giới, kỹ năng, tài nguyên, thương tích;
- quản ai biết gì bằng Knowledge Ledger;
- khóa và theo dõi **3–5 Story Promises**;
- theo dõi **Narrative Engine** thay vì chỉ topic;
- giữ **Xianxia Experience**: cultivation payoff, wonder, danger, power gap, mystical discovery, desirable resources, threshold crossing;
- giữ **Emotional Residue** qua 3–5 chương;
- tự chạy batch 10 chương tuần tự;
- tiếp tục ở chat mới mà không phụ thuộc memory hội thoại.

---

# 2. Quick Start

## Bước 1 — Kết nối GitHub

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker
```

Framework:

```text
main
```

Mỗi truyện:

```text
story/<slug>
```

Ví dụ:

```text
story/pham-nhan-cau-tien
story/van-co-dao-ton
story/ma-mon-truong-sinh
```

Không viết hai truyện trên cùng story branch.

## Bước 2 — Tạo seed

Mẫu:

```text
templates/seed.template.yaml
```

Bạn không cần điền toàn bộ. Có thể chỉ cung cấp ý tưởng, protagonist, hook, opening situation và tone.

Ví dụ lệnh tự nhiên:

```text
Dựa vào templates/seed.template.yaml tạo seed truyện mới.

Ý tưởng:
- main là tạp dịch nghĩa địa;
- mỗi khi thiên tài chết có thể nhặt một phần di sản;
- progression phải rõ;
- có mystery về những cái chết bất thường.
```

Seed là **creative intent**, chưa phải canon hoàn chỉnh.

## Bước 3 — Chạy Genesis

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

ChatGPT phải tự:

```text
1. Resolve slug
2. Tạo branch story/<slug> từ main
3. Lưu seed
4. Xây Story Bible
5. Xây Style Bible
6. Xây Characters Bible
7. Xây Master Outline
8. Lock 3–5 Story Promises
9. Xây Arc 1 Outline
10. Initialize Story Memory
11. Initialize Reader Experience Memory
12. Verify READY_TO_WRITE gate
```

Không cần duyệt từng stage trừ blocker thật sự cần người dùng quyết định.

## Bước 4 — Viết truyện

### Một chương

```text
Viết chương tiếp theo đúng pipeline v2, qua đủ 3-mode QC, rolling audit nếu đến kỳ, final và memory update.
```

### Batch 10 chương

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

### Chat mới

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.
Tiếp tục branch story/pham-nhan-cau-tien và viết batch 10 chương tiếp theo.
```

GitHub cung cấp state; không cần copy lịch sử chat cũ.

---

# 3. Cấu trúc một truyện

```text
stories/<story-slug>/
├── manifest.yaml
├── seed/
│   └── seed.yaml
│
├── bible/
│   ├── story_bible.md
│   ├── style_bible.md
│   └── characters_bible.md
│
├── outline/
│   ├── master_outline.md
│   └── arcs/
│       ├── arc_001.md
│       └── ...
│
├── chapters/
│   ├── 0001/
│   │   ├── scene_plan.md
│   │   ├── draft.txt
│   │   ├── continuity_report.md
│   │   ├── reader_retention_report.md
│   │   ├── style_fingerprint_report.md
│   │   ├── quality_report.md
│   │   └── rewrite.txt
│   ├── 0003/
│   │   └── rolling_3_chapter_audit.md
│   └── batch_0001_0010_audit.md
│
├── final/
│   ├── Chương 1: Tên chương.txt
│   └── ...
│
└── memory/
    ├── current_state.md
    ├── canon_ledger.md
    ├── timeline.md
    ├── character_states.md
    ├── relationships.md
    ├── cultivation_ledger.md
    ├── inventory_artifacts.md
    ├── factions_locations.md
    ├── knowledge_ledger.md
    ├── foreshadowing.md
    ├── unresolved_threads.md
    ├── chapter_summaries.md
    └── reader_experience.md
```

---

# 4. Genesis

Genesis chỉ chạy khi tạo truyện mới hoặc bổ sung phần chưa có.

```text
Seed
 ↓
Story Bible
 ↓
Style Bible
 ↓
Characters Bible
 ↓
Master Outline + Story Promise Controller
 ↓
Arc 1 Outline + Narrative/Xianxia/Emotional Controllers
 ↓
Story Memory
 ↓
Reader Experience Memory
```

## 4.1 Story Bible

Story Bible xây world theo causal logic:

```text
natural law
→ scarce resource
→ institution / incentive
→ social behavior
→ conflict
→ story utility
```

World phải trả lời được:

- linh khí/tài nguyên đến từ đâu;
- cảnh giới thay đổi bản chất gì;
- tông môn/gia tộc kiếm tài nguyên thế nào;
- ai sản xuất đan/pháp bảo;
- hàng hóa/tin tức di chuyển thế nào;
- cường giả bị giới hạn bởi gì;
- vì sao thế lực mạnh chưa nuốt toàn bộ thế giới.

## 4.2 Style Bible

Ngoài anti-AI blacklist, Style Bible phải có **positive prose targets**:

- awkward conversation;
- interruption;
- unfinished sentence;
- practical humor;
- embarrassment;
- irrational attachment;
- sensory messiness;
- misunderstanding;
- silence;
- spontaneous choice;
- physical inconvenience;
- asymmetrical emotion.

Không dùng như quota.

### Calibration

Không auto-calibrate chỉ từ Chương 1–3.

Chỉ khóa calibration khi có:

- 4–6 final/approved samples;
- ít nhất 4 Narrative Engine khác nhau;
- narration + dialogue + pressure/wonder phù hợp truyện.

Mỗi batch/chapter xoay 2–3 sample phù hợp để tránh style collapse.

## 4.3 Characters Bible

Character DNA gồm:

- desire / fear / wound;
- shame / value / blind spot;
- decision heuristic;
- speech fingerprint;
- emotional tells;
- cultivation philosophy;
- forbidden behavior;
- arc vector;
- **human irrationality profile**;
- **costly mistake pattern**.

Nhân vật thông minh vẫn có thể:

- sĩ diện;
- sợ mất mặt;
- tiếc đồ;
- sunk cost;
- tin nhầm người quen;
- chọn sai vì dữ liệu thiếu;
- phản ứng phòng vệ khi xấu hổ;
- impulsive kindness;
- irrational loyalty.

Không làm nhân vật ngu để chạy plot.

Đặc biệt MC không được chỉ “đề xuất sai rồi người khác sửa trước khi mất gì”. Blind spot có thể tạo cost thật: tiền, thời gian, quan hệ, thương tích, cơ hội, địa vị hoặc self-image.

## 4.4 Story Promise Controller

Master Outline khóa **3–5 lời hứa với độc giả**.

Mỗi promise phải có:

- Promise ID;
- reader promise;
- why reader came;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- long-range escalation.

Ví dụ:

```text
PR001 — Family Rise
PR002 — Cultivation Wisdom
PR003 — Old Ancestor Second Life
PR004 — Institutional Conflict
```

hoặc:

```text
PR001 — Loot Dopamine
PR002 — Cultivation Progression
PR003 — Corpse Mystery
PR004 — Hidden Conspiracy
```

### ADVANCE ≠ PAY

Ví dụ:

```text
“sắp sửa công pháp” = ADVANCE
hậu bối luyện bản sửa và nhận kết quả thật = PAY
```

Nếu 2–3 chương không PAY bất kỳ core promise nào, Reader Retention Editor phải cảnh báo.

## 4.5 Arc Outline

Arc Outline quản:

- arc question;
- promise PAY windows;
- conflict ladder;
- costly mistake opportunities;
- cultivation plan;
- Xianxia Experience;
- Emotional Residue;
- mystery/reveal;
- faction moves;
- Narrative Engine distribution;
- ending-shape distribution.

Outline là kế hoạch, không phải canon.

---

# 5. Narrative Engine

Pipeline không chỉ gắn nhãn chapter bằng topic `cultivation / investigation / relationship`.

Narrative Engine mô tả **cách chapter tạo chuyển động**.

Ví dụ:

```text
Q&A meeting
audit
negotiation
hypothesis-test
training calibration
chase
reveal
ritual
domestic
combat
grief
wonder
investigation
survival task
repair/build
travel discovery
aftermath
rescue
moral choice
competition
```

Không phải enum đóng.

### Rule quan trọng

Trong rolling window 4 chapter:

```text
3/4 cùng primary Narrative Engine = MAJOR pacing risk
```

Ba chapter `audit nhân sự / audit tài chính / audit thị trường` vẫn có thể là cùng engine dù topic khác.

QC cũng theo dõi dialogue geometry:

```text
A hỏi → B trả lời → MC kết luận
```

và investigation geometry:

```text
quan sát → giả thuyết → kiểm chứng → kết luận
```

Nếu lặp, phải sửa structure chứ không chỉ đổi từ.

---

# 6. Xianxia Experience Controller

World logic không thay thế fantasy experience.

Pipeline theo dõi riêng:

- cultivation payoff;
- wonder / awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- dao/cultivation insight có consequence;
- magical craft;
- world-scale glimpse.

Không quota mỗi chương.

Nhưng nếu nhiều chương chỉ có logistics, họp, giấy tờ, investigation đời thường mà không có trải nghiệm tiên hiệp, Reader Retention Editor cảnh báo.

`Nói về tu luyện` không tự động là `cultivation payoff`.

---

# 7. Emotional Residue

Không cần khóc mỗi chương.

Nhưng trong rolling 3–5 chapter cần có ít nhất một thay đổi thật về:

- emotional state;
- relationship meaning;
- self-image;
- shame/fear/grief/joy/attachment;
- meaning của object/place/memory.

Nếu chỉ inventory/knowledge/cultivation đổi còn con người đứng yên, pipeline cảnh báo.

---

# 8. Quy trình viết một chương

```text
Context Assembly
 ↓
Scene Plan
 ↓
Draft
 ↓
Continuity Auditor
 ↓
Reader Retention Editor
 ↓
Style Fingerprint Auditor
 ↓
Aggregate QC
 ↓
Rewrite
 ↓
Critical Re-QC
 ↓
Rolling 3-Chapter Audit if due
 ↓
Final
 ↓
Story Memory + Reader Experience Update
```

## Stage A — Context Assembly

Đọc tối thiểu:

- seed;
- bibles;
- Story Promise section;
- arc hiện tại;
- current_state;
- reader_experience;
- canon;
- cultivation;
- knowledge;
- unresolved threads;
- recent summaries;
- final gần nhất;
- full 2–3 chapter gần nhất khi cần audit repetition.

## Stage B — Scene Plan

Tạo:

```text
stories/<slug>/chapters/NNNN/scene_plan.md
```

### Không over-plan

Không bắt mọi scene phải có đủ:

```text
goal + obstacle + stakes + turn + choice + consequence + state delta
```

Có hai mode.

#### Conflict / Transaction Scene

Có thể plan goal, opposing agenda, stakes, leverage, turn, consequence.

#### Quiet / Discovery / Emotional Scene

Chỉ cần những phần relevant:

- focal tension / curiosity;
- sensory anchor;
- knowledge boundary;
- human friction;
- perception/emotional movement;
- unresolved movement / exit image.

Một scene tĩnh vẫn có giá nếu tạo relationship texture, emotional residue, wonder, character revelation hoặc meaning shift.

## Stage C — Draft

```text
stories/<slug>/chapters/NNNN/draft.txt
```

Draft là prose hoàn chỉnh, chưa release.

## Stage D1 — Continuity Auditor

```text
continuity_report.md
```

Chỉ kiểm:

- canon;
- timeline;
- geography;
- power/cultivation;
- techniques/items;
- injuries/fatigue;
- knowledge;
- relationships/factions;
- POV boundary;
- hard Character DNA contradiction.

Reviewer này **không** quyết chapter có cuốn không.

## Stage D2 — Reader Retention Editor

```text
reader_retention_report.md
```

Kiểm:

- Story Promise ADVANCE/PAY/drought;
- Narrative Engine;
- 3/4 repetition rule;
- opening/mid movement/drag;
- conflict solution repetition;
- agency/humanity;
- costly mistake realism;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

## Stage D3 — Style Fingerprint Auditor

```text
style_fingerprint_report.md
```

Bắt:

- `Không X. Mà Y.`;
- short-negation paragraphs;
- `Đúng / Nhưng / Vậy / Cho nên` argument rhythm;
- Q&A cleanliness;
- hypothesis-loop;
- aphorism density;
- narrator conclusion endings;
- paragraph cadence;
- lexical/rhetorical tics;
- calibration drift.

## Stage D4 — Aggregate Quality Gate

```text
quality_report.md
```

Không được PASS nếu bất kỳ reviewer nào còn BLOCKER/MAJOR.

Continuity PASS không được “nuốt” Retention MAJOR.

## Stage E — Rewrite

```text
rewrite.txt
```

Rewrite toàn chapter, không patch list.

Nếu issue là structural repetition, phải đổi engine/geometry/scene construction; không synonym-spin.

## Stage F — Critical Re-QC

Rerun reviewer bị ảnh hưởng khi rewrite lớn.

## Stage G — Rolling 3-Chapter Audit

Trước final chapter:

```text
3, 6, 9, 12, 15...
```

đọc full:

- N-2 final;
- N-1 final;
- N rewrite candidate.

Tạo:

```text
rolling_3_chapter_audit.md
```

So:

- opening shape;
- Narrative Engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- Story Promise PAY;
- Xianxia Experience;
- Emotional Residue.

Nếu current N tạo MAJOR repetition, sửa N. Không retcon hai final trước chỉ để tạo variety.

## Stage H — Final

```text
stories/<slug>/final/Chương N: <Tiêu đề>.txt
```

Final chỉ chứa truyện.

## Stage I — Memory Update

Sau final cập nhật cả:

- Story State Memory;
- `reader_experience.md`.

Không sang chapter mới nếu một trong hai còn đứng ở chapter trước.

---

# 9. Reader Experience Memory

File:

```text
memory/reader_experience.md
```

Theo dõi:

- last_major_payoff;
- Story Promise last ADVANCE/PAY/drought;
- last_wonder_beat;
- last_emotional_hit;
- last_costly_mistake;
- recent primary/secondary engines;
- recent dialogue geometries;
- recent ending shapes;
- recent rhetorical tics;
- Xianxia Experience;
- reader appetite / payoff debt;
- calibration rotation.

Đây **không phải canon**.

Nó giúp planner biết không chỉ “chuyện gì đã xảy ra” mà còn “độc giả vừa trải qua kiểu chapter nào”.

---

# 10. Batch 10 chương

Lệnh chuẩn:

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

Bắt buộc tuần tự:

```text
Ch. N
plan
→ draft
→ 3 reviewer QC
→ aggregate
→ rewrite
→ rolling audit nếu đến kỳ
→ final
→ story + reader memory

Ch. N+1
đọc memory mới
→ lặp
```

Không viết 10 draft rồi update memory cuối batch.

## Batch Audit

Cuối batch bắt buộc tạo:

```text
stories/<slug>/chapters/batch_NNNN_NNNN_audit.md
```

Audit tối thiểu:

- artifact completion;
- arc progress;
- Story Promise PAY/drought;
- Narrative Engine distribution;
- Xianxia Experience;
- Emotional Residue;
- continuity;
- Character DNA/human irrationality;
- power progression;
- style fingerprints;
- setup/payoff;
- next-batch handoff.

### Completion rule

```text
10 final files != batch complete
```

Batch chỉ complete khi:

- đủ final;
- mọi chapter có required QC artifacts;
- rolling audits tồn tại ở chapter 3/6/9/...;
- story memory current;
- reader_experience current;
- batch audit tồn tại;
- arc revision đã xử lý nếu cần.

Thiếu một artifact bắt buộc:

```text
INCOMPLETE
```

Orchestrator không được báo PASS/ready.

---

# 11. Memory System

## Story State Memory

### `current_state.md`

Snapshot chapter hiện tại.

### `canon_ledger.md`

Fact đã khóa.

### `timeline.md`

Thời gian, di chuyển, hồi phục, bế quan, deadline.

### `character_states.md`

State động + costly mistake residue.

### `relationships.md`

Trust, respect, affection, fear, resentment, obligation, leverage.

### `cultivation_ledger.md`

Realm, techniques, bottleneck, resources, breakthrough setup.

### `inventory_artifacts.md`

Ownership, quantity, state, consumables, artifacts.

### `factions_locations.md`

Faction state + location/travel.

### `knowledge_ledger.md`

Ai biết gì; truth/belief/rumor/partial.

### `foreshadowing.md`

Setup/payoff.

### `unresolved_threads.md`

Open/active/resolved threads.

### `chapter_summaries.md`

Structured retrieval summary.

## Reader Layer

### `reader_experience.md`

Production pattern memory như phần trên.

Chi tiết format:

```text
memory/MEMORY_SYSTEM.md
```

---

# 12. Source of Truth

Khi canon/state mâu thuẫn:

```text
1. Canon Ledger
2. Final chapters
3. Bible
4. Story Memory
5. Arc Outline
6. Master Outline
7. Seed
8. Draft / Scene Plan
```

Reader Experience Memory không override canon.

```text
Outline = kế hoạch
Final = sự kiện đã xảy ra
Canon Ledger = fact đã khóa
Reader Experience = pattern production gần đây
```

---

# 13. Resume trong chat mới

Lệnh:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.
Tiếp tục truyện ở branch story/<slug> và viết batch 10 chương tiếp theo.
```

ChatGPT phải đọc/verify:

```text
AGENTS.md
seed
master Story Promises
current_state
reader_experience
batch audit gần nhất
arc hiện tại
bibles
recent summaries/finals
artifact tree chapter gần nhất
```

Không dựa vào memory hội thoại cũ.

---

# 14. Resume khi dừng giữa chapter

## Scene plan có, draft chưa có

Resume Draft.

## Draft có, reviewer report thiếu

Resume đúng reviewer còn thiếu.

## 3 reviewer report có, aggregate thiếu

Resume Aggregate QC.

## QC yêu cầu rewrite, rewrite chưa có

Resume Rewrite.

## Rewrite có, rolling audit đến kỳ nhưng thiếu

Chạy Rolling Audit trước final.

## Final có, story memory thiếu

Update story memory.

## Story memory current, reader_experience thiếu

Vẫn INCOMPLETE. Update reader memory.

## 10 finals có nhưng batch audit thiếu

Batch vẫn INCOMPLETE. Tạo batch audit.

---

# 15. Các lệnh thường dùng

## Tạo truyện mới

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

## Xây bible

```text
Xây Story Bible, Style Bible và Characters Bible từ seed hiện tại. Chưa viết chương.
```

## Xây outline

```text
Dựa trên bible hiện tại, khóa Story Promises, lập Master Outline và Arc 1. Không viết chương.
```

## Viết một chapter

```text
Viết chương tiếp theo qua đủ pipeline v2.
```

## Viết batch

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW.
```

## Audit continuity

```text
Audit continuity 20 chương gần nhất: canon, timeline, knowledge, inventory, relationships, power.
```

## Audit reader retention

```text
Audit 10 chương gần nhất: Story Promise PAY, Narrative Engine, Xianxia Experience, Emotional Residue và ending patterns.
```

## Audit style fingerprint

```text
Audit 10 chương gần nhất: rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph rhythm và calibration drift.
```

## Audit Character DNA

```text
Kiểm Character DNA drift, human irrationality và costly mistake pattern của 20 chương gần nhất.
```

## Audit power scaling

```text
Kiểm power scaling 30 chương gần nhất.
```

## Adjust outline

```text
Đọc final + memory mới nhất và cập nhật Arc Outline theo state thật. Không retcon final.
```

---

# 16. Quy tắc văn phong

Pipeline ưu tiên:

- nhịp câu biến thiên;
- Hán Việt đúng chỗ;
- cảm xúc qua hành vi;
- hội thoại có địa vị + DNA + human friction;
- worldbuilding qua action/consequence;
- chiến đấu có position/resource/cost;
- độc giả tự suy ra khi đã đủ dữ liệu;
- positive prose texture organic.

Cảnh giác:

- `lúc này / ngay sau đó / cùng lúc đó`;
- `không khỏi / hiển nhiên / rõ ràng`;
- spam ánh mắt/khóe môi/khí tức;
- `Không X. Mà Y.` lặp;
- phủ định ngắn đứng riêng quá dày;
- `Đúng / Nhưng / Vậy / Cho nên` thành nhịp máy;
- aphorism density;
- Q&A quá sạch;
- hypothesis-loop;
- mọi chapter cùng ending;
- mọi conflict cùng giải pháp;
- cheat giải quyết mọi vấn đề.

---

# 17. Quy tắc power scaling

Khi đánh giá chiến đấu:

```text
realm
+ foundation
+ technique mastery
+ equipment
+ bloodline / physique
+ dao comprehension
+ battle experience
+ current injuries
+ resource expenditure
+ environment
+ information advantage
+ matchup
```

Vượt cấp phải có mechanism và cost cụ thể.

Special trait / cheat không được thành đáp án cho mọi conflict.

---

# 18. GitHub Workflow

## Framework

```text
main
```

Chỉ sửa `main` khi cải tiến pipeline.

## Story

```text
story/<slug>
```

Story artifact không ghi lên `main`.

### Lưu ý framework upgrade

Story branch đã tạo trước upgrade **không tự động nhận file mới từ main**.

Khi tiếp tục story cũ, Orchestrator phải kiểm framework artifacts thực tế. Nếu cần dùng pipeline v2 đầy đủ, phải sync/migrate framework theo yêu cầu người dùng.

---

# 19. Stop Conditions

Pipeline dừng trước final nếu:

- canon conflict cần retcon;
- `user_must_decide` chưa có đáp án và ảnh hưởng trực tiếp;
- outcome phá hard world/character/power rule;
- một trong ba reviewer còn BLOCKER/MAJOR;
- rolling audit đến kỳ nhưng thiếu/còn MAJOR;
- title/final state không xác định hợp lệ.

Không dừng chỉ vì một creative blank có thể giải quyết an toàn.

---

# 20. Tài liệu framework

```text
AGENTS.md
```
Luật vận hành bắt buộc.

```text
docs/ARCHITECTURE.md
```
Kiến trúc pipeline.

```text
docs/READER_EXPERIENCE_SYSTEM.md
```
Story Promise, Narrative Engine, Rolling Audit, Xianxia Experience, Emotional Residue, Human Irrationality và Calibration policy.

```text
docs/GITHUB_CHATGPT_PROTOCOL.md
```
Branch safety, state machine, resume và artifact gate.

```text
docs/BATCH_10_WORKFLOW.md
```
Batch workflow chi tiết.

```text
memory/MEMORY_SYSTEM.md
```
Story + Reader memory.

```text
prompts/PIPELINE_PROMPTS.md
```
Role contracts.

Templates chính:

```text
templates/seed.template.yaml
templates/story_bible.template.md
templates/style_bible.template.md
templates/characters_bible.template.md
templates/master_outline.template.md
templates/arc_outline.template.md
templates/chapter_scene.template.md
templates/continuity_report.template.md
templates/reader_retention_report.template.md
templates/style_fingerprint_report.template.md
templates/quality_report.template.md
templates/rolling_3_chapter_audit.template.md
templates/batch_audit.template.md
templates/reader_experience.template.md
```

---

# 21. Workflow khuyến nghị

```text
Phiên đầu
Seed → Genesis → Ch.1–10 → Batch Audit

Phiên sau
Read state + reader experience → Ch.11–20 → Batch Audit

Phiên sau
Read state + reader experience → Ch.21–30 → Batch Audit
```

Sau vài batch:

```text
Audit continuity
Audit Story Promise debt
Audit Narrative Engine repetition
Audit Xianxia Experience drought
Audit Emotional Residue
Audit Character DNA / costly mistakes
Audit power scaling
Audit style fingerprint
Reconcile arc outline với final
```

---

# 22. Một câu lệnh mẫu đầy đủ

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.

Làm việc trên branch story/pham-nhan-cau-tien.
Đọc AGENTS.md, current_state, reader_experience, Story Promises, batch audit gần nhất, arc hiện tại, bible và memory liên quan.

Viết batch 10 chương tiếp theo.
Mỗi chương bắt buộc chạy tuần tự:
scene plan → draft → Continuity QC → Reader Retention QC → Style Fingerprint QC → aggregate → rewrite → rolling audit nếu đến kỳ → final → story + reader memory update.

Không bỏ memory giữa các chương.
Không retcon final.
Nếu arc kết thúc giữa batch, xây arc tiếp theo trước khi vượt boundary.
Cuối batch tạo batch audit và verify artifact completion gate.
```

Thông thường câu ngắn sau là đủ:

```text
Tiếp tục branch story/pham-nhan-cau-tien và viết batch 10 chương tiếp theo đúng pipeline.
```

---

## Nguyên tắc cuối cùng

```text
GitHub giữ sự thật.
Bible giữ luật.
Character DNA giữ con người.
Story Promise giữ lời hứa.
Outline giữ hướng đi.
Narrative Engine giữ độ đa dạng.
Xianxia Experience giữ chất tiên hiệp.
QC tách correctness khỏi reader taste.
Final giữ tác phẩm.
Story Memory giữ continuity.
Reader Experience Memory giữ nhịp trải nghiệm.
```

Không bỏ một lớp chỉ để viết nhanh hơn.
