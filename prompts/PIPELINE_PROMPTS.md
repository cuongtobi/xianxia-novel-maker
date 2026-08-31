# Pipeline Prompts — Atomic Combined QC + Tiên Nghịch Style DNA

Controller duy nhất: **Story Promise Controller**.

Reference Style là high-level style architecture, không phải controller và không phải direct imitation prompt.

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

Nếu Reference Style bật, verify profile path và `high_level_style_dna_only` usage.

## P2 — Story Bible Architect

Build world bằng causal logic tự nhiên: `law → resource/limit → institution/behavior → conflict`. Khóa cultivation, factions, history, geography, crafts, economy, social order, hard rules và mystery foundations.

Không tạo world chỉ để fit reference. Story premise và Story Promise thắng reference.

## P3 — Style Bible Director

Khóa POV, rhythm, diction, dialogue, exposition, cultivation/combat prose, emotional handling, openings/endings, anti-AI fingerprints và calibration.

Nếu dùng default `TIEN_NGHICH_HIGH_LEVEL_STYLE.md`:

1. đọc profile;
2. chọn **3–6 high-level traits** phù hợp premise, không inherit toàn bộ;
3. ưu tiên cân nhắc:
   - mortal anchor before immortal scale;
   - accumulated pressure → decisive release;
   - cultivation as qualitative transformation;
   - lived experience → Dao/insight → consequence;
   - power gap constrains decisions;
   - restrained emotion → rupture → persistent scar;
   - layered world-scale reveal;
4. ghi rõ trait nào soften/omit;
5. ghi weakness filter: old-school pacing bloat, exposition/recap, spectator shock, repeated combat patterns, translation syntax, unsupported aphorism;
6. định nghĩa story-specific expression để prose không trở thành bản sao reference;
7. không dùng tên tác giả/tác phẩm như direct Writer instruction.

**Translation caveat:** không suy sentence-level Vietnamese style từ bản convert/dịch. Diction cuối cùng phải đến từ Style Bible + project-owned calibration.

## P4 — Character DNA Architect

Khóa desire, need, fear, wound, value, blind spot, contradiction, decision logic, speech, relationships, cultivation/combat identity, secrets và arc vector.

Reference không override Character DNA. Không biến protagonist thành lạnh lùng/ruthless chỉ vì Tiên Nghịch có tone đó.

## P5 — Master Outline + Story Promise Architect

Khóa 3–5 Story Promises. Mỗi promise có stable ID, reader value, PAY/ADVANCE definition, false pay, drought warning, escalation path và ví dụ magnitude nếu cần.

Build saga map, protagonist/antagonist progression, cultivation progression, reveals, relationships, ending direction và flex zones.

Có thể dùng nguyên lý reference ở mức dài hạn: progression nên đổi meaning/capability; world scale mở theo tầng; emotional/cultivation insight có thể được chuẩn bị từ trải nghiệm trước. Không clone arc.

## P6 — Arc Outline Architect

Build arc question, start/end state, conflict ladder, character/faction moves, cultivation/resources, reveals, setup/payoff, Story Promise PAY windows, chapter intents và flex points.

Nếu arc có Dao/insight lớn, phải có **lived material** chuẩn bị trước thay vì đột nhiên triết lý ở chapter payoff.

Nếu arc có world-scale reveal, reveal phải revalue current stakes/knowledge, không chỉ mở map lớn hơn.

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

Reference-style planning chỉ thêm tối đa **1–2 relevant style reminders**, ví dụ:

- giữ expert reasoning compressed;
- dùng ordinary-life anchor;
- power gap phải đổi quyết định;
- insight cần concrete lived support;
- world reveal phải revalue stakes.

Không biến scene plan thành checklist Tiên Nghịch.

Output content destined for `chapters/NNNN/scene_plan.md`, nhưng chưa persist.

## P8 — Vietnamese Xianxia Writer

Viết complete draft theo plan/bibles/memory.

Direct style contract = story `bible/style_bible.md`.

Không tự nhủ `viết giống Nhĩ Căn/Tiên Nghịch`; không copy wording, rhetorical frame, scene shape hay translation syntax.

Core writing rules:

- bắt đầu từ concrete event/person/problem thay vì abstract lore khi hợp cảnh;
- prose Việt tự nhiên, POV nhất quán;
- câu trung bình làm trục, câu ngắn tiết chế;
- dialogue theo Character DNA và power/status relation;
- experienced MC reason nhanh: chỉ viết phần suy luận ảnh hưởng lựa chọn;
- cultivation/craft cho đủ mechanism để decision/result believable, không thành manual;
- major progression nên tạo qualitative change về capability/perception/status/choice;
- power gap phải giới hạn hành vi thật;
- combat ưu tiên objective → judgment → resource/action → consequence, không skill-log;
- nếu có Dao/insight, đi từ lived scene/concrete image lên abstraction rồi quay lại consequence;
- emotion ưu tiên concrete attachment, action/body/silence và lasting consequence hơn narrator labeling;
- ordinary/mortal detail có thể tạo chiều sâu cho cultivation khi organic;
- world-scale reveal phải làm reader hiểu lại điều cũ, không chỉ thêm tên lớn hơn;
- wonder cần concrete proof trước adjective spam;
- không bê pacing chậm, exposition bloat, repeated spectator shock hoặc artificial cliffhanger từ old-school serialization.

Output content destined for `chapters/NNNN/draft.txt`, nhưng chưa persist.

## P9 — Combined QC Reviewer

Đọc draft và tạo **một report** với ba phần.

### A. Continuity

Kiểm canon, timeline/geography, power/cultivation, items/resources/injury, knowledge, relationship/faction, POV, hard DNA contradiction.

### B. Story Promise

Kiểm promise target, `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`, concrete payoff, false pay, magnitude, drought.

### C. Style

Kiểm AI-like fingerprints, cadence/fragments, Q&A cleanliness, hypothesis-loop, aphorism/recap/exposition, lexical tics, dialogue sameness và Style Bible/reference drift.

Nếu story dùng Tiên Nghịch profile, chỉ kiểm **relevant traits đã chọn trong Style Bible**, không đòi chapter phải có tất cả. Câu hỏi diagnostic:

- prose có grounded trong concrete event/choice hay trôi thành generic xianxia abstraction?;
- expert reasoning có bị log quá kỹ không?;
- cultivation có chỉ tăng số hay thực sự đổi capability/perception/choice khi đó là payoff chính?;
- power gap có ảnh hưởng quyết định không?;
- Dao/philosophy có lived-scene support không?;
- emotional peak có attachment/consequence cụ thể không?;
- world-scale reveal có revalue stakes không?;
- có translation-like syntax, excessive fragments, stock gestures, spectator shock hoặc adjective spam không?;
- có dấu hiệu imitation wording/rhetorical/scene pattern từ reference không?.

Severity: `BLOCKER / MAJOR / MINOR / NOTE`.

Decision:

- `PASS` nếu không có BLOCKER/MAJOR cần sửa trong chapter;
- `REWRITE_REQUIRED` nếu có.

Output destined for `chapters/NNNN/combined_qc_report.md`, chưa persist.

## P10 — Rewrite + Quick Recheck

Chỉ chạy khi P9 = `REWRITE_REQUIRED`.

Sửa candidate trong working memory. Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`. Không tạo `rewrite.txt`.

Không "sửa theo reference" bằng cách thêm triết lý, bi kịch, fragment hay thuật ngữ. Chỉ sửa finding cụ thể theo story Style Bible.

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

Reference Style batch note chỉ ghi **pattern drift đáng chú ý**, không tạo thêm controller/quota.

Không có rolling audit/checkpoint Ch.3.
