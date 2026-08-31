# Architecture

## 1. Tổng quan

Xianxia Novel Maker được thiết kế cho mô hình **ChatGPT Web + GitHub connector**. GitHub giữ state bền vững; ChatGPT đọc state, tạo artifact, kiểm tra và ghi kết quả.

Từ pipeline v2, hệ thống quản hai thứ song song:

1. **Story correctness** — canon, continuity, power, knowledge, Character DNA.
2. **Reader experience** — Story Promise, Narrative Engine, Xianxia Experience, Emotional Residue và style fingerprint.

```text
Human Seed
   ↓
Story Genesis
   ├─ Story Bible
   ├─ Style Bible
   ├─ Characters Bible
   └─ Reader-promise candidates
   ↓
Long-range Planning
   ├─ Master Outline
   │   └─ lock 3–5 Story Promises
   └─ Arc Outline
       ├─ Promise PAY windows
       ├─ Narrative Engine map
       ├─ Xianxia Experience map
       └─ Emotional Residue plan
   ↓
Initialize Memory
   ├─ Story State Memory
   └─ Reader Experience Memory
   ↓
Chapter Loop (sequential)
   ├─ Context Assembly
   ├─ Scene Plan (relaxed modes)
   ├─ Draft
   ├─ Continuity Auditor
   ├─ Reader Retention Editor
   ├─ Style Fingerprint Auditor
   ├─ Aggregate Quality Gate
   ├─ Rewrite
   ├─ Critical Re-QC
   ├─ Rolling 3-Chapter Audit on Ch. 3/6/9/...
   ├─ Final TXT
   └─ Story + Reader Memory Commit
   ↓
Batch Audit every 10 chapters
```

Chi tiết controller: `docs/READER_EXPERIENCE_SYSTEM.md`.

## 2. Bốn lớp dữ liệu

### A. Immutable / slow-changing canon

Lưu tại `bible/` và `memory/canon_ledger.md`.

- bản chất thế giới;
- quy tắc tu luyện;
- lịch sử nền;
- hệ thống cảnh giới;
- cấu trúc quyền lực;
- Character DNA cốt lõi;
- style rules;
- canon fact đã xuất hiện trong final.

### B. Planning state

Lưu tại `outline/`.

- master outline: hướng truyện dài hạn + Story Promise contract;
- arc outline: mục tiêu, payoff, Narrative Engine, Xianxia Experience;
- chapter intent: target chưa final.

Planning state có thể điều chỉnh nếu final dẫn sang hướng khác, miễn không retcon canon.

### C. Fast-changing story memory

Lưu tại `memory/`:

- time/location;
- physical/emotional state;
- cultivation;
- inventory;
- relationships;
- knowledge;
- faction state;
- foreshadowing;
- unresolved threads.

### D. Reader Experience Memory

Lưu tại `memory/reader_experience.md`.

Theo dõi:

- Story Promise last ADVANCE/PAY/drought;
- last major payoff;
- recent primary/secondary Narrative Engines;
- dialogue geometry;
- recent ending shapes;
- recent rhetorical tics;
- Xianxia Experience delivered;
- last wonder beat;
- last emotional hit;
- last costly mistake;
- reader appetite / payoff debt;
- calibration rotation.

Reader Experience Memory **không phải canon** và không override final/Character DNA.

## 3. Story branch lifecycle

### 3.1 Create

Từ `main`, tạo:

`story/<slug>`

Framework source sống trên `main`. Story branch cũ không được mặc định đã nhận framework upgrade nếu chưa sync/verify.

### 3.2 Bootstrap

```text
stories/<slug>/
  seed/seed.yaml
  bible/
  outline/arcs/
  chapters/
  final/
  memory/
```

### 3.3 Genesis

Theo thứ tự:

1. validate seed + candidate reader promises;
2. story bible;
3. style bible;
4. characters bible;
5. master outline + lock 3–5 Story Promises;
6. arc 1 outline + Narrative Engine/Xianxia/Emotional maps;
7. initialize Story State Memory;
8. initialize Reader Experience Memory.

### 3.4 Production

Viết tuần tự. Mỗi chương là transaction hoàn chỉnh.

### 3.5 Rolling checkpoint

Trước final các chương `3, 6, 9, 12...`, chạy Rolling 3-Chapter Audit.

### 3.6 Batch checkpoint

Cứ 10 chương bắt buộc có:

`chapters/batch_XXXX_XXXX_audit.md`

Không có file audit → batch `INCOMPLETE`.

## 4. Context Assembly Engine

Vì context hữu hạn, đọc theo tầng.

### Tier 0 — always read

- seed;
- story bible;
- style bible;
- master Story Promise section;
- arc hiện tại;
- current state;
- reader experience;
- canon ledger;
- chapter summaries gần nhất.

### Tier 1 — scene-specific

- Character DNA nhân vật xuất hiện;
- cultivation ledger;
- knowledge ledger;
- relationship records;
- faction/location records;
- unresolved threads;
- foreshadowing setup sắp payoff.

### Tier 2 — historical retrieval

Đọc full final cũ khi:

- callback cụ thể;
- continuity checker nghi vấn;
- lời thoại/chi tiết phải nhắc chính xác;
- Reader Retention/Style Fingerprint cần so cấu trúc;
- Rolling 3-Chapter Audit bắt buộc full N-2/N-1.

Mục tiêu: **đủ context đúng**, không phải nhiều context nhất.

## 5. Story Promise architecture

Master Outline khóa 3–5 promise.

Mỗi promise có:

- ID;
- reader promise;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

### Important distinction

`ADVANCE` là chuẩn bị.

`PAY` là độc giả thật sự nhận được:

- thành quả;
- reveal;
- capability change;
- emotional resolution;
- threshold crossing;
- trải nghiệm premise đã hứa.

Nếu 2–3 chapter không PAY core promise nào, Reader Retention Editor phải cảnh báo.

## 6. Narrative Engine architecture

Topic không đủ để đo pacing.

`Narrative Engine` mô tả cách chapter tạo chuyển động.

Ví dụ:

`Q&A meeting / audit / negotiation / hypothesis-test / training calibration / chase / reveal / ritual / domestic / combat / grief / wonder / investigation / survival task / repair-build / travel discovery / aftermath / rescue / moral choice / competition`.

Vocabulary không đóng.

### Rolling rule

Trong 4 chapter:

**3/4 cùng primary engine = MAJOR pacing risk.**

Không được coi ba chapter audit về ba topic khác nhau là variety.

## 7. Xianxia Experience architecture

Worldbuilding logic và fantasy experience là hai trục khác nhau.

Theo dõi:

- cultivation payoff;
- wonder/awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- dao insight có consequence;
- magical craft;
- world-scale glimpse.

Không quota cứng. Controller tồn tại để phát hiện drought, đặc biệt khi arc bị kéo vào logistics/administration/investigation thuần lý trí.

## 8. Emotional Residue architecture

Rolling 3–5 chapter nên có ít nhất một thay đổi thật về:

- emotional state;
- relationship meaning;
- self-image;
- grief/joy/shame/fear/attachment;
- meaning của object/place/memory.

Không bắt mỗi chapter phải melodrama.

Nếu chỉ inventory/knowledge/cultivation đổi còn con người đứng yên, Reader Retention Editor cảnh báo.

## 9. Character engine

Character Bible gồm:

### Core DNA

- desire/fear/wound;
- decision heuristic;
- speech fingerprint;
- value/blind spot;
- cultivation philosophy;
- forbidden behavior.

### Human irrationality profile

- pride trigger;
- shame/fear of losing face;
- sentimental attachment;
- sunk cost;
- bias under incomplete data;
- trust/distrust distortions;
- self-justification.

### Costly mistake pattern

Protagonist/supporting cast có thể sai theo DNA và chịu cost thật.

Không dùng “thông minh” để biến mọi nhân vật thành operations expert. Không dùng “humanity” để làm họ ngu chạy plot.

### Runtime state

Lưu trong memory:

- goal;
- relationship;
- injury;
- emotional residue;
- costly mistake scar;
- known information.

## 10. Scene planning architecture

Pipeline v2 bỏ rule “mọi scene phải có goal + obstacle + stakes + turn + choice + consequence + state delta”.

Có hai mode:

### Conflict / Transaction

Dùng structure plot rõ khi thực sự có opposing agenda.

### Quiet / Discovery / Emotional

Có thể chỉ cần:

- focal tension/curiosity;
- sensory anchor;
- knowledge boundary;
- human friction;
- perception/emotional movement;
- unresolved movement / exit image.

Scene không đổi canon vẫn có thể có giá nếu đổi **meaning, relationship texture, wonder hoặc emotional residue**.

## 11. Positive style architecture

Anti-AI blacklist không đủ.

Style Bible còn định nghĩa texture tích cực:

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

Không khóa calibration chỉ từ Ch.1–3.

Valid set:

- 4–6 approved/final samples;
- ít nhất 4 Narrative Engine khác nhau;
- narration + dialogue + pressure/wonder.

Mỗi batch/chapter xoay 2–3 sample phù hợp để tránh style collapse.

## 12. Memory model

Story State Memory gồm:

- `current_state.md`;
- `canon_ledger.md`;
- `timeline.md`;
- `character_states.md`;
- `relationships.md`;
- `cultivation_ledger.md`;
- `inventory_artifacts.md`;
- `factions_locations.md`;
- `knowledge_ledger.md`;
- `foreshadowing.md`;
- `unresolved_threads.md`;
- `chapter_summaries.md`.

Reader layer:

- `reader_experience.md`.

Chi tiết format: `memory/MEMORY_SYSTEM.md`.

## 13. Worldbuilding engine

Story Bible dùng causal chain:

`natural law → resource scarcity → institution → incentive → behavior → conflict → story utility`.

Mỗi ý tưởng thế giới phải thay đổi đời sống/xung đột, không chỉ làm lore dày.

## 14. Power system engine

Mỗi realm cần:

- qualitative change;
- quantitative range;
- abilities;
- limitations;
- resource cost;
- breakthrough condition;
- failure mode;
- social meaning;
- lifespan;
- realistic cross-realm exceptions.

Nếu vượt cấp, phải có lý do được ledger hóa: counter, artifact, terrain, injury, bloodline, ambush, sacrificial cost, superior foundation, information advantage...

## 15. Outline architecture

### Master Outline

Khóa:

- premise;
- 3–5 Story Promises;
- long-range question;
- sagas;
- irreversible turns;
- protagonist transformation;
- antagonistic forces;
- cultivation + Xianxia spine;
- ending direction.

### Arc Outline

Chi tiết:

- arc question;
- promise PAY windows;
- conflict ladder;
- costly mistake opportunities;
- cultivation;
- Xianxia Experience;
- Emotional Residue;
- reveals;
- faction moves;
- Narrative Engine distribution;
- ending-shape map.

Arc có thể đổi sau final/batch audit; canon thắng planning.

## 16. Chapter transaction

```text
READ story + reader context
→ PLAN scene
→ DRAFT
→ CONTINUITY AUDIT
→ RETENTION AUDIT
→ STYLE FINGERPRINT AUDIT
→ AGGREGATE QC
→ REWRITE
→ CRITICAL RE-QC
→ ROLLING 3-CH AUDIT if due
→ WRITE final
→ UPDATE story memory
→ UPDATE reader experience
→ COMMIT
```

Nếu bất kỳ required memory/artifact nào thất bại, transaction chưa hoàn tất.

## 17. QC architecture

### Continuity Auditor

Chỉ kiểm correctness:

- canon;
- timeline;
- distance;
- realm;
- technique;
- item;
- injury;
- knowledge;
- relationship/faction state;
- POV boundary.

### Reader Retention Editor

Chỉ kiểm reading experience:

- Story Promise PAY/drought;
- Narrative Engine;
- opening/drag;
- agency/humanity;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

### Style Fingerprint Auditor

Chỉ kiểm recurring prose fingerprints:

- `Không X. Mà Y.`;
- Q&A cleanliness;
- hypothesis-loop;
- aphorism density;
- paragraph rhythm;
- lexical/rhetorical tics;
- calibration drift.

### Aggregate Gate

Không reviewer nào được “nuốt” reviewer khác.

Continuity PASS + Retention MAJOR = vẫn rewrite.

## 18. Rolling 3-Chapter Audit

Trước final `3/6/9/12...`:

- đọc full N-2;
- full N-1;
- rewrite candidate N.

So:

- opening shape;
- engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- promises;
- xianxia;
- emotion.

Nếu current N tạo MAJOR pattern, sửa N. Không retcon hai final trước chỉ để tạo variety.

## 19. Orchestration gate

Orchestrator không được báo complete dựa trên ý định hoặc lời chat.

### Chapter required

- scene plan;
- draft;
- 3 reviewer reports;
- aggregate QC;
- rewrite nếu required;
- rolling audit nếu due;
- final;
- story memory;
- reader memory.

### Batch required

- requested finals;
- all chapter gates;
- final memories;
- batch audit;
- arc revision if needed;
- next-batch handoff.

Thiếu artifact = `INCOMPLETE`.

## 20. Human control points

Người dùng có quyền dừng/chỉnh ở:

- seed validation;
- story bible;
- character bible;
- master Story Promises;
- master outline;
- arc outline;
- batch audit.

Nếu user lệnh tự chạy batch, ChatGPT không cần hỏi lại từng chapter trừ conflict canon thật sự không thể giải quyết.

## 21. Failure handling

### Missing canon

Không bịa chi tiết ảnh hưởng lớn. Chọn phương án không khóa canon mới hoặc ghi assumption trong planning artifact.

### Outline contradiction

Final/canon thắng. Sửa future outline.

### Character drift

Dùng DNA + human irrationality profile để phân biệt phát triển thật với hành vi phục vụ plot.

### Power scaling conflict

Ưu tiên ledger. Thay mechanism of victory, không phá luật.

### Reader experience drift

Không retcon final chỉ vì engine/promise drought. Sửa chapter hiện tại chưa final hoặc future arc beats.

### Context too large

Dùng summary + ledger + reader experience + targeted full-final retrieval.

## 22. Design principle

Pipeline tối ưu cho:

**continuity + prose quality + reader retention + xianxia experience + controllability**.

Không tối ưu cho tốc độ token và không biến truyện thành một bài toán operations hoàn hảo. Logic phải chắc, nhưng nhân vật vẫn được phép sai, thương, tiếc, xấu hổ, bất ngờ và trả giá.
