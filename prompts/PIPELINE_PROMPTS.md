# Pipeline Prompts

Các prompt dưới đây là role contracts để ChatGPT tự thực thi stage. Luôn đọc `AGENTS.md`, `docs/READER_EXPERIENCE_SYSTEM.md`, `docs/RETENTION_CONTROLLERS_V3.md`, `docs/XIANXIA_DENSITY_CONTROLLER.md`, `docs/BATCH_5_WORKFLOW.md` và migration doc khi story là legacy.

Core rules:

**PASS kỹ thuật ≠ PASS trải nghiệm đọc.**

**PASS retention ≠ PASS genre density.**

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
9. Không báo PASS nếu Reader-Reward Gate còn MAJOR từ Retention Controllers v3.
10. Nếu manifest bật `xianxia_density_required`, không báo PASS nếu Xianxia Density Gate còn MAJOR.

## Legacy

Nếu story pre-v2/v3 hoặc batch_size cũ:

- không fake retroactive QC;
- dùng migration baseline khi user yêu cầu migrate;
- existing batch-10 audits vẫn hợp lệ historical;
- khi sync batch size mới, set `batch_size: 5` và bắt đầu 5-chapter batch từ `next_chapter`;
- v3 baseline có thể dựng từ recent finals + reader memory, không fake retroactive per-chapter report;
- **không tự bật Xianxia Density cho story cũ nếu user không yêu cầu**.

---

# P1 — Seed Validator & Creative Resolver

Validate premise, protagonist start, tone, world/cultivation constraints, content boundaries, target length và `user_must_decide`.

Creative blanks không bắt buộc user quyết định → tự resolve theo causal logic.

Output:

`stories/<slug>/seed/seed.yaml`

Default production cho **truyện mới v3** nếu user không override:

```yaml
batch_size: 5
require_qc: true
require_rewrite: true
retention_v3_required: true
xianxia_density_required: true
```

---

# P2 — Story Bible Architect

Build world bằng causal chain:

`natural law → scarce resource → institution/incentive → social behavior → conflict → story utility`

Mỗi realm phải có qualitative change, limitation, breakthrough requirement, failure mode, social/lifespan meaning và cross-realm logic.

World logic phải phục vụ truyện; không nhồi hệ thống chỉ để hoành tráng.

Phân biệt world scarcity với fantasy aspiration: một world có thể nghèo, nhưng vẫn phải có những thứ khiến reader muốn nhìn thấy/chiếm hữu/vươn tới.

Bắt buộc thiết kế các **Active Xianxia causal sources** để về sau conflict không chỉ là skin tu tiên. Ví dụ: linh mạch/linh triều, công pháp, thần thức, cảnh giới, injury, trận/phù/đan/khí, yêu thú, bí cảnh, thiên tượng, địa mạch, đạo ý, power hierarchy.

Mỗi source phải có khả năng tạo chuỗi:

`supernatural law/state → constraint/opportunity → decision → consequence`.

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

Style không được chống cliché đến mức triệt tiêu wonder/spectacle. Xianxia Density phải đến từ mechanism/consequence, không từ adjective spam.

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

Đặc biệt với MC competence cao, phải xác định domain có thể CLEAN_WIN và domain dễ `PARTIAL / WRONG_MODEL / DEPENDENT_ON_OTHER / COSTLY_WIN`.

Nếu MC từng ở cảnh giới cao/sống lâu, Character DNA nên xác định **high-realm aura/perspective**: loại scale memory, old-world knowledge, power meaning và vùng kiến thức có thể lỗi thời.

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

Bắt buộc khóa **Payoff Magnitude** cho từng promise:

- `PAY_MINOR`;
- `PAY_MAJOR`;
- `PAY_ARC`;
- max major payoff debt;
- major-pay windows.

Build thêm:

- saga map;
- protagonist transformation;
- competence-friction sources;
- antagonistic forces;
- cultivation progression;
- Xianxia Experience spine;
- **Xianxia Density spine**: Ambient/Active/Aspirational identity, causal sources, density risk map, first X2/X3 windows;
- Aspiration spine;
- Heat identity/long-range curve;
- reveals;
- relationship turns;
- ending direction;
- flex zones.

Không backload toàn bộ Strong Xianxia đến quá xa trong opening nếu premise là progression xianxia.

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
- Story Promise PAY windows + minimum magnitude;
- Narrative Engine distribution;
- **Dramatic Geometry map**;
- **Competence Friction plan**;
- **Aspiration beats**;
- **Heat Curve**;
- **Xianxia Density map**: X0–X3 targets, Active causal beats, Replaceability targets, rolling 3/5 pre-check;
- **Binge Test risk map**;
- Xianxia Experience targets;
- Emotional Residue plan;
- costly mistake opportunities;
- chapter intent table.

Do not force arc boundary to match batch size 5.

Do not make engine variety fake: engine labels may differ while pressure/decision/information/resolution geometry remains the same.

Không để nhiều chapter admin/economy/family liên tiếp mà supernatural law không đổi causal chain.

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
- Dramatic Geometry signature;
- Story Promise target `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`;
- intended competence outcome if MC uses competence;
- aspiration target if needed by rolling debt;
- `peak_heat` target;
- `xianxia_peak` target `X0/X1/X2/X3`;
- Replaceability target;
- Ambient/Active/Aspirational Xianxia target;
- POV + knowledge boundary;
- Xianxia Experience target if organic;
- Emotional movement if any;
- human irrationality/blind spot if relevant;
- intrinsic chapter reward before ending hook;
- ending shape.

Bắt buộc pre-check:

1. **Yếu tố nào khiến chapter này chỉ có thể tồn tại trong tu tiên giới?**
2. **Supernatural law/state nào tạo constraint/opportunity và consequence?**
3. **Nếu chapter X0/X1, rolling 3/5 có còn pass không?**

### Relaxed planning

Conflict/transaction scene may use goal/obstacle/stakes/turn/choice/consequence.

Quiet/discovery/emotional scene only needs focal tension/curiosity, sensory anchor, knowledge boundary và meaningful movement/residue.

Do not force every scene into the same mini-plot template.

Pre-check Binge Test:

1. Khoảnh khắc sướng nhất dự kiến là gì?
2. Bỏ ending hook, chapter có đủ giá trị nội tại không?

Nếu chưa có concrete reward và không có valid structural waiver, redesign trước draft.

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
- avoid packaged aphorisms and repetitive hypothesis loops;
- không biến aspiration/heat/payoff target thành exposition list;
- không cứu Binge Test chỉ bằng cliffhanger cuối;
- không fake Xianxia Density bằng cách rắc thêm “linh khí / pháp bảo / thiên địa / đạo vận”;
- Active Xianxia phải đi qua causal action/consequence;
- nếu POV từng ở high realm, thỉnh thoảng giữ scale perspective nhưng không biến thành lore flex.

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

Audit toàn bộ Retention Controllers v3 + Xianxia Density nếu manifest bật controller.

## Story Promise + Payoff Magnitude

- `UNTOUCHED / ADVANCE / PAY_MINOR / PAY_MAJOR / PAY_ARC`;
- reward score;
- pay drought;
- major payoff debt;
- false PAY;
- chuỗi PAY_MINOR đang che thiếu PAY_MAJOR hay không.

## Narrative Engine

- primary/secondary engine;
- rolling 3/4 same-engine risk.

## Dramatic Geometry Controller

Ghi pressure source, decision locus, movement mode, information flow, opposition shape, resolution mode, reversal type, kinetic level.

3 consecutive near-same → WATCH. 3/4 same core geometry → `MAJOR pacing risk` dù engine label khác.

## Competence Friction Meter

Phân loại competence conversion:

`CLEAN_WIN / COSTLY_WIN / PARTIAL / WRONG_MODEL / DEPENDENT_ON_OTHER / FAILURE / NO_CONVERSION`.

- 3 CLEAN_WIN liên tiếp → WATCH;
- 4/5 recent conversions CLEAN_WIN → `MAJOR flattening risk`.

## Aspiration Controller

Tách scarcity khỏi fantasy desire. Kiểm object_of_desire, why desirable, proof/image, gate/cost, future use, status.

Rolling 5 chỉ scarcity/admin/problem-fixing mà không aspiration/wonder đủ mạnh → `MAJOR appetite risk`.

## Heat Curve

Ghi `peak_heat`: H0 / H1 / H2 / H3.

Rolling 5 không có H2+ → `MAJOR flatness risk`.

## Xianxia Density Controller — BẮT BUỘC CHO STORY BẬT CONTROLLER

Ghi:

- Ambient Xianxia evidence;
- Active Xianxia causal beat(s);
- Aspirational Xianxia;
- `xianxia_peak X0/X1/X2/X3`;
- Replaceability `LOW/MEDIUM/HIGH`;
- previous 2/4 peaks;
- rolling 3 có X2+?;
- rolling 5 có `2×X2+ + 1×X3`?;
- 3 consecutive HIGH_REPLACEABILITY?;
- genre_density_debt.

Rules:

- rolling 3 không có X2+ → MAJOR trừ valid decompression waiver;
- rolling 5 thiếu 2 X2+ hoặc 1 X3 → MAJOR;
- 3 HIGH_REPLACEABILITY liên tiếp → MAJOR;
- terminology/infodump không clear finding.

## Binge Test — BẮT BUỘC

1. **Khoảnh khắc sướng nhất chương là gì?**
2. **Nếu bỏ ending hook, bản thân chương này có đủ đáng đọc không?** `YES / WEAK / NO`

- câu 1 = `NONE` → ít nhất MAJOR trừ decompression có emotional payoff rất rõ;
- câu 2 = `NO` → MAJOR + rewrite trừ explicit valid waiver;
- waiver không dùng hai chapter liên tiếp.

Audit thêm opening/movement/drag, conflict solution repetition, agency/human irrationality, costly mistake pattern, Xianxia Experience, Emotional Residue, ending/reason-to-continue.

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

Gate phải tách:

- **Technical Gate** — continuity, knowledge, style, artifacts;
- **Reader-Reward Gate** — payoff magnitude, geometry, competence friction, aspiration, heat, Binge Test, Xianxia/Emotional reward;
- **Xianxia Density Gate** — X0–X3, Active causality, Replaceability, rolling 3/5.

Technical Gate PASS không override Reader-Reward/Xianxia Density MAJOR.

Severity:

- BLOCKER — canon/logic/release contract broken;
- MAJOR — character/retention/payoff/engine/geometry/friction/aspiration/heat/binge/Xianxia-Density/style defect requiring rewrite;
- MINOR — useful correction;
- NOTE — tracking only.

---

# P10 — Rewrite Editor

Priority:

1. canon/knowledge/data;
2. Character DNA;
3. causality/power;
4. Story Promise + Payoff Magnitude;
5. Narrative Engine + Dramatic Geometry;
6. Xianxia Density / Replaceability;
7. Competence Friction;
8. Aspiration / Heat / Binge Test;
9. Xianxia/Emotional debt;
10. style fingerprint;
11. minor polish.

If repetition is structural, rewrite structure; do not synonym-spin.

Nếu lỗi là aspiration/heat/binge, không được chỉ thêm một câu hook cuối.

Nếu lỗi là Xianxia Density, phải sửa supernatural causality/constraint/consequence; không chữa bằng vocabulary.

Output:

`chapters/NNNN/rewrite.txt`

---

# P10.5 — Critical Re-QC

Recheck all BLOCKER/MAJOR and changed regions. Rerun affected reviewer report if rewrite materially changes its domain.

Recompute if affected:

- payoff magnitude;
- geometry;
- competence outcome;
- aspiration;
- peak heat;
- xianxia_peak;
- replaceability;
- genre_density_debt;
- Binge Test.

No final while BLOCKER/MAJOR remains.

---

# P10.6 — Rolling 3-Chapter Auditor

Trigger when `N % 3 == 0` globally: 3, 6, 9, 12, 15...

Read full:

- final N-2;
- final N-1;
- rewrite candidate N.

Audit:

- opening;
- engine;
- Dramatic Geometry;
- dialogue geometry;
- conflict solution;
- ending;
- rhetorical tics;
- Promise PAY magnitude;
- competence friction trend;
- aspiration trend;
- heat trend;
- Xianxia Density/Replaceability trend;
- Binge Test trend;
- Xianxia Experience;
- Emotional Residue;
- costly mistakes.

Heat official rule remains rolling 5. Xianxia Density has hard rolling 3 + rolling 5 rules.

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

- Story Promise `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`;
- pay drought + major payoff debt;
- last major payoff;
- last wonder beat;
- last emotional hit;
- last costly mistake;
- recent engines;
- Dramatic Geometry signatures;
- competence outcomes;
- aspiration beats;
- heat sequence / last H2+;
- xianxia_peak sequence / last X2+ / last X3;
- Ambient/Active/Aspirational summaries;
- replaceability sequence;
- genre_density_debt;
- high-realm aura last used if relevant;
- Binge Test results;
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
- Story Promise magnitude + pay/major-payoff debt;
- Narrative Engine distribution, including windows crossing batch boundary;
- Dramatic Geometry distribution;
- Competence Friction distribution;
- Aspiration coverage;
- rolling-5 Heat Curve;
- Xianxia Density peak sequence;
- Active X2+ / Strong X3 counts;
- Replaceability distribution;
- genre_density_debt;
- Binge Test health;
- Xianxia/Emotional experience;
- continuity;
- character agency/irrationality;
- cultivation/power/resource economy;
- style fingerprints;
- threads/setup/payoff;
- reader memory consistency;
- next-batch handoff.

Batch technical gate sạch nhưng retention/Xianxia-Density MAJOR còn tồn tại → `REPAIR_REQUIRED`, không PASS.

Batch ranges normally:

- 1–5
- 6–10
- 11–15
- 16–20

Existing batch-10 historical audits remain valid after migration.

---

# P14 — Completion Verifier

Before telling user a chapter/batch is complete, inspect artifact tree.

Native v3 chapter requires:

- scene_plan;
- draft;
- continuity_report;
- reader_retention_report with Retention Controllers v3 + Xianxia Density when enabled + Binge Test;
- style_fingerprint_report;
- quality_report with Technical Gate + Reader-Reward Gate + Xianxia Density Gate when enabled;
- rewrite when required;
- rolling audit when N%3==0;
- final;
- story memory + reader experience current through N.

Native default batch requires:

- requested 5 finals;
- memory current through last chapter;
- batch audit including geometry/magnitude/friction/aspiration/heat/density/binge sections;
- next-batch handoff.

Missing required artifact = `INCOMPLETE`, never PASS.

Reader-Reward/Xianxia-Density Gate MAJOR = `REPAIR_REQUIRED`, never PASS.