# Stories Workspace — v4.0

Story data lives on each `story/<slug>` branch.

Do not put real story instances on `main`; `main` keeps framework, docs, templates and bootstrap examples.

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
│   └── master_outline.md
├── examples/
│   └── style/
│       ├── index.md
│       └── *.txt
├── chapters/
│   ├── 0001/
│   │   ├── chapter_state.md
│   │   ├── scene_state.md
│   │   ├── draft.txt
│   │   └── continuity_check.md
│   └── batch_0001_0005_audit.md
├── final/
│   └── Chương X: <Tiêu đề>.txt
└── memory/
    ├── story_state.md
    ├── arc_state.md
    ├── character_states.md
    └── ...continuity ledgers/summaries
```

## Branch naming

`story/<slug>`

Slug should remain stable for the life of the story.

## Chapter directory

Use four digits for stable sorting:

- `chapters/0001/`
- `chapters/0002/`
- ...
- `chapters/0127/`

## Batch audit

Default batch = 5 chapters.

Examples:

- `chapters/batch_0001_0005_audit.md`
- `chapters/batch_0006_0010_audit.md`

Audit is included in the atomic commit of the fifth requested chapter.

## Resume rule

A new ChatGPT session does not need prior chat history.

Read exact story branch, then:

1. `manifest.yaml`;
2. `memory/story_state.md`;
3. `memory/arc_state.md`;
4. relevant `memory/character_states.md` and continuity ledgers;
5. recent summaries/final as needed;
6. Master/Bibles only for stable facts or long direction.

Do not resume from verbal chat state when GitHub disagrees.

## Legacy stories

Older branches may contain `scene_plan.md`, `combined_qc_report.md`, `quality_report.md`, `rewrite.txt` or older batch ranges. Preserve them as history. From the v4 migration cutoff forward, use the v4 layout only.
