# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt** trên ChatGPT Web + GitHub.

Framework hiện hành: **v3.2 — Promise-Only + Atomic Combined QC**.

Controller duy nhất: **Story Promise Controller**.

## Pipeline

```text
Seed
→ Story Bible
→ Style Bible
→ Characters Bible
→ Master Outline + 3–5 Story Promises
→ Arc Outline
→ Story + Promise Memory
→ Batch 5
```

Mỗi chapter:

```text
READ
→ SCENE PLAN
→ DRAFT
→ COMBINED QC
→ FINAL
→ MEMORY UPDATE
→ ONE ATOMIC GIT COMMIT
```

`combined_qc_report.md` gồm ba phần:

- Continuity
- Story Promise
- Style

## Rewrite

Rewrite **không còn là stage mặc định**.

Nếu Combined QC = PASS:

```text
draft → final
```

Nếu Combined QC = REWRITE_REQUIRED:

- sửa candidate trong working memory;
- quick recheck finding fail;
- ghi recheck vào cùng Combined QC report;
- chỉ persist final đã pass.

Không tạo `rewrite.txt` cho chapter mới.

## Atomic chapter commit

Không write từng artifact bằng nhiều commit.

Sau khi toàn bộ chapter đã sẵn sàng:

```text
create_blob(all changed files)
→ create_tree(base_tree=chapter-start tree)
→ create_commit(parent=chapter-start HEAD)
→ update_ref once
```

Một chapter commit chứa tối thiểu:

```text
chapters/NNNN/scene_plan.md
chapters/NNNN/draft.txt
chapters/NNNN/combined_qc_report.md
final/Chương N: <title>.txt
memory/* changed files
manifest.yaml
```

Nếu là chapter cuối requested batch, cùng commit thêm `batch_NNNN_NNNN_audit.md`.

## Batch 5

Lệnh chuẩn:

```text
Viết batch 5 chương tiếp theo theo BATCH_5_WORKFLOW, tuần tự và cập nhật memory sau từng chương.
```

Mỗi chapter = một atomic commit. Không có checkpoint Ch.3 hoặc rolling audit. Batch audit chỉ tạo sau chapter thứ 5 của requested range.

## Story Promise Controller

Mỗi story khóa 3–5 promises. Per chapter dùng:

- UNTOUCHED
- ADVANCE
- PAY_MINOR
- PAY_MAJOR
- PAY_ARC

Theo dõi last PAY, major PAY, drought và planned payoff window. Setup/lời hứa tương lai không tự tính PAY.

## Artifact structure

```text
stories/<slug>/
├── manifest.yaml
├── seed/seed.yaml
├── bible/
├── outline/
├── chapters/
│   ├── 0001/
│   │   ├── scene_plan.md
│   │   ├── draft.txt
│   │   └── combined_qc_report.md
│   └── batch_0001_0005_audit.md
├── final/
│   └── Chương X: <Tiêu đề>.txt
└── memory/
```

Historical story branches có thể vẫn chứa report/rewrite/rolling-audit cũ; giữ làm lịch sử nhưng không tiếp tục sinh ở v3.2.

## Source of truth

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

## Core docs

- `AGENTS.md`
- `docs/ARCHITECTURE.md`
- `docs/BATCH_5_WORKFLOW.md`
- `docs/GITHUB_CHATGPT_PROTOCOL.md`
- `docs/READER_EXPERIENCE_SYSTEM.md`
- `prompts/PIPELINE_PROMPTS.md`
- `templates/combined_qc_report.template.md`

## Principle

```text
GitHub giữ sự thật.
Bible giữ luật.
Character DNA giữ con người.
Story Promise giữ lời hứa.
Combined QC giữ chất lượng.
Atomic commit giữ transaction sạch.
Final giữ tác phẩm.
Memory giữ continuity.
```
