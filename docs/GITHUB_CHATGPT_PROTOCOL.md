# ChatGPT Web + GitHub Protocol

## 1. Mục đích

Tài liệu này định nghĩa cách vận hành pipeline hoàn toàn qua hội thoại ChatGPT và GitHub connector/plugin.

Không cần một service chạy nền. GitHub là persistent memory; ChatGPT là execution engine theo từng phiên.

## 2. Repository model

- Framework branch: `main`
- Story branch: `story/<slug>`
- Một story branch chỉ chứa dữ liệu của một truyện trong `stories/<slug>/`.
- Framework có thể được cải tiến trên `main`; story đang chạy không tự động nhận thay đổi trừ khi user yêu cầu đồng bộ.

## 3. New Story Protocol

Khi user cung cấp seed:

### Step 1 — Resolve slug

- ưu tiên `meta.slug` nếu có;
- nếu trống, sinh slug Latin/kebab-case từ working title;
- branch: `story/<slug>`.

### Step 2 — Create branch

Tạo từ `main`.

### Step 3 — Create story tree

Tạo ít nhất:

```text
stories/<slug>/seed/seed.yaml
stories/<slug>/bible/story_bible.md
stories/<slug>/bible/style_bible.md
stories/<slug>/bible/characters_bible.md
stories/<slug>/outline/master_outline.md
stories/<slug>/outline/arcs/arc_001.md
stories/<slug>/memory/current_state.md
stories/<slug>/memory/canon_ledger.md
stories/<slug>/memory/timeline.md
stories/<slug>/memory/character_states.md
stories/<slug>/memory/relationships.md
stories/<slug>/memory/cultivation_ledger.md
stories/<slug>/memory/inventory_artifacts.md
stories/<slug>/memory/factions_locations.md
stories/<slug>/memory/knowledge_ledger.md
stories/<slug>/memory/foreshadowing.md
stories/<slug>/memory/unresolved_threads.md
stories/<slug>/memory/chapter_summaries.md
```

### Step 4 — Seed validation

Không hỏi lại phần user đã cung cấp. Chỉ xác định:

- contradiction;
- missing critical constraint;
- creative blanks AI được phép quyết định;
- content user bắt buộc quyết định.

Nếu không có blocker, tự tiếp tục Genesis.

### Step 5 — Genesis

Chạy theo thứ tự:

1. Story Bible
2. Style Bible
3. Characters Bible
4. Master Outline
5. Arc 1 Outline
6. Initialize Memory

Mỗi stage đọc output trước đó.

## 4. How ChatGPT Should Read GitHub

### Framework session start

Đọc:

- `AGENTS.md`
- tài liệu workflow liên quan.

### Story session start

Đọc từ đúng branch:

- seed;
- current_state;
- arc hiện tại;
- bible liên quan;
- memory ledgers liên quan;
- batch audit gần nhất nếu có.

### Targeted reads

Không tải toàn bộ hundreds of chapters. Dùng filename, summary và ledger để tìm đúng final cần đọc.

## 5. How ChatGPT Should Write GitHub

### Framework files

Ghi vào `main` chỉ khi user đang phát triển pipeline.

### Story files

Ghi vào `story/<slug>`.

Không ghi story artifact lên `main`.

### Atomicity rule

Với chapter N:

1. ghi scene plan;
2. ghi draft;
3. ghi QC;
4. ghi rewrite;
5. ghi final;
6. cập nhật memory.

Nếu dừng giữa chừng, `final/` không được giả vờ đã hoàn tất.

## 6. Commit Strategy

Khuyến nghị:

- Genesis: 1–3 commits theo nhóm bible/outline/memory.
- Production: 1 commit/chapter hoặc 1 commit cho chapter artifacts + 1 memory commit.
- Batch audit: 1 commit cuối batch.

Commit message gợi ý:

- `story: bootstrap <slug>`
- `story: build bible for <slug>`
- `story: outline opening arc for <slug>`
- `chapter: finalize ch 001 <slug>`
- `memory: update through ch 001 <slug>`
- `audit: batch 001-010 <slug>`

Không bắt buộc đúng literal nếu GitHub connector thuận tiện hơn, nhưng commit phải dễ hiểu.

## 7. Branch Safety

Trước mọi write:

- xác nhận repository full name;
- xác nhận story slug;
- xác nhận branch;
- xác nhận path bắt đầu bằng `stories/<same-slug>/`.

Nếu user chuyển truyện giữa phiên, reset context assembly và đọc branch mới.

## 8. Standard User Interaction

### Create story

User:

> Tạo truyện mới theo seed sau...

Assistant thực hiện:

- tạo branch;
- lưu seed;
- Genesis;
- báo các artifact chính đã tạo.

### Write batch

User:

> Viết tiếp 10 chương.

Assistant thực hiện:

- xác định story branch đang làm;
- đọc state;
- chạy sequential chapter loop;
- tạo batch audit.

### Continue in a new conversation

User:

> Làm tiếp repo cuongtobi/xianxia-novel-maker, branch story/xxx, viết batch tiếp.

Assistant không cần lịch sử chat cũ; GitHub cung cấp state.

## 9. Orchestrator State Machine

```text
NO_STORY
  ↓ seed
SEED_SAVED
  ↓
STORY_BIBLE_READY
  ↓
STYLE_BIBLE_READY
  ↓
CHARACTERS_BIBLE_READY
  ↓
MASTER_OUTLINE_READY
  ↓
ARC_READY
  ↓
MEMORY_READY
  ↓
READY_TO_WRITE
  ↓
SCENE_PLANNED
  ↓
DRAFTED
  ↓
QC_COMPLETE
  ↓
REWRITTEN
  ↓
FINALIZED
  ↓
MEMORY_COMMITTED
  └────────→ READY_TO_WRITE
```

State được suy ra từ GitHub artifacts, không cần database riêng.

## 10. Artifact Status Rules

### Scene plan exists, no draft

Resume từ Draft.

### Draft exists, no QC

Resume từ QC; không viết lại draft vô cớ.

### QC says rewrite required, no rewrite

Resume Rewrite.

### Rewrite exists, no final

Run critical re-QC rồi final.

### Final exists, memory outdated

Không viết chapter mới. Update memory trước.

### Memory says chapter N but final only through N-1

Memory inconsistency. Kiểm tra Git history/final và sửa memory.

## 11. Title Generation

Tiêu đề chương được chốt sau rewrite, không bắt buộc giữ working title của scene plan.

Tiêu đề tốt:

- gắn sự kiện / hình ảnh / lựa chọn chính;
- không spoil twist quá lớn;
- không dùng cùng pattern quá dày;
- phù hợp văn phong truyện.

Final filename bắt buộc:

`Chương X: <Tiêu đề>.txt`

## 12. Data vs Prose Separation

Không nhét metadata vào final chapter.

- Data → bible / outline / memory / QC.
- Prose → draft / rewrite / final.
- Final → chỉ truyện.

## 13. Framework Update Protocol

Khi user yêu cầu sửa pipeline:

1. làm trên `main`;
2. đọc docs hiện hành;
3. sửa file nguồn liên quan;
4. đảm bảo AGENTS và README không mâu thuẫn;
5. không tự chỉnh story branch đang chạy;
6. báo migration note nếu framework change ảnh hưởng story cũ.

## 14. Recommended Chat Commands

### Genesis

`Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.`

### One chapter

`Viết chương tiếp theo qua đủ scene plan, draft, QC, rewrite, final và memory update.`

### Batch

`Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật memory sau từng chương.`

### Audit

`Audit 20 chương gần nhất: canon, power scaling, knowledge, Character DNA và repetition; không rewrite nếu chưa cần.`

### Repair

`Sửa các lỗi continuity đã phát hiện, ưu tiên thay đổi artifact chưa final; không retcon final nếu chưa được phép.`

## 15. What “automatic” means

Trong phạm vi ChatGPT Web, “tự động” nghĩa là khi user ra lệnh batch, assistant tự thực hiện mọi bước cần thiết trong lượt làm việc bằng GitHub tools mà không yêu cầu user duyệt từng stage.

Nó không có nghĩa có daemon chạy sau khi cuộc hội thoại kết thúc, và không được giả vờ có công việc nền chưa thực hiện.
