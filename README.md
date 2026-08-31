# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt** bằng ChatGPT Web + GitHub.

Framework hiện hành dùng triết lý **promise-first, controller-light**: chỉ giữ **Story Promise Controller**. Continuity và Style vẫn được QC bằng auditor, nhưng không phải controller sáng tác.

## Pipeline

```text
Seed
→ Story Bible
→ Style Bible
→ Characters Bible
→ Master Outline + 3–5 Story Promises
→ Arc Outline + Promise PAY windows
→ Story Memory + Promise Memory
→ Scene Plan
→ Draft
→ Continuity Auditor
→ Story Promise Reviewer
→ Style Fingerprint Auditor
→ Aggregate Quality Gate
→ Rewrite if needed
→ Final TXT
→ Update Memory
→ Next chapter
```

Default batch = **5 chương**, viết tuần tự.

## Controller duy nhất

### Story Promise Controller

Mỗi truyện khóa 3–5 lời hứa độc giả. Mỗi promise có:

- ID;
- promise;
- lý do reader quan tâm;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

Per chapter dùng:

`UNTOUCHED / ADVANCE / PAY_MINOR / PAY_MAJOR / PAY_ARC`.

Payoff magnitude là một phần của Story Promise, không phải controller riêng.

## Đã loại bỏ khỏi pipeline

Không còn controller/gate/quota bắt buộc cho:

- Narrative Engine;
- Dramatic Geometry;
- Competence Friction;
- Aspiration;
- Heat Curve;
- Binge Test;
- Xianxia Experience;
- Xianxia Density;
- Emotional Residue;
- Human Irrationality.

Các yếu tố như nhịp, cảm xúc, wonder, sai lầm hay chất tiên hiệp vẫn được Writer/Story Bible/Style Bible xử lý tự nhiên, nhưng không bị đo thành rolling metric.

## Quick start

```text
@GitHub làm việc với repo cuongtobi/xianxia-novel-maker
```

Tạo truyện:

```text
Dùng seed này tạo story branch mới và chạy toàn bộ Genesis đến khi sẵn sàng viết chương 1.
```

Viết batch:

```text
Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

## Branch model

- Framework: `main`
- Story: `story/<slug>`

Framework changes không tự áp vào story branch cũ; story cũ cần sync/migrate riêng.

## Story tree

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
│   │   ├── reader_retention_report.md   # compatibility filename; content = Story Promise Review
│   │   ├── style_fingerprint_report.md
│   │   ├── quality_report.md
│   │   └── rewrite.txt                  # only when needed/configured
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
    └── reader_experience.md             # Promise runtime state only
```

## Chapter transaction

```text
Context Assembly
→ Scene Plan
→ Draft
→ Continuity Audit
→ Story Promise Review
→ Style Audit
→ Aggregate Gate
→ Rewrite if needed
→ Critical Re-QC
→ Final
→ Story Memory
→ Promise Memory
```

Không có Rolling 3-Chapter Audit bắt buộc.

## Rewrite discipline

Rewrite ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD` và mặc định không làm final dài hơn draft quá khoảng 25%. Lỗi cấu trúc lớn nên re-plan/re-draft thay vì vá dài.

## Source of truth

```text
1. Canon Ledger
2. Final Chapters
3. Bibles
4. Memory
5. Arc Outline
6. Master Outline
7. Seed
8. Draft / Scene Plan
```

## Tài liệu chính

- `AGENTS.md`
- `docs/ARCHITECTURE.md`
- `docs/BATCH_5_WORKFLOW.md`
- `docs/READER_EXPERIENCE_SYSTEM.md`
- `docs/REFERENCE_STYLE_SYSTEM.md`
- `docs/GITHUB_CHATGPT_PROTOCOL.md`
- `memory/MEMORY_SYSTEM.md`
- `prompts/PIPELINE_PROMPTS.md`
- `templates/*.template.*`

## Nguyên tắc cuối

```text
GitHub giữ sự thật.
Bible giữ luật.
Character DNA giữ con người.
Story Promise giữ lời hứa.
QC bắt lỗi.
Writer viết truyện, không viết để clear metric.
```
