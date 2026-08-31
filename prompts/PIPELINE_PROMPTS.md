# Pipeline Prompts — Atomic Combined QC

Controller duy nhất: **Story Promise Controller**.

## P0 — Orchestrator

1. Xác định exact repo/branch/slug.
2. Đọc manifest/source of truth.
3. Resolve requested range; `batch tiếp theo` mặc định = 5 chapters.
4. Với từng chapter, giữ toàn bộ intermediate work trong session memory.
5. Chỉ persist khi scene plan + draft + combined QC + final + memory/manifest đều sẵn sàng.
6. Persist chapter bằng one tree/commit + one branch ref update.
7. Không sang chapter mới trước khi commit chapter hiện tại verify thành công.
8. Không tạo retired QC artifacts/controllers.

## P1 — Seed Validator

Validate premise, protagonist, world/cultivation intent, tone, boundaries, target length và user decisions. Creative blanks không cần user duyệt → tự resolve hợp lý.

## P2 — Story Bible Architect

Build world bằng causal logic tự nhiên: `law → resource/limit → institution/behavior → conflict`. Khóa cultivation, factions, history, geography, crafts, economy, social order, hard rules và mystery foundations.

## P3 — Style Bible Director

Khóa POV, rhythm, diction, dialogue, exposition, cultivation/combat prose, emotional handling, openings/endings, anti-AI fingerprints và calibration. Reference Style nếu bật chỉ dùng high-level traits qua Style Bible.

## P4 — Character DNA Architect

Khóa desire, need, fear, wound, value, blind spot, contradiction, decision logic, speech, relationships, cultivation/combat identity, secrets và arc vector.

## P5 — Master Outline + Story Promise Architect

Khóa 3–5 Story Promises. Mỗi promise có stable ID, reader value, PAY/ADVANCE definition, false pay, drought warning, escalation path và ví dụ magnitude nếu cần.

Build saga map, protagonist/antagonist progression, cultivation progression, reveals, relationships, ending direction và flex zones.

## P6 — Arc Outline Architect

Build arc question, start/end state, conflict ladder, character/faction moves, cultivation/resources, reveals, setup/payoff, Story Promise PAY windows, chapter intents và flex points.

## P7 — Chapter Scene Planner

Plan gọn:

- chapter objective;
- POV/time/place/cast;
- start state;
- conflict/pressure;
- key beats/turn;
- choice/consequence nếu có;
- Story Promise target;
- concrete payoff nếu target = PAY;
- end state;
- continuity/style constraints;
- hook nếu organic.

Output content destined for `chapters/NNNN/scene_plan.md`, nhưng chưa persist.

## P8 — Vietnamese Xianxia Writer

Viết complete draft theo plan/bibles/memory. Prose Việt tự nhiên, POV nhất quán, dialogue theo DNA, worldbuilding qua tình huống, cultivation/craft/combat rõ nhưng không thành manual/log. Không viết cho retired metrics.

Output content destined for `chapters/NNNN/draft.txt`, nhưng chưa persist.

## P9 — Combined QC Reviewer

Đọc draft và tạo **một report** với ba phần.

### A. Continuity
Kiểm canon, timeline/geography, power/cultivation, items/resources/injury, knowledge, relationship/faction, POV, hard DNA contradiction.

### B. Story Promise
Kiểm promise target, `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`, concrete payoff, false pay, magnitude, drought.

### C. Style
Kiểm AI-like fingerprints, cadence/fragments, Q&A cleanliness, hypothesis-loop, aphorism/recap/exposition, lexical tics, dialogue sameness, Style Bible/reference drift.

Severity: `BLOCKER / MAJOR / MINOR / NOTE`.

Decision:

- `PASS` nếu không có BLOCKER/MAJOR cần sửa trong chapter;
- `REWRITE_REQUIRED` nếu có.

Output destined for `chapters/NNNN/combined_qc_report.md`, chưa persist.

## P10 — Rewrite + Quick Recheck

Chỉ chạy khi P9 = `REWRITE_REQUIRED`.

Sửa candidate trong working memory. Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`. Không tạo `rewrite.txt`.

Recheck đúng các finding fail; append `Rewrite Recheck` vào cùng Combined QC report. Chỉ khi pass mới cho phép final.

Nếu P9 = PASS, bỏ qua hoàn toàn P10 và dùng draft nguyên văn làm final.

## P11 — Final + Memory Builder

Chuẩn bị:

- final TXT;
- current state/ledgers affected;
- chapter summary;
- promise memory;
- manifest `last_finalized_chapter`, `next_chapter`, batch pointers;
- batch audit nếu chapter đóng requested batch.

Chưa write GitHub.

## P12 — Atomic Git Committer

Input: chapter-start HEAD/tree + toàn bộ prepared contents.

1. create_blob cho mọi new/changed file;
2. create_tree từ chapter-start base tree;
3. create_commit với chapter-start HEAD làm parent;
4. update_ref exact story branch đúng một lần;
5. verify branch HEAD.

Chapter commit tối thiểu chứa scene plan, draft, combined QC, final, changed memory và manifest. Chapter cuối batch thêm batch audit.

Nếu fail trước update_ref: transaction chưa complete; không tiến `next_chapter` bằng lời nói.

## P13 — Batch Auditor

Chỉ ở chapter cuối requested batch. Audit 5 chapter commits/finals, Combined QC PASS, memory current, continuity handoff, Story Promise payoff/drought, style caution và next-batch handoff.

Không có rolling audit/checkpoint Ch.3.
