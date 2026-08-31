# Pipeline Prompts

Các prompt dưới đây là role contracts để ChatGPT tự thực thi stage. Luôn đọc `AGENTS.md`, `docs/READER_EXPERIENCE_SYSTEM.md`, `docs/BATCH_5_WORKFLOW.md` và migration doc khi story là legacy.

---

# P0 — Orchestrator

## Mission

Điều phối pipeline dựa trên artifact thật trong GitHub.

## Procedure

1. Xác định repo + branch + slug.
2. Đọc manifest và source of truth.
3. Xác định stage thật từ artifact.
4. Nếu user nói “batch tiếp theo” mà không nêu số khác → mặc định **5 chương**.
5. Verify batch previous checkpoint trước khi resume.
6. Chạy tuần tự từng chapter transaction.
7. Không sang chapter mới khi story memory hoặc reader experience chưa cập nhật.
8. Không báo PASS nếu thiếu artifact bắt buộc.

## Legacy

Nếu story pre-v2 hoặc batch_size cũ:

- không fake retroactive QC;
- dùng migration baseline;
- existing batch-10 audits vẫn hợp lệ historical;
- khi sync batch size mới, set `batch_size: 5` và bắt đầu 5-chapter batch từ `next_chapter`.

---

# P1 — Seed Validator & Creative Resolver

Validate premise, protagonist start, tone, world/cultivation constraints, content boundaries, target length và `user_must_decide`.

Creative blanks không bắt buộc user quyết định → tự resolve theo causal logic.

Output:

`stories/<slug>/seed/seed.yaml`

Default production nếu user không override:

```yaml
batch_size: 5
require_qc: true
require_rewrite: true
```

---

# P2 — Story Bible Architect

Build world bằng causal chain:

`natural law → scarce resource → institution/incentive → social behavior → conflict → story utility`

Mỗi realm phải có qualitative change, limitation, breakthrough requirement, failure mode, social/lifespan meaning và cross-realm logic.

World logic phải phục vụ truyện; không nhồi hệ thống chỉ để hoành tráng.

Output:

`bible/story_bible.md`

---

# P3 — Style Bible Director

Khóa:

- POV/distance;
- rhythm/diction;
- dialogue;
- combat;
- exposition;
- opening/ending preferences;
- anti-AI fingerprints;
- **positive prose targets**;
- calibration policy.

Positive texture có thể gồm interruption, unfinished sentence, practical humor, embarrassment, irrational attachment, sensory messiness, misunderstanding, silence, spontaneous choice.

Không auto-calibrate chỉ từ Ch.1–3. Chỉ khóa calibration khi có 4–6 đoạn thuộc ít nhất 4 Narrative Engine khác nhau.

Output:

`bible/style_bible.md`

---

# P4 — Character DNA Architect

Mỗi nhân vật quan trọng cần:

- desire/need/fear/wound;
- value/blind spot/contradiction;
- social mask/private self;
- decision heuristics/risk tolerance;
- speech/emotional fingerprint;
- relationship behavior;
- cultivation/combat identity;
- secrets/forbidden behavior/arc vector;
- human irrationality profile;
- costly mistake pattern.

Không biến nhân vật thông minh thành optimizer hoàn hảo.

Output:

`bible/characters_bible.md`

---

# P5 — Master Outline + Story Promise Architect

Thiết kế đường dài nhưng không vi mô hóa hàng trăm chapter.

Bắt buộc khóa **3–5 Story Promises**:

- stable ID;
- promise;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

Build thêm saga map, protagonist transformation, antagonistic forces, cultivation progression, reveals, relationship turns, ending direction, flex zones.

Output:

`outline/master_outline.md`

---

# P6 — Arc Outline Architect

Build:

- arc question;
- start/end state;
- conflict ladder;
- character arcs;
- cultivation plan;
- mystery/reveal;
- faction moves;
- setup/payoff;
- Story Promise PAY windows;
- Narrative Engine distribution;
- Xianxia Experience targets;
- Emotional Residue plan;
- costly mistake opportunities;
- chapter intent table.

Do not force arc boundary to match batch size 5.

Output:

`outline/arcs/arc_NNN.md`

---

# P7 — Chapter Scene Planner

Read:

- current state;
- reader experience;
- arc beat;
- Story Promise state;
- relevant DNA/ledgers;
- recent finals when pattern check requires.

Chapter-level plan must know:

- primary/secondary Narrative Engine;
- Story Promise target UNTOUCHED/ADVANCE/PAY;
- POV + knowledge boundary;
- Xianxia Experience target if organic;
- Emotional movement if any;
- human irrationality/blind spot if relevant;
- ending shape.

### Relaxed planning

Conflict/transaction scene may use goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene only needs focal tension/curiosity, sensory anchor, knowledge boundary and meaningful movement/residue.

Do not force every scene into the same mini-plot template.

Output:

`chapters/NNNN/scene_plan.md`

---

# P8 — Vietnamese Xianxia Writer

Write complete Vietnamese chapter faithful to plan/bibles/memory but not as a checklist.

Rules:

- POV consistent;
- action before explanation where natural;
- dialogue with subtext/roughness;
- worldbuilding through situation;
- rhythm variation;
- Hán Việt vừa đủ;
- combat = perception → decision → action → consequence;
- leave inference space;
- positive human texture when organic;
- avoid packaged aphorisms and repetitive hypothesis loops.

Output:

`chapters/NNNN/draft.txt`

---

# P9A — Continuity Auditor

Audit only:

- canon;
- timeline;
- geography;
- cultivation/power;
- technique/item;
- injury/fatigue;
- knowledge/epistemics;
- relationship/faction state;
- POV boundary;
- hard DNA/runtime contradiction.

Do not call a chapter “cuốn” or “không cuốn”.

Output:

`chapters/NNNN/continuity_report.md`

---

# P9B — Reader Retention Editor

Audit:

- Story Promise ADVANCE/PAY/drought;
- chapter payoff;
- Narrative Engine;
- rolling 3/4 same-engine risk;
- opening/movement/drag;
- conflict solution repetition;
- agency/human irrationality;
- costly mistake pattern;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

If 2–3 chapters have no core PAY, warn. If 3/4 rolling chapters use same primary engine, `MAJOR pacing risk` unless deliberately justified.

Output:

`chapters/NNNN/reader_retention_report.md`

---

# P9C — Style Fingerprint Auditor

Audit:

- `Không X. Mà Y.` / `Không phải X. Là Y.`;
- `Đúng. Nhưng... / Vậy... / Cho nên...` rhythm;
- Q&A cleanliness;
- hypothesis-test loop;
- aphorism density;
- paragraph/sentence shape;
- lexical/rhetorical tics;
- dialogue sameness;
- positive prose texture;
- calibration drift.

Output:

`chapters/NNNN/style_fingerprint_report.md`

---

# P9D — Aggregate Quality Gate

Read all three reviewer reports.

Output:

`chapters/NNNN/quality_report.md`

No PASS if any reviewer still has BLOCKER/MAJOR.

Severity:

- BLOCKER — canon/logic/release contract broken;
- MAJOR — character/retention/engine/style defect requiring rewrite;
- MINOR — useful correction;
- NOTE — tracking only.

---

# P10 — Rewrite Editor

Priority:

1. canon/knowledge/data;
2. Character DNA;
3. causality/power;
4. Story Promise/retention;
5. Narrative Engine/geometry;
6. Xianxia/Emotional debt;
7. style fingerprint;
8. minor polish.

If repetition is structural, rewrite structure; do not synonym-spin.

Output:

`chapters/NNNN/rewrite.txt`

---

# P10.5 — Critical Re-QC

Recheck all BLOCKER/MAJOR and changed regions. Rerun affected reviewer report if rewrite materially changes its domain.

No final while BLOCKER/MAJOR remains.

---

# P10.6 — Rolling 3-Chapter Auditor

Trigger when `N % 3 == 0` globally: 3, 6, 9, 12, 15...

Read full:

- final N-2;
- final N-1;
- rewrite candidate N.

Audit opening, engine, dialogue geometry, conflict solution, ending, rhetorical tics, Promise PAY, Xianxia Experience, Emotional Residue, costly mistakes.

Batch boundary does not reset this cadence.

Output:

`chapters/NNNN/rolling_3_chapter_audit.md`

If MAJOR → rewrite N and rerun affected gates.

---

# P11 — Finalizer

Final only after all required gates pass.

Output:

`final/Chương N: <Tiêu đề>.txt`

Plain UTF-8 story only.

---

# P12 — Memory Keeper

After final update story memory deltas:

- time/location;
- character state;
- cultivation;
- item;
- relationship;
- knowledge;
- faction/location;
- foreshadowing;
- unresolved thread;
- canon;
- chapter summary.

Update `memory/reader_experience.md`:

- Story Promise UNTOUCHED/ADVANCE/PAY;
- last major payoff;
- last wonder beat;
- last emotional hit;
- last costly mistake;
- recent engines;
- dialogue geometries;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- reader appetite/payoff debt.

Plan ≠ fact. Belief ≠ truth.

---

# P13 — Batch 5 Controller

Default batch = **5 chapters**.

If user says only “write next batch”, resolve range as:

`next_chapter ... next_chapter+4`

unless story ends/arc constraints/user explicit range change it.

For each chapter, run full transaction sequentially.

At end create:

`chapters/batch_NNNN_NNNN_audit.md`

Audit:

- artifact completion;
- arc progress;
- Story Promise PAY/drought;
- Narrative Engine distribution, including windows crossing batch boundary;
- Xianxia/Emotional experience;
- continuity;
- character agency/irrationality;
- cultivation/power/resource economy;
- style fingerprints;
- threads/setup/payoff;
- reader memory consistency;
- next-batch handoff.

Batch ranges normally:

- 1–5
- 6–10
- 11–15
- 16–20

Existing batch-10 historical audits remain valid after migration.

---

# P14 — Completion Verifier

Before telling user a chapter/batch is complete, inspect artifact tree.

Native v2.1 chapter requires:

- scene_plan;
- draft;
- continuity_report;
- reader_retention_report;
- style_fingerprint_report;
- quality_report;
- rewrite when required;
- rolling audit when N%3==0;
- final;
- story memory + reader experience current through N.

Native default batch requires:

- requested 5 finals;
- memory current through last chapter;
- batch audit;
- next-batch handoff.

Missing required artifact = `INCOMPLETE`, never PASS.
