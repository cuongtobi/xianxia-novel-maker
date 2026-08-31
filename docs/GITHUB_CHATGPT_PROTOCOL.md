# ChatGPT Web + GitHub Protocol

## 1. Mục đích

Tài liệu này định nghĩa cách vận hành pipeline hoàn toàn qua hội thoại ChatGPT và GitHub connector/plugin.

Không cần một service chạy nền. GitHub là persistent memory; ChatGPT là execution engine theo từng phiên.

Pipeline v2 quản song song:

- story correctness;
- reader experience.

## 2. Repository model

- Framework branch: `main`
- Story branch: `story/<slug>`
- Một story branch chỉ chứa dữ liệu của một truyện trong `stories/<slug>/`.
- Framework có thể được cải tiến trên `main`; story đang chạy **không tự động nhận thay đổi** trừ khi user yêu cầu đồng bộ.

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
stories/<slug>/memory/reader_experience.md
```

### Step 4 — Seed validation

Không hỏi lại phần user đã cung cấp. Chỉ xác định:

- contradiction;
- missing critical constraint;
- creative blanks AI được phép quyết định;
- content user bắt buộc quyết định;
- candidate reader promises từ premise/hook.

Nếu không có blocker, tự tiếp tục Genesis.

### Step 5 — Genesis

Chạy theo thứ tự:

1. Story Bible
2. Style Bible
3. Characters Bible
4. Master Outline + lock 3–5 Story Promises
5. Arc 1 Outline + Narrative Engine/Xianxia/Emotional maps
6. Initialize Story State Memory
7. Initialize Reader Experience Memory

Mỗi stage đọc output trước đó.

READY_TO_WRITE chỉ hợp lệ khi Story Promises và `reader_experience.md` đã initialized.

## 4. How ChatGPT Should Read GitHub

### Framework session start

Đọc:

- `AGENTS.md`
- `docs/READER_EXPERIENCE_SYSTEM.md`
- tài liệu workflow liên quan.

### Story session start

Đọc từ đúng branch:

- seed;
- current_state;
- `reader_experience.md`;
- master Story Promise section;
- arc hiện tại;
- bible liên quan;
- memory ledgers liên quan;
- batch audit gần nhất nếu có;
- artifact tree chapter gần nhất.

### Targeted reads

Không tải toàn bộ hàng trăm chapter. Dùng filename, summary và ledger.

Nhưng phải đọc full final khi:

- continuity trực tiếp;
- callback cụ thể;
- Reader Retention/Style Fingerprint cần so repetition;
- Rolling 3-Chapter Audit yêu cầu full N-2/N-1.

## 5. How ChatGPT Should Write GitHub

### Framework files

Ghi vào `main` chỉ khi user đang phát triển pipeline.

### Story files

Ghi vào `story/<slug>`.

Không ghi story artifact lên `main`.

### Atomicity rule — chapter N

1. `scene_plan.md`
2. `draft.txt`
3. `continuity_report.md`
4. `reader_retention_report.md`
5. `style_fingerprint_report.md`
6. `quality_report.md` aggregate
7. `rewrite.txt` nếu required/config
8. critical re-QC
9. `rolling_3_chapter_audit.md` nếu `N % 3 == 0`
10. final TXT
11. update story memory
12. update `reader_experience.md`
13. refresh `current_state.md`

Nếu dừng giữa chừng, `final/` không được giả vờ đã hoàn tất.

## 6. Commit Strategy

Khuyến nghị:

- Genesis: 1–3 commits theo nhóm bible/outline/memory.
- Production: 1 commit/chapter hoặc 1 commit chapter artifacts + 1 memory commit.
- Batch audit: 1 commit cuối batch.

Commit message gợi ý:

- `story: bootstrap <slug>`
- `story: build bible for <slug>`
- `story: lock promises for <slug>`
- `story: outline opening arc for <slug>`
- `chapter: finalize ch 001 <slug>`
- `memory: update through ch 001 <slug>`
- `audit: rolling ch 001-003 <slug>`
- `audit: batch 001-010 <slug>`

Không bắt buộc đúng literal, nhưng lịch sử phải dễ đọc.

## 7. Branch Safety

Trước mọi write:

- xác nhận repository full name;
- xác nhận story slug;
- xác nhận branch;
- story path bắt đầu bằng `stories/<same-slug>/`;
- framework write chỉ vào `main`.

Nếu user chuyển truyện giữa phiên, reset context assembly và đọc branch mới.

## 8. Standard User Interaction

### Create story

User:

> Tạo truyện mới theo seed sau...

Assistant:

- tạo branch;
- lưu seed;
- Genesis;
- lock promises;
- initialize both memories;
- báo artifact chính đã tạo.

### Write batch

User:

> Viết tiếp 10 chương.

Assistant:

- xác định story branch;
- đọc story + reader state;
- verify previous artifact completion;
- chạy sequential chapter loop;
- rolling audit tại 3/6/9/...;
- tạo batch audit;
- verify completion gate.

### Continue in a new conversation

User:

> Làm tiếp repo ..., branch story/xxx, viết batch tiếp.

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
  ↓ Story Promises locked
PROMISES_READY
  ↓
ARC_READY
  ↓
STORY_MEMORY_READY
  ↓
READER_MEMORY_READY
  ↓
READY_TO_WRITE
  ↓
SCENE_PLANNED
  ↓
DRAFTED
  ↓
CONTINUITY_QC_COMPLETE
  ↓
RETENTION_QC_COMPLETE
  ↓
STYLE_QC_COMPLETE
  ↓
AGGREGATE_QC_COMPLETE
  ↓
REWRITTEN
  ↓
ROLLING_AUDIT_COMPLETE (when due)
  ↓
FINALIZED
  ↓
STORY_MEMORY_COMMITTED
  ↓
READER_MEMORY_COMMITTED
  └────────→ READY_TO_WRITE
```

State được suy ra từ **artifact thật trên GitHub**, không cần database riêng.

## 10. Artifact Status Rules

### Scene plan exists, no draft

Resume Draft.

### Draft exists, one/more reviewer report missing

Resume đúng reviewer còn thiếu. Không coi `quality_report.md` cũ là thay thế ba reviewer.

### Three reviewer reports exist, aggregate missing

Resume Aggregate QC.

### Aggregate says rewrite required, no rewrite

Resume Rewrite.

### Rewrite exists, rolling audit due but missing

Run/re-run affected reviewer, aggregate, rồi Rolling 3-Chapter Audit. Không final.

### Rolling audit has MAJOR

Rewrite current candidate, rerun affected QC + rolling audit.

### Rewrite exists, no final, all gates PASS

Run critical re-QC rồi final.

### Final exists, story memory outdated

Không viết chapter mới. Update memory.

### Story memory current nhưng `reader_experience.md` outdated

Vẫn `INCOMPLETE`. Update reader memory trước chapter mới.

### Memory says chapter N but final only through N-1

Memory inconsistency. Kiểm final/Git history rồi sửa memory.

### 10 finals exist but `batch_NNNN_NNNN_audit.md` missing

Batch `INCOMPLETE`. Tạo audit trước khi báo hoàn tất.

## 11. Story Promise / Reader Experience Status

Orchestrator phải biết:

- 3–5 promise đã khóa;
- last ADVANCE/PAY;
- current drought;
- recent engines;
- recent endings;
- recent rhetorical tics;
- last wonder/emotional hit;
- current payoff debt.

`ADVANCE` không được tự đổi thành `PAY` chỉ để tránh warning.

## 12. Rolling Audit Protocol

Trigger: trước final các chapter chia hết cho 3.

Read full:

- N-2 final;
- N-1 final;
- N rewrite candidate.

Check:

- opening shape;
- Narrative Engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- Story Promise PAY;
- Xianxia Experience;
- Emotional Residue.

Output:

`chapters/NNNN/rolling_3_chapter_audit.md`

Nếu MAJOR, sửa current N; không retcon N-2/N-1 chỉ để tạo variety.

## 13. Title Generation

Tiêu đề chương chốt sau rewrite, không bắt buộc giữ working title.

Tiêu đề tốt:

- gắn sự kiện/hình ảnh/lựa chọn;
- không spoil twist lớn;
- không dùng cùng pattern quá dày;
- phù hợp style bible.

Final filename:

`Chương X: <Tiêu đề>.txt`

## 14. Data vs Prose Separation

- Data → bible / outline / memory / QC.
- Prose → draft / rewrite / final.
- Reader-production state → `reader_experience.md`.
- Final → chỉ truyện.

Không nhét metadata/controller labels vào final.

## 15. Framework Update Protocol

Khi user yêu cầu sửa pipeline:

1. làm trên `main`;
2. đọc docs hiện hành;
3. sửa source files + templates liên quan;
4. đảm bảo `AGENTS.md`, Architecture, Batch Workflow, Protocol và README không mâu thuẫn;
5. không tự chỉnh story branch đang chạy;
6. báo migration note nếu framework change ảnh hưởng story cũ;
7. verify file tree sau update.

## 16. Recommended Chat Commands

### Genesis

`Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.`

### One chapter

`Viết chương tiếp theo qua đủ scene plan, 3-mode QC, rewrite, rolling audit nếu đến kỳ, final và memory update.`

### Batch

`Viết batch 10 chương tiếp theo theo BATCH_10_WORKFLOW, tuần tự và cập nhật story + reader memory sau từng chương.`

### Audit continuity

`Audit continuity 20 chương gần nhất; không rewrite nếu chưa cần.`

### Audit retention

`Audit Story Promise, Narrative Engine, Xianxia Experience và Emotional Residue 10 chương gần nhất.`

### Audit style fingerprint

`Audit rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density và ending repetition 10 chương gần nhất.`

### Repair

`Sửa các lỗi đã phát hiện, ưu tiên artifact chưa final; không retcon final nếu chưa được phép.`

## 17. What “automatic” means

Trong ChatGPT Web, “tự động” nghĩa là khi user ra lệnh batch, assistant tự thực hiện mọi bước cần thiết trong lượt làm việc bằng GitHub tools mà không yêu cầu duyệt từng stage.

Nó không có nghĩa có daemon chạy sau khi hội thoại kết thúc, và không được giả vờ có công việc nền chưa thực hiện.

## 18. Completion wording

Chỉ dùng từ như `hoàn tất`, `PASS`, `READY_TO_WRITE`, `ready for next batch` khi Artifact Completion Gate đã verify.

Nếu nội dung chính đã viết nhưng thiếu report/memory/audit bắt buộc, phải nói rõ:

`INCOMPLETE — missing <artifact>`.
