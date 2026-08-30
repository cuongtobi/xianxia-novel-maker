# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt**, vận hành trực tiếp bằng **ChatGPT Web + GitHub**.

GitHub là **persistent memory + source of truth** của truyện. ChatGPT là **orchestrator + world architect + writer + editor + continuity checker**. Mỗi truyện nằm trên một branch riêng và có thể tiếp tục ở bất kỳ cuộc hội thoại ChatGPT nào chỉ bằng cách đọc lại dữ liệu trên GitHub.

---

## 1. Pipeline làm gì?

Pipeline chuẩn:

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
  ↓
Arc Outline
  ↓
Chapter Scene Plan
  ↓
Draft
  ↓
Quality Check
  ↓
Rewrite
  ↓
Critical Re-QC
  ↓
Final TXT
  ↓
Memory Update
  ↓
Chương tiếp theo
```

Mục tiêu:

- viết truyện dài hàng trăm chương nhưng vẫn giữ canon và continuity;
- văn phong tiếng Việt tự nhiên, có khí chất tiên hiệp / tu tiên;
- tránh giọng văn máy móc và các pattern dễ nhận ra của AI;
- mỗi nhân vật quan trọng có **Character DNA** riêng;
- kiểm soát power scaling, cảnh giới, công pháp, vật phẩm, thương tích và tài nguyên;
- quản lý ai biết bí mật gì bằng **Knowledge Ledger**;
- cho phép ChatGPT tự chạy **batch 10 chương** sau một lệnh;
- có thể đóng chat hôm nay và tiếp tục truyện ở chat khác mà không phụ thuộc memory hội thoại cũ.

---

# 2. Quick Start

Nếu chỉ muốn bắt đầu viết truyện, làm theo 4 bước dưới đây.

## Bước 1 — Kết nối GitHub

Trong ChatGPT Web, kết nối GitHub và chỉ định repo:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker
```

Framework nằm trên:

```text
main
```

Mỗi truyện sẽ nằm trên branch riêng:

```text
story/<slug>
```

Ví dụ:

```text
story/pham-nhan-cau-tien
story/van-co-dao-ton
story/ma-mon-truong-sinh
```

Không viết hai truyện trên cùng một story branch.

---

## Bước 2 — Tạo seed

Mẫu seed nằm tại:

```text
templates/seed.template.yaml
```

Bạn **không cần điền toàn bộ**. Có thể chỉ cung cấp những ý quan trọng và để AI tự xây phần còn lại.

Ví dụ seed tối giản:

```yaml
meta:
  working_title: "Phàm Nhân Cầu Tiên"
  slug: "pham-nhan-cau-tien"
  genres:
    - "tiên hiệp"
    - "tu tiên"
  target_length_chapters: 500

creative_intent:
  one_sentence_premise: "Một thiếu niên phàm tục vô linh căn tìm cách bước vào con đường trường sinh."
  core_hook: "Tu tiên bằng cách nghiên cứu quy luật vận hành của linh khí thay vì thiên phú."
  reading_experience:
    primary_mood: "trầm tĩnh"
    secondary_moods:
      - "nguy hiểm"
      - "khám phá"

protagonist_seed:
  name: "Lục Trầm"
  gender: "nam"
  starting_age: 16
  origin: "thôn nhỏ vùng biên"
  personality_keywords:
    - "kiên nhẫn"
    - "thực tế"
    - "đa nghi"
  strengths:
    - "quan sát tốt"
  flaws:
    - "khó tin người"
  special_trait_or_cheat: "Không có hệ thống; khả năng quan sát linh khí đặc biệt nhạy bén."

world_seed:
  cultivation_flavor: "tu tiên cổ điển, tài nguyên khan hiếm, tông môn cạnh tranh"

plot_seed:
  opening_situation: "Lục Trầm sống bằng nghề hái thuốc cùng gia đình."
  inciting_incident: "Một trận chiến giữa hai tu sĩ phá hủy vùng núi gần thôn."
  first_major_goal: "Tìm đường gia nhập một tông môn nhỏ."

tone_and_style_seed:
  narration_pov: "third_limited"
  preferred_pacing: "vừa, có thời gian tích lũy và khám phá"

production:
  batch_size: 10
  auto_run_batch: true
  require_qc: true
  require_rewrite: true
```

Những field chưa biết có thể để trống hoặc `null`.

Seed chỉ là **ý định sáng tác ban đầu**, không phải canon hoàn chỉnh.

---

## Bước 3 — Yêu cầu ChatGPT tạo truyện

Gửi seed và lệnh:

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

ChatGPT phải tự thực hiện:

```text
1. Resolve slug
2. Tạo branch story/<slug> từ main
3. Lưu seed
4. Xây Story Bible
5. Xây Style Bible
6. Xây Characters Bible
7. Xây Master Outline
8. Xây Arc 1 Outline
9. Khởi tạo Memory
10. Đưa truyện về trạng thái READY_TO_WRITE
```

Không cần yêu cầu duyệt từng stage nếu seed không có blocker bắt buộc người dùng quyết định.

---

## Bước 4 — Viết truyện

### Viết 1 chương

```text
Viết chương tiếp theo qua đủ scene plan, draft, QC, rewrite, final và memory update.
```

### Viết 10 chương

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

### Viết tiếp trong chat mới

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.
Tiếp tục branch story/pham-nhan-cau-tien và viết batch 10 chương tiếp theo.
```

ChatGPT phải đọc GitHub để phục hồi state. Không cần copy lại toàn bộ lịch sử chat cũ.

---

# 3. Cấu trúc một truyện

Mỗi story branch chứa dữ liệu truyện tại:

```text
stories/<story-slug>/
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
│       ├── arc_002.md
│       └── ...
│
├── chapters/
│   ├── 0001/
│   │   ├── scene_plan.md
│   │   ├── draft.txt
│   │   ├── quality_report.md
│   │   └── rewrite.txt
│   ├── 0002/
│   └── ...
│
├── final/
│   ├── Chương 1: Tên chương.txt
│   ├── Chương 2: Tên chương.txt
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
    └── chapter_summaries.md
```

---

# 4. Genesis — quá trình khởi tạo một truyện

Genesis chỉ chạy khi tạo truyện mới hoặc khi người dùng chủ động yêu cầu xây lại một phần chưa có.

Thứ tự bắt buộc:

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
 ↓
Arc 1 Outline
 ↓
Initialize Memory
```

Mỗi stage phải đọc output của stage trước.

## Story Bible

Chứa nền tảng logic của thế giới, ví dụ:

- thiên địa / vị diện / giới vực;
- linh khí và nguồn tài nguyên;
- cảnh giới và tiểu cảnh giới;
- tuổi thọ;
- linh căn, căn cốt, thể chất, huyết mạch;
- công pháp, thuật pháp, thần thông;
- kiếm đạo / thể tu / đan đạo / khí đạo / trận đạo;
- đan dược;
- luyện khí;
- pháp bảo;
- trận pháp;
- phù lục;
- linh thú / yêu thú;
- thiên kiếp;
- tâm ma;
- tông môn;
- gia tộc;
- hoàng triều;
- thương hội;
- chính đạo / ma đạo;
- kinh tế tu tiên;
- tiền tệ và trao đổi;
- khoảng cách và tốc độ di chuyển;
- truyền tin / truyền tống;
- địa chính trị;
- quy tắc chiến đấu và vượt cấp.

Worldbuilding phải có quan hệ **nguyên nhân → hệ quả**, không chỉ tạo danh sách tên nghe hoành tráng.

## Style Bible

Quy định:

- POV;
- nhịp truyện;
- mật độ hội thoại;
- mức Hán Việt;
- cách miêu tả chiến đấu;
- cách viết cảm xúc;
- cách exposition;
- cách kết chương;
- pattern ngôn ngữ cần tránh;
- tiêu chuẩn để văn xuôi không có cảm giác AI.

## Characters Bible

Mỗi nhân vật quan trọng phải có Character DNA riêng, gồm tối thiểu:

- core desire;
- core fear;
- formative wound;
- shame;
- non-negotiable value;
- blind spot;
- internal contradiction;
- social mask;
- decision heuristic;
- risk tolerance;
- pressure response;
- speech fingerprint;
- emotional tells;
- relationship behavior;
- cultivation philosophy;
- combat signature;
- secret / hidden agenda;
- forbidden behavior;
- arc vector.

Nếu đổi tên hai nhân vật mà lời thoại và phản ứng vẫn hoán đổi được cho nhau, DNA chưa đạt.

## Master Outline

Master Outline quản lý hướng dài hạn:

- premise;
- major conflicts;
- các phase lớn;
- mục tiêu dài hạn của protagonist;
- progression của thế giới;
- progression tu luyện;
- major reveals;
- setup/payoff lớn;
- ending direction.

Không cần khóa cứng hàng trăm chương ngay từ đầu.

## Arc Outline

Arc Outline cụ thể hơn Master Outline và chỉ quản lý một arc hiện tại hoặc sắp tới.

Outline là **kế hoạch**, chưa phải canon.

Final chapter + canon ledger mới là những gì thực sự đã xảy ra.

---

# 5. Quy trình viết một chương

Mỗi chương là một transaction hoàn chỉnh.

```text
Context Assembly
 ↓
Scene Plan
 ↓
Draft
 ↓
Quality Check
 ↓
Rewrite
 ↓
Critical Re-QC
 ↓
Final
 ↓
Memory Update
```

## Stage A — Assemble Context

Trước khi viết chương N, ChatGPT phải đọc dữ liệu liên quan:

- seed;
- Story Bible;
- Style Bible;
- Character DNA của nhân vật xuất hiện;
- Master Outline phần liên quan;
- Arc Outline hiện tại;
- current state;
- canon;
- cultivation state;
- knowledge state;
- foreshadowing;
- unresolved threads;
- summaries gần nhất;
- full final chương N-1 nếu continuity trực tiếp.

Không cần đọc lại hàng trăm chương cũ nếu ledger và summaries đã đủ.

## Stage B — Scene Plan

Tạo:

```text
stories/<slug>/chapters/NNNN/scene_plan.md
```

Scene plan phải xác định:

- POV;
- thời gian / địa điểm;
- người hiện diện;
- mục tiêu;
- obstacle;
- stakes;
- thông tin nhân vật được biết;
- thông tin nhân vật không được biết;
- causal chain;
- turn / reversal;
- outcome;
- state changes;
- setup / payoff;
- memory delta dự kiến.

## Stage C — Draft

Tạo:

```text
stories/<slug>/chapters/NNNN/draft.txt
```

Draft là bản văn xuôi hoàn chỉnh, chưa phải bản phát hành.

## Stage D — Quality Check

Tạo:

```text
stories/<slug>/chapters/NNNN/quality_report.md
```

QC kiểm tra tối thiểu:

- canon;
- timeline;
- geography / travel time;
- cultivation / power scaling;
- skills / techniques;
- artifact ownership;
- injuries / fatigue;
- consumables;
- character knowledge;
- relationships;
- Character DNA;
- POV;
- causal logic;
- pacing;
- prose naturalness;
- repetition;
- dialogue differentiation;
- exposition load;
- setup / payoff;
- ending quality.

Severity:

```text
BLOCKER
MAJOR
MINOR
NOTE
```

Không được final nếu còn `BLOCKER` hoặc `MAJOR` chưa xử lý.

## Stage E — Rewrite

Tạo:

```text
stories/<slug>/chapters/NNNN/rewrite.txt
```

Rewrite là **toàn bộ chương hoàn chỉnh**, không phải danh sách patch.

Rewrite phải sửa các lỗi QC nhưng không tự ý thay đổi canon hoặc thêm twist lớn ngoài outline.

## Stage F — Critical Re-QC

Kiểm tra lại:

- toàn bộ BLOCKER;
- toàn bộ MAJOR;
- những đoạn bị thay đổi lớn;
- continuity bị ảnh hưởng bởi rewrite.

## Stage G — Final

Chỉ sau khi pass QC mới tạo:

```text
stories/<slug>/final/Chương N: <Tiêu đề>.txt
```

Nội dung final:

```text
Chương N: <Tiêu đề>

<nội dung chương>
```

Final chỉ chứa truyện.

Không chèn:

- prompt;
- QC note;
- metadata;
- markdown report;
- lời giải thích của AI.

## Stage H — Memory Update

Ngay sau khi final, cập nhật memory trước khi viết chương tiếp theo.

---

# 6. Batch 10 chương

Lệnh chuẩn:

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

Pipeline **không** làm như sau:

```text
plan 10 chương
→ draft 10 chương
→ QC 10 chương
→ memory cuối batch
```

Cách này dễ phá continuity.

Pipeline bắt buộc làm:

```text
Chương N
plan → draft → QC → rewrite → final → memory

Chương N+1
đọc memory mới → plan → draft → QC → rewrite → final → memory

...

Chương N+9
plan → draft → QC → rewrite → final → memory

↓
Batch Audit
```

Memory của chương trước luôn là input của chương sau.

## Batch Preflight

Trước batch, ChatGPT kiểm tra:

- story branch;
- chapter range;
- arc hiện tại;
- state cuối batch trước;
- active threads;
- cultivation constraints;
- Character DNA drift risk;
- setup/payoff đang chờ;
- pacing risks.

## Arc boundary

Nếu arc hiện tại kết thúc ở giữa batch:

```text
Arc 1 kết thúc ở Chương 126
Batch = Chương 121–130
```

Pipeline phải xây / đọc Arc 2 trước khi viết chương 127.

Không kéo Arc 1 thêm chỉ để đủ batch 10.

## Batch Audit

Sau chương thứ 10 tạo:

```text
stories/<slug>/chapters/batch_NNNN_NNNN_audit.md
```

Audit kiểm tra xuyên cả batch:

- arc progress;
- continuity;
- timeline;
- geography;
- knowledge;
- inventory;
- injuries;
- relationships;
- Character DNA drift;
- supporting cast agency;
- antagonist movement;
- cultivation progression;
- power scaling;
- resource economy;
- repeated words;
- repeated scene structures;
- repeated cliffhangers;
- AI-like prose patterns;
- forgotten plot threads;
- next-batch handoff.

---

# 7. Memory System

Memory là phần quan trọng nhất để truyện dài không tự mâu thuẫn.

## current_state.md

Snapshot hiện tại của truyện:

- chương mới nhất;
- thời gian;
- địa điểm;
- protagonist đang ở đâu;
- mục tiêu trước mắt;
- active conflict;
- arc hiện tại;
- trạng thái cần biết trước chương tiếp theo.

## canon_ledger.md

Các fact đã khóa.

Ví dụ:

```text
- Lục Trầm sinh tại Thanh Hà thôn.
- Trần Mặc đã chết ở Chương 47.
- Huyền Vân Kiếm bị phá hủy ở Chương 82.
```

Không được tự ý retcon canon.

## timeline.md

Quản lý:

- thứ tự sự kiện;
- ngày / tháng / năm nếu truyện có;
- thời gian tu luyện;
- thời gian di chuyển;
- tuổi nhân vật;
- sự kiện xảy ra song song.

## character_states.md

Theo dõi trạng thái hiện tại của từng nhân vật:

- location;
- physical state;
- mental state;
- current goals;
- secrets;
- promises;
- debts;
- injuries;
- current resources.

## relationships.md

Theo dõi quan hệ có trạng thái, không dùng nhãn đơn giản như `friend/enemy`.

Ví dụ:

```text
trust: 3/10
fear: 7/10
debt: protagonist owes one life-saving favor
hidden resentment: yes
public relationship: allies
private relationship: mutual suspicion
```

## cultivation_ledger.md

Theo dõi:

- cảnh giới;
- tiểu cảnh giới;
- foundation quality;
- technique mastery;
- skills;
- dao comprehension;
- bottlenecks;
- resources;
- breakthrough conditions;
- injuries affecting combat;
- reason nhân vật có thể / không thể vượt cấp.

## inventory_artifacts.md

Theo dõi:

- pháp bảo;
- binh khí;
- đan dược;
- phù lục;
- linh thạch;
- consumables;
- item owner;
- item location;
- item state;
- item usage.

## factions_locations.md

Theo dõi:

- tông môn;
- gia tộc;
- thế lực;
- địa điểm;
- faction standing;
- political changes;
- ownership / control.

## knowledge_ledger.md

Theo dõi **ai biết điều gì**.

Ví dụ:

```text
Bí mật: Lục Trầm có thể cảm nhận dòng linh khí.

Biết:
- Lục Trầm
- sư phụ

Nghi ngờ:
- trưởng lão họ Hàn

Không biết:
- đồng môn
- đối thủ hiện tại
```

Điều này ngăn lỗi nhân vật biết thông tin chỉ vì narrator hoặc AI biết.

## foreshadowing.md

Theo dõi:

- setup;
- hints;
- expected payoff window;
- actual payoff;
- status.

## unresolved_threads.md

Danh sách câu hỏi / xung đột chưa giải quyết.

## chapter_summaries.md

Tóm tắt mỗi chương để context assembly không cần đọc lại toàn bộ truyện.

---

# 8. Source of Truth

Nếu dữ liệu mâu thuẫn, ưu tiên theo thứ tự:

```text
1. Canon Ledger
2. Final chapters
3. Bible
4. Memory ledgers
5. Arc Outline
6. Master Outline
7. Seed
8. Draft / Scene Plan
```

Điểm quan trọng:

```text
Outline = kế hoạch
Final = sự kiện đã xảy ra
Canon Ledger = fact đã khóa
```

Nếu nhân vật hành động hợp DNA làm lệch một beat chưa final trong outline, ưu tiên logic nhân vật và điều chỉnh outline tương lai thay vì ép nhân vật quay lại plan cũ.

---

# 9. Các lệnh thường dùng

## Tạo truyện mới

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

## Chỉ xây bible

```text
Xây Story Bible, Style Bible và Characters Bible từ seed hiện tại. Chưa viết chương.
```

## Xây outline

```text
Dựa trên bible hiện tại, lập Master Outline và Arc 1. Không viết chương.
```

## Viết 1 chương

```text
Viết chương tiếp theo qua đủ scene plan, draft, QC, rewrite, final và memory update.
```

## Viết 10 chương

```text
Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

## Tiếp tục truyện

```text
Tiếp tục branch story/<slug> từ current_state và viết chương tiếp theo.
```

## Audit continuity

```text
Audit 20 chương gần nhất: canon, timeline, knowledge, inventory, relationships và continuity. Chưa rewrite nếu chưa cần.
```

## Audit power scaling

```text
Kiểm tra power scaling của 30 chương gần nhất: cảnh giới, technique mastery, tài nguyên, breakthrough, injury recovery và logic vượt cấp.
```

## Audit nhân vật

```text
Kiểm tra Character DNA drift và voice collision của các nhân vật xuất hiện trong 20 chương gần nhất.
```

## Audit văn phong

```text
Audit 20 chương gần nhất để tìm AI-like prose patterns, từ/cấu trúc lặp, exposition thừa, dialogue đồng giọng và cliffhanger lặp.
```

## Điều chỉnh outline

```text
Đọc final + memory mới nhất và cập nhật Arc Outline theo diễn biến thực tế. Không retcon final.
```

## Repair continuity

```text
Sửa các lỗi continuity đã phát hiện. Ưu tiên sửa artifact chưa final; không retcon final nếu tôi chưa cho phép.
```

---

# 10. Tiếp tục truyện trong một cuộc hội thoại mới

Bạn không cần giữ nguyên một chat hàng tháng.

Trong chat mới chỉ cần nói:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.
Tiếp tục truyện ở branch story/<slug> và viết batch 10 chương tiếp theo.
```

ChatGPT phải đọc tối thiểu:

```text
AGENTS.md
seed/seed.yaml
memory/current_state.md
batch audit gần nhất
arc hiện tại
bible liên quan
recent chapter summaries
final gần nhất nếu cần continuity trực tiếp
```

GitHub mới là memory bền vững của pipeline, không phải lịch sử hội thoại ChatGPT.

---

# 11. Resume khi pipeline dừng giữa chương

Pipeline có thể xác định stage hiện tại từ artifact trên GitHub.

## Có scene plan nhưng chưa có draft

```text
Resume từ Draft.
```

## Có draft nhưng chưa có QC

```text
Resume từ Quality Check.
```

Không viết lại draft vô cớ.

## QC yêu cầu rewrite nhưng chưa có rewrite

```text
Resume từ Rewrite.
```

## Có rewrite nhưng chưa có final

```text
Chạy Critical Re-QC rồi tạo Final nếu pass.
```

## Có final nhưng memory chưa cập nhật

```text
Cập nhật memory trước.
```

Không được viết chương mới khi memory vẫn đứng ở chương trước.

## Memory nói đã đến chương N nhưng final chỉ có N-1

Đây là inconsistency.

Pipeline phải kiểm tra final + Git history và sửa memory trước khi tiếp tục.

---

# 12. Quy tắc văn phong

Mục tiêu là tiếng Việt tự nhiên có khí chất tiên hiệp, không phải bản dịch máy hoặc văn mẫu AI.

Pipeline ưu tiên:

- nhịp câu thay đổi theo tình huống;
- Hán Việt dùng đúng chỗ;
- cảm xúc thể hiện qua hành vi và lựa chọn;
- hội thoại phản ánh địa vị và Character DNA;
- worldbuilding đi qua hành động và hậu quả;
- chiến đấu có vị trí, mục tiêu, tài nguyên và hậu quả;
- độc giả được tự suy ra khi thông tin đã đủ.

Pipeline phải cảnh giác với:

- lạm dụng `lúc này`;
- `ngay sau đó`;
- `cùng lúc đó`;
- `không khỏi`;
- `hiển nhiên`;
- `rõ ràng`;
- spam `ánh mắt` / `khóe môi` / `khí tức`;
- câu ba vế đối xứng lặp;
- mọi nhân vật nói cùng một giọng;
- nhân vật liên tục tự giải thích tâm lý;
- narrator kể lại điều độc giả vừa đọc;
- encyclopedia dump giữa cảnh;
- mọi conflict đều kết bằng chiến đấu;
- mọi chương đều kết cùng một loại cliffhanger;
- protagonist liên tục được bảo vật hoặc cheat cứu nguy;
- breakthrough xảy ra theo lịch quá đều.

---

# 13. Quy tắc power scaling

Power scaling không chỉ dựa vào tên cảnh giới.

Khi đánh giá khả năng chiến đấu phải xét:

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

Vượt cấp phải có nguyên nhân cụ thể và cost hợp lý.

Special trait / cheat không được trở thành đáp án cho mọi xung đột.

---

# 14. GitHub workflow

## Framework

Framework sống trên:

```text
main
```

Chỉ sửa `main` khi đang cải tiến pipeline.

## Story

Mỗi truyện sống trên:

```text
story/<slug>
```

Story artifacts không được ghi lên `main`.

## Commit gợi ý

Genesis:

```text
story: bootstrap <slug>
story: build bible for <slug>
story: outline opening arc for <slug>
```

Production:

```text
chapter: finalize ch 001 <slug>
memory: update through ch 001 <slug>
```

Cuối batch:

```text
audit: batch 001-010 <slug>
```

Commit message không bắt buộc giống literal, nhưng phải dễ đọc lịch sử.

---

# 15. Khi nào pipeline được phép tự quyết?

Seed có thể để AI tự xây nhiều phần.

Field:

```yaml
open_questions:
  user_wants_ai_to_decide: []
  user_must_decide: []
```

### `user_wants_ai_to_decide`

AI được tự lựa chọn phương án sáng tạo phù hợp bible và tiếp tục pipeline.

### `user_must_decide`

Nếu vấn đề ảnh hưởng trực tiếp tới chương sắp viết, pipeline phải dừng trước final và yêu cầu người dùng quyết định.

Ngoài blocker thực sự, ưu tiên tự giải quyết sáng tạo thay vì hỏi người dùng ở từng bước nhỏ.

---

# 16. Stop Conditions

Pipeline phải dừng trước khi tạo final nếu:

- có canon conflict không thể giải quyết nếu không retcon;
- constraint trong `user_must_decide` chưa có đáp án và ảnh hưởng trực tiếp;
- outcome bắt buộc phá hard rule của world / character / power system;
- còn QC severity `BLOCKER` hoặc `MAJOR`;
- title / final state không thể xác định hợp lệ.

Trong các trường hợp khác, pipeline nên tự xử lý và tiếp tục.

---

# 17. Final filename

Format bắt buộc:

```text
Chương X: <Tiêu đề>.txt
```

Ví dụ:

```text
Chương 1: Người Trên Núi.txt
Chương 2: Một Sợi Linh Khí.txt
Chương 108: Kiếm Qua Huyền Quan.txt
```

> **Lưu ý Windows:** dấu `:` hợp lệ trên GitHub nhưng Windows không cho phép filename có dấu `:` khi checkout trực tiếp. Workflow ChatGPT Web + GitHub vẫn có thể dùng format trên. Nếu sau này cần clone repo về Windows, nên bổ sung một export step chuyển `:` sang ký tự an toàn trong bản local.

---

# 18. Tài liệu framework

Đọc sâu hơn tại:

```text
AGENTS.md
```

Luật vận hành bắt buộc cho ChatGPT.

```text
docs/ARCHITECTURE.md
```

Kiến trúc toàn pipeline.

```text
docs/GITHUB_CHATGPT_PROTOCOL.md
```

Cách ChatGPT Web và GitHub phối hợp, state machine, branch safety, resume.

```text
docs/BATCH_10_WORKFLOW.md
```

Quy trình chi tiết khi viết batch 10 chương.

```text
memory/MEMORY_SYSTEM.md
```

Thiết kế persistent memory và các ledger.

```text
prompts/PIPELINE_PROMPTS.md
```

Prompt contract cho từng stage.

```text
templates/seed.template.yaml
```

Mẫu seed tạo truyện mới.

Các template khác:

```text
templates/story_bible.template.md
templates/style_bible.template.md
templates/characters_bible.template.md
templates/master_outline.template.md
templates/arc_outline.template.md
templates/chapter_scene.template.md
templates/quality_report.template.md
```

---

# 19. Workflow khuyến nghị hằng ngày

Nếu đang vận hành một truyện dài, workflow đơn giản nhất là:

```text
Ngày / phiên đầu tiên
Seed → Genesis → Chương 1–10 → Batch Audit

Phiên tiếp theo
Read state → Chương 11–20 → Batch Audit

Phiên tiếp theo
Read state → Chương 21–30 → Batch Audit

...
```

Sau mỗi vài batch có thể chạy thêm:

```text
Audit continuity 30–50 chương
Audit Character DNA
Audit power scaling
Audit repetition/style
Reconcile arc outline với final
```

Cách này giúp truyện có khả năng phát triển tự nhiên nhưng không mất kiểm soát khi số chương tăng lớn.

---

# 20. Một câu lệnh mẫu đầy đủ

Sau khi đã có một truyện đang chạy:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.

Làm việc trên branch story/pham-nhan-cau-tien.
Đọc AGENTS.md, current_state, batch audit gần nhất, arc hiện tại, các bible và memory liên quan.

Viết batch 10 chương tiếp theo.
Mỗi chương bắt buộc chạy tuần tự:
scene plan → draft → QC dữ liệu + continuity + văn phong → rewrite → critical re-QC → final → memory update.

Không bỏ qua memory giữa các chương.
Không retcon final.
Nếu arc kết thúc giữa batch, xây arc tiếp theo trước khi vượt boundary.
Cuối batch tạo batch audit và next-batch handoff.
```

Thông thường bạn không cần viết dài như trên vì `AGENTS.md` và workflow đã chứa các luật này. Câu lệnh ngắn sau là đủ:

```text
Tiếp tục branch story/pham-nhan-cau-tien và viết batch 10 chương tiếp theo đúng pipeline.
```

---

## Nguyên tắc cuối cùng

```text
GitHub giữ sự thật.
Bible giữ luật.
Character DNA giữ con người.
Outline giữ hướng đi.
Scene plan giữ logic chương.
QC giữ chất lượng.
Final giữ tác phẩm.
Memory giữ continuity.
```

Không bỏ qua một lớp chỉ để viết nhanh hơn.
