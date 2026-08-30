# Architecture

## 1. Tổng quan

Xianxia Novel Maker được thiết kế cho mô hình **ChatGPT Web + GitHub connector**, không phụ thuộc một backend riêng. GitHub giữ toàn bộ state bền vững; ChatGPT đọc state, tạo artifact, kiểm tra và ghi lại kết quả.

```text
Human Seed
   ↓
Story Genesis
   ├─ Story Bible
   ├─ Style Bible
   └─ Characters Bible
   ↓
Long-range Planning
   ├─ Master Outline
   └─ Arc Outline
   ↓
Chapter Loop (sequential)
   ├─ Context Assembly
   ├─ Scene Plan
   ├─ Draft
   ├─ Data/Continuity QC
   ├─ Style/Character QC
   ├─ Rewrite
   ├─ Final TXT
   └─ Memory Commit
   ↓
Batch Audit every 10 chapters
```

## 2. Ba lớp dữ liệu

### A. Immutable / slow-changing canon

Lưu tại `bible/` và `memory/canon_ledger.md`.

Dữ liệu này thay đổi hiếm và phải có lý do rõ ràng:

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

- master outline: hướng truyện dài hạn;
- arc outline: mục tiêu, biến chuyển, payoff trong một arc;
- chapter intent: mục tiêu dự kiến của từng chương.

Planning state có thể điều chỉnh nếu diễn biến final dẫn đến hướng tốt hơn, miễn không retcon canon.

### C. Fast-changing runtime memory

Lưu tại `memory/`.

- vị trí hiện tại;
- thời điểm;
- trạng thái cơ thể / tinh thần;
- tiến độ tu luyện;
- vật phẩm;
- quan hệ;
- bí mật ai biết;
- lời hứa / nhiệm vụ / nợ;
- faction standing;
- foreshadowing;
- unresolved threads.

Runtime memory phải cập nhật sau **mỗi chương**, không đợi hết arc.

## 3. Story branch lifecycle

### 3.1 Create

Từ `main`, tạo branch:

`story/<slug>`

Ví dụ:

`story/pham-nhan-nghich-thien`

### 3.2 Bootstrap

Tạo cây:

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

1. validate seed;
2. story bible;
3. style bible;
4. characters bible;
5. master outline;
6. arc 1 outline;
7. initialize memory.

### 3.4 Production

Viết tuần tự các chương. Mỗi chương là một vòng transaction hoàn chỉnh.

### 3.5 Batch checkpoint

Cứ 10 chương tạo `chapters/batch_XXXX_XXXX_audit.md` hoặc cập nhật checkpoint tương đương.

## 4. Context Assembly Engine

Vì context ChatGPT hữu hạn, không đọc toàn bộ truyện mỗi lần. Trước một chương, context được assemble theo tầng.

### Tier 0 — always read

- seed;
- story bible;
- style bible;
- arc hiện tại;
- current state;
- canon ledger;
- chapter summaries gần nhất.

### Tier 1 — scene-specific

- Character DNA nhân vật xuất hiện;
- cultivation ledger liên quan;
- knowledge ledger liên quan;
- relationship records liên quan;
- faction/location records liên quan;
- unresolved thread liên quan;
- foreshadowing setup sắp payoff.

### Tier 2 — historical retrieval

Chỉ đọc full final cũ khi:

- cần callback cụ thể;
- lời hứa / manh mối xuất hiện trước đó;
- chi tiết hội thoại phải nhắc lại chính xác;
- continuity checker phát hiện nghi vấn.

Mục tiêu: **đủ context đúng**, không phải nhiều context nhất.

## 5. Memory model

Memory chia thành 11 ledger độc lập để giảm drift.

### `current_state.md`
Snapshot đầu vào cho chương kế tiếp:

- current chapter;
- current arc;
- date/time;
- location;
- POV candidate;
- immediate goals;
- active danger;
- recent consequences.

### `canon_ledger.md`
Fact đã khóa. Mỗi entry nên có:

- ID;
- fact;
- introduced chapter;
- evidence;
- scope;
- mutable?;
- notes.

### `timeline.md`
Sự kiện theo thứ tự thời gian, có khoảng thời gian di chuyển / tu luyện khi quan trọng.

### `character_states.md`
State động từng nhân vật:

- location;
- physical;
- emotional;
- short-term goal;
- known secrets;
- current alliances;
- injuries;
- debt/promises;
- last seen chapter.

### `relationships.md`
Quan hệ là vector, không chỉ label:

- trust;
- affection;
- fear;
- respect;
- resentment;
- obligation;
- leverage;
- public vs private relation.

### `cultivation_ledger.md`
Cho mỗi nhân vật tu luyện:

- realm;
- subrealm;
- foundation quality;
- techniques;
- mastery;
- dao comprehension;
- resources;
- bottleneck;
- combat modifiers;
- breakthrough constraints.

### `inventory_artifacts.md`
Ownership + trạng thái vật phẩm:

- owner;
- location;
- quantity;
- charge/durability;
- known functions;
- hidden functions;
- acquisition chapter;
- last use.

### `factions_locations.md`
State tổ chức và địa điểm:

- leadership;
- alignment;
- resources;
- current conflicts;
- relation to protagonist;
- spatial constraints;
- travel connections.

### `knowledge_ledger.md`
Ngăn nhân vật biết điều họ chưa thể biết:

- information atom;
- holders;
- source;
- confidence;
- false belief / true fact;
- revealed chapter.

### `foreshadowing.md`
- setup ID;
- planted chapter;
- surface meaning;
- intended payoff window;
- status: dormant / reinforced / paid / abandoned-with-reason.

### `unresolved_threads.md`
- thread;
- origin;
- urgency;
- characters involved;
- next pressure point;
- target arc;
- status.

### `chapter_summaries.md`
Mỗi chương 8–15 bullet có cấu trúc, chỉ ghi sự kiện có giá trị truy hồi.

## 6. Worldbuilding engine

Story Bible không sinh thế giới bằng cách “điền form”. Quy trình bắt buộc dùng **causal chain**.

Ví dụ:

`Linh khí tập trung theo địa mạch`
→ tông môn chiếm linh sơn
→ phàm nhân tụ cư dưới chân núi để giao thương
→ tuyến vận chuyển linh thạch trở thành mục tiêu cướp bóc
→ thương hội thuê tán tu hộ tống
→ luật tông môn về đường bay xuất hiện
→ xung đột kinh tế và địa chính trị tự nhiên.

Mỗi ý tưởng thế giới phải trả lời ít nhất một câu: **nó làm thay đổi đời sống hoặc xung đột như thế nào?**

## 7. Power system engine

Không dùng cảnh giới chỉ như level number.

Mỗi realm cần:

- qualitative change: thay đổi bản chất gì;
- quantitative range: mạnh hơn ra sao;
- abilities unlocked;
- limitations;
- resource cost;
- breakthrough condition;
- failure mode;
- social meaning;
- expected lifespan;
- realistic cross-realm exceptions.

### Cross-realm rule

Nếu nhân vật vượt cấp chiến đấu, phải có lý do được ledger hóa, ví dụ:

- technique tương khắc;
- artifact;
- terrain;
- opponent injured;
- bloodline/physique;
- ambush;
- sacrificial cost;
- superior foundation.

Không được dùng “thiên tài nên thắng” như lý do duy nhất.

## 8. Character engine

Character Bible gồm hai lớp:

### Core DNA — chậm thay đổi

Giá trị, vết thương, nỗi sợ, cách ra quyết định, giọng nói, philosophy.

### Runtime state — đổi theo chương

Mục tiêu hiện tại, quan hệ, thương tích, nghi ngờ, thông tin đang biết, nguồn lực.

Nhờ tách hai lớp, nhân vật có thể phát triển mà không mất bản sắc.

## 9. Outline architecture

### Master Outline

Không bắt buộc khóa từng chương cho hàng nghìn chương. Chỉ khóa:

- premise;
- long-term dramatic question;
- major eras / sagas;
- major irreversible turns;
- protagonist transformation;
- major antagonistic forces;
- ending direction;
- non-negotiable setups/payoffs.

### Arc Outline

Chi tiết hơn:

- arc question;
- start state;
- end state;
- conflict ladder;
- character turns;
- cultivation progression;
- reveals;
- setup/payoff;
- chapter beats.

Arc có thể điều chỉnh sau batch audit.

## 10. Chapter transaction

Một chương được coi là transaction atomic:

```text
READ context
→ PLAN scene
→ DRAFT
→ QC
→ REWRITE
→ RE-QC critical issues
→ WRITE final
→ UPDATE memory
→ COMMIT
```

Nếu memory update thất bại, transaction chưa hoàn tất.

## 11. QC architecture

QC gồm hai pass độc lập về mục tiêu.

### Data QC

Tìm contradictions:

- canon;
- time;
- distance;
- realm;
- technique;
- item;
- injury;
- knowledge;
- relationship;
- faction state.

### Narrative QC

Tìm defects:

- POV leakage;
- character drift;
- low-causality scene;
- exposition dump;
- generic emotion;
- repetitive diction;
- AI-like rhythm;
- dialogue sameness;
- weak transition;
- unjustified reveal;
- flat ending.

Sau rewrite chỉ re-check lỗi critical + vùng sửa lớn, không cần chấm lại máy móc mọi tiêu chí nếu không bị ảnh hưởng.

## 12. Human control points

Pipeline có thể chạy tự động, nhưng người dùng có quyền dừng/chỉnh ở:

- seed validation;
- story bible;
- character bible;
- master outline;
- arc outline;
- batch audit.

Nếu người dùng lệnh “tự chạy batch”, ChatGPT không cần hỏi lại từng chương trừ khi gặp xung đột canon không thể giải quyết an toàn.

## 13. Failure handling

### Missing canon

Không bịa nếu chi tiết có thể ảnh hưởng lớn. Ghi assumption rõ trong planning artifact hoặc chọn phương án không khóa canon mới.

### Outline contradiction

Final/canon thắng outline. Sửa outline tương lai, không sửa quá khứ.

### Character drift

Dùng DNA để xác định phản ứng hợp lý, rồi rewrite.

### Power scaling conflict

Ưu tiên ledger. Nếu outline đòi kết quả phi lý, thay cơ chế chiến thắng chứ không phá luật.

### Context too large

Dùng summary + ledger + targeted retrieval, không cắt style/canon core.

## 14. Design principle

Pipeline tối ưu cho **continuity + prose quality + controllability**, không tối ưu cho tốc độ token. Viết dài tập tốt đòi hỏi state bền vững và kiểm tra tuần tự.
