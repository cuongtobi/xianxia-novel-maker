# AGENTS.md — Operating Contract

## 1. Core architecture

Framework hiện hành dùng **một controller duy nhất: Story Promise Controller**.

Mỗi chapter dùng transaction tối giản:

```text
READ CONTEXT
→ SCENE PLAN
→ DRAFT
→ COMBINED QC
→ FINAL
→ MEMORY UPDATE
→ ONE ATOMIC GIT COMMIT
```

`combined_qc_report.md` chứa ba phần duy nhất:

1. Continuity;
2. Story Promise;
3. Style.

Không tạo riêng `continuity_report.md`, `reader_retention_report.md`, `style_fingerprint_report.md`, `quality_report.md` hay `rewrite.txt` cho chapter mới.

## 2. Controller boundary

Controller duy nhất: **Story Promise Controller**.

Không chạy Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration, Heat, Binge, Xianxia Experience, Xianxia Density, Emotional Residue hay Human Irrationality Controller.

Continuity và Style là QC kỹ thuật, không phải controller sáng tác.

## 3. Roles

- Orchestrator: xác định stage, assemble context, điều phối transaction và verify commit.
- World/Story/Character/Style Architects: tạo Bible/Outline.
- Story Promise Controller: khóa 3–5 promises và theo dõi payoff.
- Scene Planner: plan gọn.
- Writer: viết prose theo canon + Style Bible.
- Combined QC Reviewer: kiểm Continuity + Story Promise + Style trong một report.
- Memory Keeper: chuẩn bị toàn bộ memory/manifest updates trước atomic commit.

## 4. Source of truth

1. `memory/canon_ledger.md`
2. final chapters
3. `bible/*.md`
4. `memory/*.md`
5. arc outline
6. master outline
7. seed
8. draft/scene plan

Outline = plan. Final + canon ledger = chuyện đã xảy ra.

## 5. Read-before-write

Trước chapter mới đọc tối thiểu:

- manifest + seed;
- Story/Style/Characters Bible phần liên quan;
- Story Promises;
- arc hiện tại;
- current state + promise memory;
- ledgers cần thiết;
- 3 recent summaries;
- full final gần nhất khi continuity trực tiếp cần.

Không reread toàn lịch sử nếu summary/ledger đủ.

## 6. Story Promise Controller

Genesis khóa 3–5 promises. Mỗi promise có stable ID, reader value, PAY definition, ADVANCE definition, false pay, drought warning và escalation path.

Per chapter dùng:

- `UNTOUCHED`
- `ADVANCE`
- `PAY_MINOR`
- `PAY_MAJOR`
- `PAY_ARC`

Theo dõi `last_pay_chapter`, `last_major_pay_chapter`, `pay_drought`, next planned payoff window. Không fake payoff chỉ để clear drought.

## 7. Scene plan

Chỉ cần:

- objective;
- POV/time/place/cast;
- start state;
- conflict/pressure;
- key beats/turn;
- choice/consequence nếu có;
- Story Promise target + payoff nếu có;
- end state;
- continuity constraints;
- style constraints;
- hook nếu organic.

## 8. Draft

Writer ưu tiên truyện trước checklist. Prose Việt tự nhiên, POV nhất quán, dialogue theo DNA, worldbuilding qua tình huống, cultivation/craft/combat đủ rõ nhưng không thành manual/log.

## 9. Combined QC

Một reviewer đọc draft và ghi **một** `combined_qc_report.md`.

### Continuity
Kiểm canon, timeline, geography, cultivation/power, item/resource/injury, knowledge, relationship/faction, POV và hard DNA contradiction.

### Story Promise
Kiểm target có chạm thật không, ADVANCE/PAY classification, magnitude, false pay, drought.

### Style
Kiểm AI-like fingerprints, fragment/cadence abuse, Q&A quá sạch, hypothesis-loop, aphorism/recap/exposition, lexical tics, dialogue sameness và house-style/reference drift.

Severity: `BLOCKER / MAJOR / MINOR / NOTE`.

- còn BLOCKER/MAJOR cần sửa trong chapter → `REWRITE_REQUIRED`;
- chỉ MINOR/NOTE hoặc không finding → `PASS`.

## 10. Rewrite policy

**Rewrite chỉ chạy khi Combined QC = REWRITE_REQUIRED.**

Nếu draft PASS:

```text
draft → final
```

Final phải dùng nguyên prose draft; không tạo bản rewrite gần giống chỉ vì workflow.

Nếu cần rewrite, sửa trong memory làm việc, không persist `rewrite.txt`. Sau sửa, Combined QC report ghi thêm `Rewrite Recheck` và final dùng candidate đã pass.

Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`. Structural failure → re-plan/re-draft trong transaction. Không patch-expansion để clear checklist.

## 11. Atomic Git chapter transaction

**Không ghi GitHub từng artifact trong lúc đang xử lý chapter.**

Quy trình bắt buộc:

1. lấy branch HEAD + base tree;
2. assemble context;
3. tạo scene plan, draft, combined QC;
4. nếu cần, rewrite/recheck trong memory làm việc;
5. tạo final;
6. tính toàn bộ memory/ledger/summary/manifest updates;
7. nếu chapter cuối batch, tạo batch audit;
8. tạo blob cho tất cả file mới/thay đổi;
9. `create_tree(base_tree=<chapter-start tree>)`;
10. `create_commit(parent=<chapter-start HEAD>)`;
11. `update_ref` branch đúng **một lần**;
12. verify HEAD + manifest/memory.

Chapter commit phải chứa tối thiểu:

- `chapters/NNNN/scene_plan.md`
- `chapters/NNNN/draft.txt`
- `chapters/NNNN/combined_qc_report.md`
- `final/Chương N: <title>.txt`
- tất cả memory/ledger/summary thay đổi
- manifest update
- batch audit nếu N là chapter cuối requested batch.

Nếu phiên lỗi trước `update_ref`, chapter **chưa hoàn tất** và branch không được coi là đã tiến state.

## 12. Batch 5

Viết tuần tự 5 chapter; mỗi chapter = một atomic commit. Chapter N+1 chỉ bắt đầu sau khi commit N đã verify thành công.

Không có checkpoint Ch.3. Batch audit chỉ tạo sau chapter thứ 5 của requested range và nên nằm trong atomic commit của chapter đó.

## 13. Completion

Chapter COMPLETE khi atomic commit đã chứa scene plan, draft, combined QC PASS, final và memory/manifest current.

Batch COMPLETE khi đủ 5 requested finals/commits, memory current qua chapter cuối và batch audit tồn tại.
