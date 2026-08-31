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

## 3. Reference Prose boundary

Reference Style mode hiện hành: **`prose_mechanics_only`**.

Reference profile chỉ được ảnh hưởng:

- sentence architecture/rhythm;
- clause flow/transitions;
- diction/Hán Việt balance;
- paragraph rhythm;
- narration stance;
- internal monologue compression;
- dialogue prose;
- description density;
- action/combat prose;
- exposition handling;
- emotional understatement ở cấp câu chữ;
- repetition limits;
- Vietnamese adaptation filter.

Reference profile **không được ảnh hưởng**:

- premise;
- plot/arc;
- Character DNA;
- worldbuilding;
- cultivation design;
- payoff design;
- Dao/insight architecture;
- emotional arc;
- progression structure;
- world-scale reveal strategy.

Không yêu cầu Writer viết giống một tác giả cụ thể; không copy wording, rhetorical frame, scene/plot beat hoặc syntax bản dịch/convert.

## 4. Roles

- Orchestrator: xác định stage, assemble context, điều phối transaction và verify commit.
- World Architect: tạo Story Bible **không dùng Reference Prose Profile**.
- Story Architect: tạo Master/Arc Outline **không dùng Reference Prose Profile**.
- Character Architect: tạo Character DNA **không dùng Reference Prose Profile**.
- Style Director: stage duy nhất được adapt Reference Prose Profile vào Style Bible.
- Story Promise Controller: khóa 3–5 promises và theo dõi payoff.
- Scene Planner: plan gọn; chỉ nhận tối đa 1–2 prose reminder từ Style Bible nếu cần.
- Writer: viết prose theo canon + Style Bible.
- Combined QC Reviewer: kiểm Continuity + Story Promise + Style trong một report.
- Memory Keeper: chuẩn bị memory/manifest updates trước atomic commit.

## 5. Source of truth

1. `memory/canon_ledger.md`
2. final chapters
3. `bible/*.md`
4. `memory/*.md`
5. arc outline
6. master outline
7. seed
8. draft/scene plan

Outline = plan. Final + canon ledger = chuyện đã xảy ra.

## 6. Read-before-write

Trước chapter mới đọc tối thiểu:

- manifest + seed;
- Story/Style/Characters Bible phần liên quan;
- Story Promises;
- arc hiện tại;
- current state + promise memory;
- ledgers cần thiết;
- 3 recent summaries;
- full final gần nhất khi continuity trực tiếp cần.

Writer dùng Style Bible làm direct style source. Không cần đọc reference profile mỗi chapter nếu Style Bible đã adapt đầy đủ.

## 7. Story Promise Controller

Genesis khóa 3–5 promises. Mỗi promise có stable ID, reader value, PAY definition, ADVANCE definition, false pay, drought warning và escalation path.

Per chapter dùng:

- `UNTOUCHED`
- `ADVANCE`
- `PAY_MINOR`
- `PAY_MAJOR`
- `PAY_ARC`

Theo dõi `last_pay_chapter`, `last_major_pay_chapter`, `pay_drought`, next planned payoff window. Không fake payoff chỉ để clear drought.

## 8. Scene plan

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

Reference-style reminder chỉ được là prose mechanics, không được là story-DNA instruction.

## 9. Draft

Writer ưu tiên truyện trước checklist. Prose Việt tự nhiên, POV nhất quán, dialogue theo DNA, worldbuilding qua tình huống, cultivation/craft/combat đủ rõ nhưng không thành manual/log.

Reference prose chỉ ảnh hưởng **cách câu/đoạn được viết**, không quyết định chuyện gì xảy ra.

## 10. Combined QC

Một reviewer đọc draft và ghi một `combined_qc_report.md`.

### Continuity
Kiểm canon, timeline, geography, cultivation/power, item/resource/injury, knowledge, relationship/faction, POV và hard DNA contradiction.

### Story Promise
Kiểm target có chạm thật không, ADVANCE/PAY classification, magnitude, false pay, drought.

### Style
Kiểm sentence/paragraph rhythm, clause flow, diction, narrator directness, internal-monologue density, dialogue, description, action/exposition prose, convert syntax, stock tics, Style Bible drift và imitation risk.

**Không chấm plot/Dao/emotional arc/world scale/progression theo reference.**

Severity: `BLOCKER / MAJOR / MINOR / NOTE`.

- còn BLOCKER/MAJOR cần sửa trong chapter → `REWRITE_REQUIRED`;
- chỉ MINOR/NOTE hoặc không finding → `PASS`.

## 11. Rewrite policy

Rewrite chỉ chạy khi Combined QC = REWRITE_REQUIRED.

Nếu draft PASS:

```text
draft → final
```

Nếu cần rewrite, sửa trong memory làm việc, không persist `rewrite.txt`. Sau sửa, Combined QC ghi `Rewrite Recheck` và final dùng candidate đã pass.

Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`.

## 12. Atomic Git chapter transaction

Không ghi GitHub từng artifact trong lúc đang xử lý chapter.

1. lấy branch HEAD + base tree;
2. assemble context;
3. tạo scene plan, draft, combined QC;
4. nếu cần, rewrite/recheck trong memory làm việc;
5. tạo final;
6. tính memory/ledger/summary/manifest updates;
7. nếu chapter cuối batch, tạo batch audit;
8. create_blob cho tất cả file mới/thay đổi;
9. `create_tree(base_tree=<chapter-start tree>)`;
10. `create_commit(parent=<chapter-start HEAD>)`;
11. `update_ref` branch đúng một lần;
12. verify HEAD + manifest/memory.

Chapter commit tối thiểu chứa:

- `chapters/NNNN/scene_plan.md`
- `chapters/NNNN/draft.txt`
- `chapters/NNNN/combined_qc_report.md`
- `final/Chương N: <title>.txt`
- memory/ledger/summary thay đổi
- manifest update
- batch audit nếu N là chapter cuối requested batch.

Nếu lỗi trước `update_ref`, chapter chưa hoàn tất.

## 13. Batch 5

Viết tuần tự 5 chapter; mỗi chapter = một atomic commit. Chapter N+1 chỉ bắt đầu sau khi commit N verify thành công.

Không có checkpoint Ch.3. Batch audit chỉ tạo sau chapter thứ 5 của requested range và nên nằm trong atomic commit của chapter đó.

## 14. Completion

Chapter COMPLETE khi atomic commit đã chứa scene plan, draft, combined QC PASS, final và memory/manifest current.

Batch COMPLETE khi đủ 5 requested finals/commits, memory current qua chapter cuối và batch audit tồn tại.
