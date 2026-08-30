# Memory System

## 1. Mục tiêu

Memory là hệ thống chống quên và chống tự mâu thuẫn cho truyện dài. Nó không thay thế final chapter và cũng không phải bản tóm tắt văn học. Memory lưu **state có thể truy vấn** để chương sau biết chính xác thế giới đang ở đâu.

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
└── chapter_summaries.md
```

## 2. Memory principles

1. Final chapter là sự kiện đã xảy ra; memory là chỉ mục của sự kiện đó.
2. Chỉ ghi fact có bằng chứng từ bible hoặc final.
3. Phân biệt **truth**, **belief**, **rumor**, **plan**.
4. Không biến suy luận của AI thành canon.
5. Mỗi thay đổi quan trọng phải có `source chapter`.
6. State hiện tại phải được cập nhật sau mỗi chương final.
7. Nếu memory và final xung đột, final thắng; sửa memory.
8. Nếu bible và final xung đột vì lỗi đã phát hành, đánh dấu contradiction và yêu cầu quyết định retcon, không âm thầm sửa quá khứ.

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
- Next likely pressure:
```

Không copy toàn bộ Character DNA vào đây. DNA ở `bible/characters_bible.md`; file này chỉ lưu state động.

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
- Goal:
- Major events:
- Choice:
- Consequence:
- New knowledge:
- Relationship delta:
- Cultivation delta:
- Inventory delta:
- Setup/payoff:
- Open thread:
- End state:
```

## 15. Memory Update Protocol

Sau rewrite và re-QC:

### Step 1 — Extract delta

So sánh đầu chương và cuối chương:

- ai ở đâu;
- biết gì mới;
- mất/nhận gì;
- mạnh/yếu đi thế nào;
- quan hệ đổi ra sao;
- nhiệm vụ/lời hứa nào phát sinh;
- setup/payoff nào thay trạng thái.

### Step 2 — Validate delta

Mỗi delta phải có bằng chứng trong rewrite.

### Step 3 — Write final

Chỉ sau khi rewrite đủ điều kiện.

### Step 4 — Update ledgers

Cập nhật từng file liên quan.

### Step 5 — Refresh `current_state.md`

Đây là bước cuối cùng của chapter transaction.

## 16. Memory Compaction

Khi truyện dài:

- không xóa canon;
- có thể chuyển thread đã resolved lâu vào phần archive trong cùng file;
- chapter summary giữ dạng ngắn;
- chỉ đọc 3–10 summary gần nhất theo nhu cầu;
- dùng ID ổn định cho entity và fact;
- không đổi ID vì đổi tên/danh xưng.

## 17. Contradiction Protocol

Khi phát hiện contradiction:

1. tìm bằng chứng trong final;
2. xác định fact nào xuất hiện trước;
3. phân loại: memory bug / draft bug / published canon conflict;
4. memory bug → sửa memory;
5. draft bug → rewrite draft;
6. published canon conflict → không tự retcon, ghi issue và xin/user directive nếu ảnh hưởng lớn.

## 18. Minimum memory for a new story

Ngay sau Genesis phải tạo ít nhất:

- current_state;
- canon ledger với luật nền;
- cultivation ledger cho protagonist;
- character state cho main cast;
- faction/location state vùng mở đầu;
- knowledge ledger các secret quan trọng;
- foreshadowing ledger từ master/arc outline;
- unresolved threads của opening arc.
