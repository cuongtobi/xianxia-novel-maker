# Stories Workspace

Thư mục này chứa dữ liệu truyện trên từng `story/<slug>` branch.

Không đặt nội dung truyện thật trên `main`; `main` chỉ giữ framework và template.

## Story instance layout

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
│   └── arcs/
├── chapters/
├── final/
└── memory/
```

## Branch naming

`story/<slug>`

Slug phải ổn định suốt vòng đời truyện.

## Chapter directory

Dùng 4 chữ số để sort đúng:

- `chapters/0001/`
- `chapters/0002/`
- ...
- `chapters/0127/`

Mỗi chapter directory chuẩn:

```text
scene_plan.md
draft.txt
quality_report.md
rewrite.txt
```

Final nằm riêng trong `final/` với tên phát hành:

`Chương X: <Tiêu đề>.txt`

## Batch audit

Ví dụ:

`chapters/batch_0001_0010_audit.md`

`chapters/batch_0011_0020_audit.md`

## Resume rule

Một phiên ChatGPT mới không cần lịch sử chat trước. Chỉ cần branch story và repository, sau đó đọc `manifest.yaml`, `memory/current_state.md`, arc hiện tại và các bible theo protocol.
