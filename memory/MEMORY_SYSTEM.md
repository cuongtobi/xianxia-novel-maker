# Memory System

## 1. Mục tiêu

Memory là hệ thống chống quên và chống tự mâu thuẫn cho truyện dài. Nó không thay thế final chapter và cũng không phải bản tóm tắt văn học.

Memory có hai lớp:

1. **Story State Memory** — thế giới/nhân vật/canon đang ở đâu.
2. **Reader Experience Memory** — độc giả vừa trải qua loại chương gì, promise nào vừa được trả, cảm giác nào đang thiếu.

Hai lớp không được trộn. Reader Experience không override canon.

Mỗi story branch phải có:

```text
memory/
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

## 2. Memory principles

1. Final chapter là sự kiện đã xảy ra; memory là chỉ mục của sự kiện đó.
2. Chỉ ghi canon fact có bằng chứng từ bible hoặc final.
3. Phân biệt **truth**, **belief**, **rumor**, **plan**.
4. Không biến suy luận của AI thành canon.
5. Mỗi thay đổi quan trọng phải có `source chapter`.
6. State hiện tại phải được cập nhật sau mỗi chương final.
7. Nếu memory và final xung đột, final thắng; sửa memory.
8. Nếu bible và final xung đột vì lỗi đã phát hành, đánh dấu contradiction và yêu cầu quyết định retcon, không âm thầm sửa quá khứ.
9. Reader Experience Memory chỉ mô tả **trải nghiệm và pattern**, không phải sự thật thế giới.
10. `ADVANCE` và `PAY` của Story Promise phải phân biệt rõ.

## 3. `current_state.md`

Dùng format:

```md
# Current State

- Last finalized chapter: 0
- Current arc: arc_001
- Story date/time:
- Primary location:
- Immediate external pressure:
- Immediate protagonist goal:
- Current cliff/question:

## Active Cast
| Character | Location | Physical | Emotional | Immediate Goal | Last Seen |

## Active Deadlines
| Deadline | Due | Consequence | Source |

## Recent irreversible changes
-

## Required context for next chapter
-
```

File này phải ngắn, ưu tiên dữ liệu cần cho chương kế tiếp.

## 4. `canon_ledger.md`

```md
# Canon Ledger

| ID | Fact | Type | Introduced | Evidence | Scope | Mutable | Notes |
|---|---|---|---|---|---|---|---|
```

### Type gợi ý

- WORLD
- HISTORY
- CULTIVATION
- CHARACTER
- RELATIONSHIP
- LOCATION
- FACTION
- ITEM
- TECHNIQUE
- SECRET
- EVENT

### Mutable

- `NO`: fact nền hoặc sự kiện quá khứ đã khóa.
- `STATE_ONLY`: fact gốc không đổi nhưng state hiện tại có thể đổi.
- `YES_WITH_EVENT`: chỉ đổi qua sự kiện trong truyện.

## 5. `timeline.md`

```md
# Timeline

| Story Time | Chapter | Duration | Location | Event | Participants | Consequence |
|---|---:|---|---|---|---|---|
```

Ghi cả khoảng thời gian:

- hành trình;
- bế quan;
- hồi phục;
- kỳ hạn nhiệm vụ;
- thời điểm đại hội;
- thời hạn bí cảnh mở/đóng.

Nếu calendar chưa cụ thể, dùng relative time nhất quán: `Ngày 12 sau nhập môn`, `3 canh sau`, v.v.

## 6. `character_states.md`

```md
# Character States

## CHAR_001 — Tên
- Last updated: Ch. 0
- Location:
- Physical state:
- Injuries:
- Emotional state:
- Immediate goal:
- Mid-term goal:
- Active fear/pressure:
- Public status:
- Private concern:
- Known secrets: [K001]
- False beliefs: [B001]
- Debts/promises:
- Active relationships:
- Last meaningful choice:
- Last costly mistake:
- Residual shame/pride/grief/attachment:
- Next likely pressure:
```

Không copy toàn bộ Character DNA vào đây. DNA ở `bible/characters_bible.md`; file này chỉ lưu state động.

Sai lầm gây cost thật phải để lại residue nếu final chứng minh nó còn ảnh hưởng.

## 7. `relationships.md`

```md
# Relationships

| A | B | Trust | Respect | Affection | Fear | Resentment | Obligation | Leverage | Public Relation | Private Reality | Last Change |
|---|---|---:|---:|---:|---:|---:|---:|---|---|---|---|
```

Không cần số tuyệt đối hoàn hảo. Điểm dùng để phát hiện chuyển biến vô lý. Nếu dùng thang 0–10, thay đổi >2 điểm trong một chương phải có sự kiện tương xứng.

## 8. `cultivation_ledger.md`

```md
# Cultivation Ledger

## CHAR_001 — Tên
- Realm:
- Subrealm:
- Foundation quality:
- Qi/energy condition:
- Soul/spirit condition:
- Body condition:
- Dao comprehension:
- Current bottleneck:
- Breakthrough requirements:

### Techniques
| Technique | Tier | Mastery | Cost | Cooldown/limit | Source | Last Used |

### Special traits
| Trait | Effect | Limit | Known by | Source |

### Resources toward breakthrough
| Resource | Qty | Purpose | Acquired | Used |
```

### Breakthrough audit

Mỗi breakthrough phải ghi:

- setup chapters;
- accumulation;
- insight;
- resource;
- trigger;
- risk;
- lasting consequence.

Reader-facing cultivation PAY được ghi riêng ở `reader_experience.md`; ledger này chỉ giữ state tu luyện.

## 9. `inventory_artifacts.md`

```md
# Inventory & Artifacts

| ID | Item | Owner | Location | Qty | State | Known Function | Hidden Function | Acquired | Last Used | Notes |
|---|---|---|---|---:|---|---|---|---|---|---|
```

Đặc biệt theo dõi:

- linh thạch;
- đan dược quan trọng;
- phù lục dùng một lần;
- pháp bảo cần nạp;
- chìa khóa / lệnh bài;
- bằng chứng;
- chiến lợi phẩm;
- vật phẩm quest.

## 10. `factions_locations.md`

```md
# Factions & Locations

## Faction F001 — Tên
- Leadership:
- Current objective:
- Resources:
- Current conflicts:
- Relation to protagonist:
- Internal tension:
- Recent move:
- Information held:

## Location L001 — Tên
- Region:
- Controller:
- Travel connections:
- Distance/time:
- Security:
- Resources:
- Current conditions:
- Last changed:
```

## 11. `knowledge_ledger.md`

Đây là ledger quan trọng nhất để tránh “AI biết nên nhân vật cũng biết”.

```md
# Knowledge Ledger

| ID | Information Atom | Truth Status | Holder | Acquisition Source | Chapter | Confidence | Can Share? | Notes |
|---|---|---|---|---|---:|---|---|---|
```

### Truth Status

- TRUE
- FALSE_BELIEF
- RUMOR
- PARTIAL
- UNKNOWN

Nếu một nhân vật suy luận, ghi `confidence`, không tự nâng thành TRUE trừ khi có evidence.

Ký ức chủ quan, residue, vision hoặc lời kể người chết không tự động là TRUE.

## 12. `foreshadowing.md`

```md
# Foreshadowing Ledger

| ID | Setup | Planted | Reinforced | Intended Payoff Window | Surface Meaning | Hidden Meaning | Status | Payoff |
|---|---|---|---|---|---|---|---|---|
```

Status:

- DORMANT
- ACTIVE
- REINFORCED
- PAID
- ABANDONED_WITH_REASON

Không để setup quan trọng biến mất mà không quyết định.

## 13. `unresolved_threads.md`

```md
# Unresolved Threads

| ID | Thread | Origin | Characters | Urgency | Next Pressure Point | Target Arc | Status | Resolution |
|---|---|---|---|---|---|---|---|---|
```

Status:

- OPEN
- ESCALATING
- WAITING
- RESOLVED
- DROPPED_WITH_REASON

## 14. `chapter_summaries.md`

Mỗi chương chỉ ghi dữ liệu truy hồi đáng giá.

```md
## Chương 1 — Tên

- Time/location:
- POV:
- Major pressure/question:
- Major events:
- Choice:
- Consequence:
- New knowledge:
- Relationship delta:
- Emotional/self-image delta:
- Cultivation delta:
- Inventory delta:
- Setup/payoff:
- Story Promise ADVANCE/PAY:
- Narrative Engine:
- Xianxia Experience:
- Open thread:
- End state:
```

## 15. `reader_experience.md`

Đây là memory về **cách truyện đang được trải nghiệm**, không phải canon.

Format khuyến nghị:

```md
# Reader Experience Memory

- Last updated: Ch. 0
- Current arc:
- Last major payoff:
- Last wonder beat:
- Last emotional hit:
- Last costly mistake:
- Current reader appetite:
- Current payoff debt:

## Story Promise State
| Promise ID | Promise | Core? | PAY definition | Last ADVANCE | Last PAY | Drought warning | Current drought | Status |
|---|---|---|---|---:|---:|---:|---:|---|

## Recent Chapter Experience
| Ch | Primary Engine | Secondary Engine | Dialogue Geometry | Promise ADVANCE/PAY | Xianxia Experience | Emotional Residue | Ending Shape |
|---:|---|---|---|---|---|---|---|

## Recent Rhetorical Tics
| Tic | Chapters seen | Density/risk | Avoid next? |
|---|---|---|---|

## Recent Ending Shapes
-

## Recent Xianxia Beats
- cultivation payoff:
- wonder:
- supernatural danger:
- power gap:
- mystical discovery:
- desirable resource:
- threshold crossing:
- magical craft:
- world-scale glimpse:

## Emotional Residue Window
- Last relationship shift:
- Last self-image shift:
- Last grief/joy/shame/attachment beat:
- Chapters since meaningful emotional change:

## Narrative Engine Window
- Last 4 primary engines:
- 3/4 same-engine risk:

## Calibration Rotation
- Active samples:
- Engines represented:
- Samples to rest next:
```

### Reader Experience rules

1. Update sau mỗi final.
2. Chỉ ghi `PAY` khi final thực sự thỏa PAY definition trong master outline.
3. `recent` nên giữ 8–10 chương gần nhất; cũ hơn có thể compact.
4. Rhetorical tic là signal, không phải canon.
5. `reader appetite` là suy đoán production để planner dùng, không phải sự thật về người dùng thật.
6. Không dùng memory này để ép quota hoặc phá scene organic.

## 16. Memory Update Protocol

Sau rewrite và re-QC:

### Step 1 — Extract story-state delta

So sánh đầu chương và cuối chương:

- ai ở đâu;
- biết gì mới;
- mất/nhận gì;
- mạnh/yếu đi thế nào;
- quan hệ đổi ra sao;
- nhiệm vụ/lời hứa nào phát sinh;
- setup/payoff nào thay trạng thái.

### Step 2 — Validate delta

Mỗi canon/state delta phải có bằng chứng trong rewrite/final candidate.

### Step 3 — Finalize chapter

Chỉ sau khi quality gate và rolling audit (nếu required) PASS.

### Step 4 — Update story-state ledgers

Cập nhật từng file liên quan.

### Step 5 — Update Reader Experience Memory

Từ final, xác định:

- Story Promise: untouched / ADVANCE / PAY;
- primary/secondary Narrative Engine;
- dialogue geometry;
- Xianxia Experience thực sự delivered;
- Emotional Residue;
- ending shape;
- rhetorical tics đáng theo dõi;
- costly mistake nếu có;
- current payoff debt.

### Step 6 — Refresh `current_state.md`

Đây là bước cuối cùng của chapter transaction.

Không sang chương mới nếu `reader_experience.md` hoặc `current_state.md` chưa cập nhật.

## 17. Memory Compaction

Khi truyện dài:

- không xóa canon;
- có thể chuyển thread đã resolved lâu vào archive trong cùng file;
- chapter summary giữ dạng ngắn;
- chỉ đọc 3–10 summary gần nhất theo nhu cầu;
- dùng ID ổn định cho entity và fact;
- không đổi ID vì đổi tên/danh xưng;
- `reader_experience.md` giữ chi tiết 8–10 chương gần nhất, sau đó compact thành pattern theo arc/batch;
- không giữ mọi lexical tic lịch sử; chỉ giữ tic đang hoạt động hoặc tái phát.

## 18. Contradiction Protocol

Khi phát hiện contradiction:

1. tìm bằng chứng trong final;
2. xác định fact nào xuất hiện trước;
3. phân loại: memory bug / draft bug / published canon conflict;
4. memory bug → sửa memory;
5. draft bug → rewrite draft;
6. published canon conflict → không tự retcon, ghi issue và xin/user directive nếu ảnh hưởng lớn.

Reader Experience Memory không tham gia quyết định canon conflict.

## 19. Minimum memory for a new story

Ngay sau Genesis phải tạo ít nhất:

- current_state;
- canon ledger với luật nền;
- cultivation ledger cho protagonist;
- character state cho main cast;
- faction/location state vùng mở đầu;
- knowledge ledger các secret quan trọng;
- foreshadowing ledger từ master/arc outline;
- unresolved threads của opening arc;
- **reader_experience.md** với 3–5 Story Promise đã khóa, drought warning, empty recent windows và Reader Experience opening state.
