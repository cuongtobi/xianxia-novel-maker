# Pipeline Prompts — Promise-Only

Các role contract dưới đây dùng cho framework v3.1. Đọc `AGENTS.md`, `docs/BATCH_5_WORKFLOW.md`, `docs/READER_EXPERIENCE_SYSTEM.md` và `docs/REFERENCE_STYLE_SYSTEM.md` khi story bật Reference Style.

**Controller duy nhất: Story Promise Controller.**

---

# P0 — Orchestrator

1. Xác định repo + exact branch + slug.
2. Đọc manifest/source of truth.
3. Xác định stage thật từ artifact.
4. `batch tiếp theo` mặc định = 5 chương.
5. Chạy tuần tự từng chapter transaction.
6. Không sang chapter mới trước memory update.
7. Không báo COMPLETE nếu thiếu artifact.
8. Không gọi hoặc tái tạo controller đã retire.

---

# P1 — Seed Validator

Validate premise, protagonist, world/cultivation intent, tone, boundaries, target length và user decisions. Creative blanks không cần user duyệt → tự resolve hợp lý.

Nếu Reference Style bật, verify profile path và high-level-only usage.

Output: `seed/seed.yaml`.

---

# P2 — Story Bible Architect

Build world bằng causal logic tự nhiên:

`law → resource/limit → institution/behavior → conflict`.

Khóa cultivation realms, resources, factions, history, geography, crafts, economy, social order, hard rules và mystery foundations.

Không dùng Xianxia Density score/quota. Chất tiên hiệp phải đến từ bản thân world design, không từ metric.

Output: `bible/story_bible.md`.

---

# P3 — Style Bible Director

Khóa POV, rhythm, diction, dialogue, exposition, cultivation/combat prose, emotional handling, opening/ending preferences, anti-AI fingerprints và calibration policy.

Nếu Reference Style bật:

- adapt high-level traits vào house style;
- không copy câu chữ/rhetorical frame/plot beat;
- story Style Bible là direct writing contract;
- project-owned samples chỉ dùng sau khi đủ chất lượng và đa dạng scene type.

Output: `bible/style_bible.md`.

---

# P4 — Character DNA Architect

Mỗi nhân vật quan trọng cần desire, need, fear, wound, value, blind spot, contradiction, decision logic, speech fingerprint, relationship behavior, cultivation/combat identity, secrets và arc vector.

Nhân vật có thể sai hoặc cảm tính nếu hợp DNA; không có quota thất bại/competence friction.

Output: `bible/characters_bible.md`.

---

# P5 — Master Outline + Story Promise Architect

Thiết kế đường dài nhưng không vi mô hóa hàng trăm chapter.

Khóa **3–5 Story Promises**. Mỗi promise có:

- stable ID;
- promise;
- reader value;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path;
- examples của PAY_MINOR/PAY_MAJOR/PAY_ARC nếu hữu ích.

Build saga map, protagonist transformation, antagonist progression, cultivation progression, major reveals, relationships, ending direction và flex zones.

Không build controller spine khác.

Output: `outline/master_outline.md`.

---

# P6 — Arc Outline Architect

Build arc question, start/end state, conflict ladder, character/faction moves, cultivation/resources, reveals, setup/payoff, Story Promise PAY windows, chapter intent và flex points.

Không lập Narrative Engine distribution, Geometry map, Competence plan, Heat curve, Xianxia Density map, Aspiration/Binge/Emotional quota.

Output: `outline/arcs/arc_NNN.md`.

---

# P7 — Chapter Scene Planner

Read current state, promise memory, arc beat, Story Promises, Style Bible, relevant DNA/ledgers và recent final khi cần.

Plan gọn:

- chapter objective;
- POV/time/place/cast;
- start state;
- conflict/pressure;
- key beats/turn;
- choice/consequence nếu có;
- Story Promise target: UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC;
- concrete payoff nếu target = PAY;
- end state;
- continuity constraints;
- style constraints;
- ending hook nếu organic.

Không pre-score Engine/Geometry/Heat/Density/Competence/Aspiration/Binge.

Output: `chapters/NNNN/scene_plan.md`.

---

# P8 — Vietnamese Xianxia Writer

Viết chapter hoàn chỉnh theo plan/bibles/memory nhưng **không viết như checklist**.

Rules:

- POV consistent;
- character desire/action có lực;
- worldbuilding qua tình huống;
- dialogue có DNA và subtext;
- prose Việt tự nhiên;
- câu trung bình làm trục, câu ngắn tiết chế;
- cultivation/craft/combat đủ rõ nhưng không thành manual/log;
- không giải thích mọi suy luận;
- không thêm micro-mechanism để chứng minh genre;
- không cố tạo failure/cost chỉ vì metric;
- core fantasy competence được phép thắng sạch nếu hợp premise;
- Reference Style chỉ qua Style Bible, không copy source.

Output: `chapters/NNNN/draft.txt`.

---

# P9 — Continuity Auditor

Kiểm draft/rewrite với final + canon + ledgers:

- facts/timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction;
- POV;
- hard Character DNA contradiction.

Output: `continuity_report.md`.

---

# P10 — Story Promise Reviewer

Đây là reviewer của controller duy nhất.

Với mỗi promise:

1. chapter có touch thật không?;
2. classification UNTOUCHED/ADVANCE/PAY_* có đúng không?;
3. PAY có concrete result/reveal/state change không?;
4. magnitude có bị phóng đại không?;
5. có false pay không?;
6. drought sau chapter là bao nhiêu?;
7. nếu vượt warning, nên sửa current chapter hay future plan?

Không chấm retention controller khác.

Output giữ filename compatibility: `reader_retention_report.md`.

---

# P11 — Style Fingerprint Auditor

Kiểm:

- repeated rhetorical frames;
- fragment/cadence abuse;
- Q&A quá sạch;
- hypothesis-loop lặp;
- aphorism/recap/exposition;
- lexical tics;
- dialogue sameness;
- house style drift;
- Reference Style drift/overfit nếu bật.

Không dùng Narrative Engine quota để chấm style.

Output: `style_fingerprint_report.md`.

---

# P12 — Aggregate + Rewrite

Aggregate ba reviewer: continuity, Story Promise, style.

Không có Reader-Reward/Xianxia Density/Heat/Binge/Engine gate.

Rewrite chỉ sửa findings cụ thể. Ưu tiên:

`CUT > COMPRESS > REORDER > REPLACE > ADD`.

Mặc định final:draft <= khoảng 1.25. Structural fail → re-plan/re-draft thay vì patch-expansion.

Output: `quality_report.md`, `rewrite.txt` khi cần.

---

# P13 — Final + Memory Keeper

Sau PASS:

1. tạo final TXT;
2. update current state + ledgers + summary;
3. update `reader_experience.md` chỉ với Promise runtime state;
4. update manifest;
5. verify transaction complete.

---

# P14 — Batch Auditor

Sau default 5 chương, kiểm:

- artifact completeness;
- memory current;
- continuity handoff;
- Story Promise PAY/drought/magnitude;
- style findings đáng lưu ý;
- next-batch story/promise priorities.

Không chạy retired controllers.
