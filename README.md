# Xianxia Novel Maker

Pipeline viết truyện dài tập **tiên hiệp / tu tiên / huyền huyễn bằng tiếng Việt**, vận hành trực tiếp bằng **ChatGPT Web + GitHub**.

## Mục tiêu

- Mỗi truyện là một branch độc lập: `story/<slug>`.
- Người dùng khởi tạo truyện bằng một `seed.yaml` theo mẫu chuẩn.
- GitHub là **source of truth** cho canon, outline, memory, chapter artifacts và bản final.
- ChatGPT đóng vai trò **orchestrator + writer + editor + continuity checker**.
- Pipeline hỗ trợ viết theo **batch 10 chương**, nhưng xử lý tuần tự từng chương để giữ continuity.
- Mỗi chương phải qua: scene plan → draft → quality check → rewrite → final → memory update.
- Văn phong đích: tiếng Việt tự nhiên, có khí chất tiên hiệp/tu tiên, tránh cảm giác văn mẫu và dấu vết máy móc.

## Pipeline chuẩn

`Seed → Story Bible → Style Bible → Characters Bible → Master Outline → Arc Outline → Chapter Scene → Draft → Quality Check → Rewrite → Final TXT → Memory Update`

## Cấu trúc một story branch

```text
stories/<story-slug>/
├── seed/
│   └── seed.yaml
├── bible/
│   ├── story_bible.md
│   ├── style_bible.md
│   └── characters_bible.md
├── outline/
│   ├── master_outline.md
│   └── arcs/
│       └── arc_001.md
├── chapters/
│   └── 0001/
│       ├── scene_plan.md
│       ├── draft.txt
│       ├── quality_report.md
│       └── rewrite.txt
├── final/
│   └── Chương 1: Tên chương.txt
└── memory/
    ├── current_state.md
    ├── canon_ledger.md
    ├── timeline.md
    ├── character_states.md
    ├── relationships.md
    ├── cultivation_ledger.md
    ├── inventory_artifacts.md
    ├── factions_locations.md
    ├── foreshadowing.md
    ├── unresolved_threads.md
    ├── knowledge_ledger.md
    └── chapter_summaries.md
```

> Lưu ý: dấu `:` trong tên file hợp lệ trên GitHub nhưng không tương thích khi checkout trực tiếp trên Windows. Pipeline vẫn dùng đúng format final do dự án yêu cầu. Nếu cần local Windows, có thể đổi quy ước filename riêng mà không thay đổi tiêu đề hiển thị.

## Quy tắc bất biến

1. Không viết chương mới nếu chưa đọc đủ memory liên quan và outline hiện hành.
2. Không tự ý retcon canon. Mọi thay đổi canon phải được ghi rõ và có lý do.
3. Power scaling, timeline, tri thức nhân vật, quan hệ, vật phẩm và thương tích phải được kiểm tra trước khi final.
4. Nhân vật phải hành động theo Character DNA; không được biến thành công cụ đẩy cốt truyện.
5. Batch 10 chương không đồng nghĩa 10 chương viết độc lập. Chương sau phải đọc final + memory update của chương trước.
6. Bản `final/` chỉ được tạo sau khi QC đạt chuẩn và rewrite đã xử lý toàn bộ lỗi nghiêm trọng.
7. Sau mỗi chương final, memory phải cập nhật ngay trước khi sang chương tiếp theo.

## Bắt đầu

Đọc theo thứ tự:

1. `AGENTS.md`
2. `docs/ARCHITECTURE.md`
3. `templates/seed.template.yaml`
4. `docs/GITHUB_CHATGPT_PROTOCOL.md`
5. `docs/BATCH_10_WORKFLOW.md`
6. `prompts/PIPELINE_PROMPTS.md`

Khi tạo truyện mới, tạo branch `story/<slug>`, copy seed template vào `stories/<slug>/seed/seed.yaml`, điền seed, rồi chạy pipeline từ Stage 1.
