# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt**, vận hành bằng **ChatGPT Web + GitHub**.

GitHub giữ persistent state/source of truth. ChatGPT đóng vai orchestrator + architect + writer + auditor.

Pipeline v2.1 tối ưu đồng thời:

- canon/continuity;
- Character DNA + agency;
- Story Promise delivery;
- Narrative Engine diversity;
- Xianxia Experience;
- Emotional Residue;
- prose naturalness;
- power/resource consistency.

## 1. Pipeline

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
Rolling 3-Chapter Audit when N % 3 == 0
↓
Final TXT
↓
Story Memory + Reader Experience Memory
↓
Next chapter
```

**Default production batch = 5 chapters.**

## 2. Quick Start

Kết nối repo:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker
```

Framework ở `main`. Mỗi story ở `story/<slug>`.

Tạo truyện mới:

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

Viết batch mặc định:

```text
Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

Hoặc ngắn hơn:

```text
Viết batch tiếp theo đúng pipeline.
```

Nếu user không ghi số khác, `batch tiếp theo` = **5 chương**.

## 3. Seed

Template:

`templates/seed.template.yaml`

Default production:

```yaml
production:
  batch_size: 5
  auto_run_batch: true
  require_qc: true
  require_rewrite: true
```

Seed có thể để trống field để AI tự resolve nếu không thuộc `user_must_decide`.

## 4. Story branch structure

```text
stories/<slug>/
├── manifest.yaml
├── seed/seed.yaml
├── bible/
│   ├── story_bible.md
│   ├── style_bible.md
│   └── characters_bible.md
├── outline/
│   ├── master_outline.md
│   └── arcs/arc_001.md
├── chapters/
│   ├── 0001/
│   │   ├── scene_plan.md
│   │   ├── draft.txt
│   │   ├── continuity_report.md
│   │   ├── reader_retention_report.md
│   │   ├── style_fingerprint_report.md
│   │   ├── quality_report.md
│   │   ├── rewrite.txt
│   │   └── rolling_3_chapter_audit.md   # only when due
│   └── batch_0001_0005_audit.md
├── final/
│   └── Chương X: <Tiêu đề>.txt
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

## 5. Genesis

```text
Seed
→ Story Bible
→ Style Bible
→ Characters Bible
→ Master Outline + Story Promises
→ Arc 1 Outline
→ Initialize Story Memory
→ Initialize Reader Experience Memory
→ READY_TO_WRITE
```

### Story Promises

Mỗi truyện khóa 3–5 promise. Mỗi promise định nghĩa:

- `PAY` thật là gì;
- `ADVANCE` là gì;
- false pay;
- drought warning;
- escalation path.

Setup không được tự tính là payoff.

## 6. Chapter transaction

Mỗi chapter là transaction tuần tự:

```text
Context Assembly
→ Scene Plan
→ Draft
→ 3-mode QC
→ Aggregate Gate
→ Rewrite
→ Critical Re-QC
→ Rolling 3-Chapter Audit if due
→ Final
→ Story Memory
→ Reader Experience Memory
```

Không viết chapter N+1 khi memory của N chưa cập nhật.

### Relaxed scene planning

Conflict/transaction scene có thể plan goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene không bị ép đủ mini-plot; chỉ cần focal tension/curiosity, sensory anchor, knowledge boundary và meaningful movement/residue.

## 7. QC architecture

Ba reviewer độc lập:

### Continuity Auditor

- canon;
- timeline/geography;
- cultivation/power;
- technique/item;
- injury/fatigue;
- knowledge;
- relationship/faction;
- POV boundary;
- hard DNA/runtime contradiction.

### Reader Retention Editor

- Story Promise PAY/drought;
- Narrative Engine;
- pacing/drag;
- character agency/humanity;
- costly mistakes;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

### Style Fingerprint Auditor

- `Không X. Mà Y.` density;
- Q&A cleanliness;
- hypothesis-loop;
- aphorism density;
- paragraph/cadence repetition;
- dialogue sameness;
- positive prose texture;
- calibration drift.

`quality_report.md` aggregate cả ba. Không PASS nếu còn BLOCKER/MAJOR.

## 8. Narrative Engine

Narrative Engine là **cách chapter tạo chuyển động**, không phải topic.

Ví dụ:

`Q&A meeting / audit / negotiation / hypothesis-test / training calibration / chase / reveal / ritual / domestic / combat / grief / wonder / investigation / survival task / repair-build / travel discovery / aftermath / rescue / moral choice / competition`

Hard rule:

**rolling 4 chapters mà 3/4 cùng primary engine = MAJOR pacing risk.**

Batch boundary không reset rule.

## 9. Rolling 3-Chapter Audit

Chạy trước final tại:

`3, 6, 9, 12, 15, 18...`

Đọc full N-2 + N-1 + candidate N.

Kiểm:

- opening shape;
- engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- promise PAY;
- Xianxia Experience;
- Emotional Residue.

Batch size 5 không đổi cadence này.

## 10. Batch 5 Workflow

Tài liệu chi tiết:

`docs/BATCH_5_WORKFLOW.md`

Default ranges:

```text
Batch 1: Ch.1–5
Batch 2: Ch.6–10
Batch 3: Ch.11–15
Batch 4: Ch.16–20
...
```

Mỗi batch vẫn viết tuần tự từng chapter.

Cuối batch tạo:

```text
chapters/batch_0001_0005_audit.md
chapters/batch_0006_0010_audit.md
chapters/batch_0011_0015_audit.md
...
```

Batch audit kiểm artifact completion + story experience xuyên range.

## 11. Reader Experience Memory

`memory/reader_experience.md` lưu:

- promise last ADVANCE/PAY;
- last major payoff;
- last wonder beat;
- last emotional hit;
- last costly mistake;
- recent primary/secondary engines;
- dialogue geometries;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- current reader appetite/payoff debt.

Planner đọc file này trước chapter mới để biết độc giả vừa trải qua loại trải nghiệm gì.

## 12. Xianxia Experience + Emotional Residue

Theo dõi riêng fantasy experience:

- cultivation payoff;
- wonder/awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- magical craft;
- world-scale glimpse.

Trong rolling 3–5 chapter cũng cần meaningful emotional/relationship/self-image movement; không ép melodrama giả.

## 13. Human irrationality

Character DNA cho phép bias, sĩ diện, shame, attachment, sunk cost, fear, loyalty, incomplete data và impulsive kindness.

Nhân vật thông minh không phải optimizer hoàn hảo. MC đôi lúc phải sai thật và trả cost thật; supporting cast không luôn sửa lỗi trước hậu quả.

## 14. Calibration

Không auto-calibrate từ Ch.1–3.

Chỉ khóa calibration khi có 4–6 đoạn được duyệt/final, thuộc ít nhất 4 Narrative Engine khác nhau. Mỗi chapter dùng 2–3 sample phù hợp rồi xoay vòng.

## 15. Source of truth

```text
1. Canon Ledger
2. Final Chapters
3. Bibles
4. Memory
5. Arc Outline
6. Master Outline
7. Seed
8. Draft/Scene Plan
```

Outline = plan. Final = event. Canon Ledger = locked fact.

## 16. Resume ở chat mới

Lệnh:

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker.
Tiếp tục branch story/<slug> và viết batch 5 chương tiếp theo đúng pipeline.
```

Đọc tối thiểu:

- `AGENTS.md`;
- `docs/BATCH_5_WORKFLOW.md`;
- manifest;
- seed;
- current state;
- reader experience;
- batch audit gần nhất;
- arc hiện tại;
- bibles/ledgers liên quan;
- recent summaries/final.

## 17. Legacy story / batch-size migration

Story từng chạy batch 10 không cần xóa/chia audit lịch sử.

Ví dụ `batch_0001_0010_audit.md` vẫn là historical checkpoint hợp lệ.

Khi sync framework mới:

```yaml
pipeline:
  version: "2.1"
  batch_size: 5
  batch_workflow: "docs/BATCH_5_WORKFLOW.md"
```

Nếu story đã final Ch.10, batch mới mặc định là Ch.11–15.

Không fake retroactive split audit 1–5 / 6–10 nếu 1–10 đã audit hợp lệ.

## 18. Completion gate

Batch chỉ được báo READY/PASS khi:

- đủ 5 final mặc định hoặc đủ requested range;
- per-chapter artifacts đầy đủ trong enforcement window;
- rolling audits đến hạn tồn tại;
- story memory + reader experience cập nhật tới chapter cuối;
- batch audit tồn tại;
- không còn BLOCKER/MAJOR;
- next-batch handoff rõ.

Thiếu artifact → `INCOMPLETE`.

## 19. Final filename

```text
Chương X: <Tiêu đề>.txt
```

Final chỉ chứa title + story prose UTF-8 plain text.

## 20. Tài liệu framework

- `AGENTS.md`
- `docs/ARCHITECTURE.md`
- `docs/GITHUB_CHATGPT_PROTOCOL.md`
- `docs/BATCH_5_WORKFLOW.md`
- `docs/READER_EXPERIENCE_SYSTEM.md`
- `docs/FRAMEWORK_V2_MIGRATION.md`
- `memory/MEMORY_SYSTEM.md`
- `prompts/PIPELINE_PROMPTS.md`
- `templates/*.template.*`

## Nguyên tắc cuối

```text
GitHub giữ sự thật.
Bible giữ luật.
Character DNA giữ con người.
Story Promise giữ lời hứa.
Narrative Engine giữ độ đa dạng.
QC giữ chất lượng.
Final giữ tác phẩm.
Memory giữ continuity.
Reader Experience Memory giữ trải nghiệm độc giả.
Batch 5 giữ vòng sản xuất ngắn, dễ kiểm soát và dễ điều chỉnh.
```
