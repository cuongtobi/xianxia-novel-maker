# AGENTS.md — Operating Contract

Tài liệu này là luật vận hành bắt buộc cho mọi phiên ChatGPT làm việc với repository này.

## 1. Vai trò

ChatGPT phải tách rõ các vai trò dù cùng một model thực hiện:

- **Orchestrator** — xác định stage, đọc đúng source of truth, điều phối workflow, verify artifact gate.
- **World Architect** — world/cultivation có nhân quả, tài nguyên, giới hạn và hậu quả xã hội.
- **Story Architect** — master outline, arc, progression dài hạn.
- **Story Promise Controller** — khóa 3–5 reader promises, theo dõi ADVANCE/PAY magnitude/drought.
- **Xianxia Experience Controller** — cultivation payoff, wonder, danger, power gap, mystical discovery, desirable resource, threshold crossing.
- **Xianxia Density Controller** — kiểm Ambient/Active/Aspirational Xianxia, X0–X3, replaceability và rolling genre-density để truyện không chỉ có “skin tu tiên”.
- **Dramatic Geometry Controller** — bắt chapter khác engine label nhưng cùng conflict/decision/resolution geometry.
- **Competence Friction Controller** — theo dõi CLEAN_WIN streak, partial/wrong-model/cost/dependence để MC không frictionless.
- **Aspiration + Heat Controller** — tách fantasy desire khỏi scarcity và kiểm rolling heat curve.
- **Character Director** — Character DNA, agency, human irrationality, costly mistakes.
- **Scene Planner** — đủ constraint nhưng không over-plan prose.
- **Writer** — prose tiếng Việt tự nhiên.
- **Continuity Auditor** — canon/state/knowledge/power/POV.
- **Reader Retention Editor** — promise magnitude, Narrative Engine, Dramatic Geometry, competence friction, aspiration, heat, Binge Test, Xianxia Density, pacing/drag, agency, Xianxia Experience, Emotional Residue.
- **Style Fingerprint Auditor** — rhetorical tic, Q&A cleanliness, hypothesis-loop, aphorism density, cadence/calibration drift.
- **Rewriter** — sửa theo QC, không retcon tùy tiện.
- **Memory Keeper** — update story memory + Reader Experience Memory sau mỗi final.

Không bỏ reviewer, rolling audit hoặc memory để tăng tốc.

Đọc thêm:

- `docs/READER_EXPERIENCE_SYSTEM.md`
- `docs/RETENTION_CONTROLLERS_V3.md`
- `docs/XIANXIA_DENSITY_CONTROLLER.md`
- `docs/BATCH_5_WORKFLOW.md`

## 2. Source of truth

Khi canon/state xung đột, ưu tiên:

1. `memory/canon_ledger.md`
2. final chapters
3. `bible/*.md`
4. `memory/*.md`
5. `outline/arcs/*.md`
6. `outline/master_outline.md`
7. seed
8. draft/scene plan

Outline là kế hoạch. Final + canon ledger là chuyện đã xảy ra.

`memory/reader_experience.md` là source of truth cho production pattern gần đây: promise PAY magnitude, Narrative Engine, Dramatic Geometry, competence outcomes, aspiration beats, heat, Xianxia Density peaks/replaceability, Binge Test, ending shape, rhetorical tic, Xianxia/Emotional debt. Nó không override canon hoặc Character DNA.

## 3. Branch contract

- Framework sống trên `main`.
- Mỗi truyện sống trên `story/<slug>`.
- Không viết hai truyện trên cùng branch.
- Không ghi story artifact lên `main`.
- Framework change trên `main` không tự động áp vào story branch cũ nếu chưa sync/migrate.

### Legacy migration

Story cũ thiếu Reader Experience / 3-mode QC dùng `docs/FRAMEWORK_V2_MIGRATION.md`.

Không fake retroactive per-chapter QC. Có thể dựng migration baseline từ final thật.

Batch audit lịch sử 10 chương vẫn hợp lệ. Khi story sync batch size 5, không cần chia audit 1–10 cũ thành 1–5 và 6–10.

**Xianxia Density Controller chỉ áp mặc định cho truyện mới dùng framework v3. Không tự sửa/migrate story branch cũ nếu user không yêu cầu.**

## 4. Read-before-write

Trước một chapter, đọc tối thiểu:

- seed;
- story/style bible;
- Character DNA nhân vật xuất hiện;
- Story Promises + master outline phần liên quan;
- arc hiện tại;
- `memory/current_state.md`;
- `memory/reader_experience.md`;
- canon/character/cultivation/knowledge/foreshadowing/unresolved ledgers liên quan;
- ít nhất 3 recent summaries;
- full final gần nhất khi continuity trực tiếp.

Reader Retention / Style / Rolling Audit phải đọc full 2–3 recent finals khi kiểm repetition; không chỉ dựa summary.

Nếu story legacy chưa migrate và framework hiện hành yêu cầu reader memory, migrate trước hoặc làm theo explicit user directive về version.

## 5. World + Xianxia contract

Worldbuilding phải trả lời:

- luật tự nhiên nào tạo tài nguyên/khan hiếm;
- ai kiểm soát/khai thác;
- institution/incentive nào xuất hiện;
- đời sống người thường và tu sĩ thay đổi ra sao;
- conflict nào tự nhiên sinh ra;
- giới hạn/cost/ngoại lệ là gì.

Mỗi realm phải có qualitative change, limitation, breakthrough requirement, failure mode, social meaning và cross-realm logic.

**World logic không thay thế Xianxia Experience.** Theo dõi riêng:

- cultivation payoff;
- wonder/awe;
- supernatural danger;
- power gap;
- mystical discovery;
- desirable resource;
- threshold crossing;
- dao/cultivation insight có consequence;
- magical craft;
- world-scale glimpse.

### Xianxia Density rule

Xianxia Experience có thể tồn tại như một beat riêng lẻ, nhưng **Xianxia Density** kiểm việc luật tu tiên có thật sự đi vào causal chain của truyện hay không.

Mỗi chapter của truyện mới v3 phải ghi:

- Ambient Xianxia;
- Active Xianxia causal beat(s);
- Aspirational Xianxia;
- `xianxia_peak: X0/X1/X2/X3`;
- Replaceability: LOW / MEDIUM / HIGH.

Core rolling rules:

- rolling 3 phải có ít nhất 1 chapter `X2+`;
- 3 consecutive `HIGH_REPLACEABILITY` → **MAJOR genre dilution risk**;
- rolling 5 phải có ít nhất 2 chapter `X2+` + ít nhất 1 chapter `X3`;
- rolling 5 phải có aspiration/wonder desire đủ rõ;
- không clear finding bằng cách rắc thêm “linh khí / pháp bảo / đạo vận”. Phải sửa causal structure.

Chi tiết: `docs/XIANXIA_DENSITY_CONTROLLER.md`.

## 6. Story Promise contract

Genesis khóa **3–5 Story Promises** trong master outline.

Mỗi promise có:

- stable ID;
- reader promise;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

Rules:

- setup ≠ PAY;
- nói về tu luyện ≠ cultivation payoff nếu không có thay đổi hữu hình;
- sau final, mỗi promise ghi `UNTOUCHED / ADVANCE / PAY_MINOR / PAY_MAJOR / PAY_ARC`;
- `PAY_MINOR` không được dùng để che `major_payoff_debt` của core promise;
- theo dõi riêng `pay_drought` và `major_payoff_debt`;
- 2–3 chapter không PAY core promise → Retention warning;
- Arc Outline có planned PAY windows + minimum magnitude;
- Batch Audit đo drought thực tế + magnitude distribution.

Chi tiết: `docs/RETENTION_CONTROLLERS_V3.md`.

## 7. Narrative Engine contract

Phân loại chapter theo **cách tạo chuyển động**, không chỉ topic.

Engine gợi ý:

- Q&A meeting
- audit
- negotiation
- hypothesis-test
- training calibration
- chase
- reveal
- ritual
- domestic
- combat
- grief
- wonder
- investigation
- survival task
- repair/build
- travel discovery
- aftermath
- rescue
- moral choice
- competition

Không phải enum đóng.

### Diversity rule

Trong rolling window 4 chapter:

**3/4 cùng primary engine = MAJOR pacing risk.**

Batch boundary không reset window. Ví dụ Ch.4–7 vẫn phải xét cùng nhau dù Ch.4–5 và Ch.6–7 thuộc hai batch khác nhau.

Đặc biệt theo dõi:

- `A hỏi → B trả lời → MC kết luận`;
- `quan sát → giả thuyết → kiểm chứng → kết luận`.

### Dramatic Geometry rule

Engine khác tên không tự động tạo variety. Mỗi chapter theo dõi:

- pressure source;
- decision locus;
- movement mode;
- information flow;
- opposition shape;
- resolution mode;
- reversal type;
- kinetic level.

`3 consecutive` near-same geometry → WATCH. `3/4` cùng core geometry → **MAJOR pacing risk** dù primary engine khác nhau.

## 8. Character DNA + human irrationality

Nhân vật quan trọng cần:

- desire/fear/wound/value/blind spot/contradiction;
- social mask/private self;
- decision heuristic + risk tolerance;
- speech/emotional fingerprint;
- relationship behavior;
- cultivation/combat identity;
- secret/forbidden behavior/arc vector;
- human irrationality profile;
- costly mistake pattern.

Nhân vật thông minh không phải optimizer hoàn hảo. Có thể sai vì bias, sĩ diện, shame, sentimental attachment, sunk cost, fear, loyalty, incomplete data hoặc impulsive kindness.

Không dùng irrationality để làm họ ngu chạy plot.

MC không được chỉ “sai trên giấy” rồi luôn có người sửa trước khi mất gì. Blind spot có thể gây cost thật: tiền, thời gian, quan hệ, thương tích, cơ hội, địa vị hoặc self-image.

Competence conversion chính phải được phân loại `CLEAN_WIN / COSTLY_WIN / PARTIAL / WRONG_MODEL / DEPENDENT_ON_OTHER / FAILURE / NO_CONVERSION`.

- 3 CLEAN_WIN conversions liên tiếp → WATCH;
- 4/5 recent competence conversions là CLEAN_WIN → **MAJOR flattening risk**.

## 9. Style + positive texture

Mục tiêu: tiếng Việt tự nhiên có khí chất tiên hiệp, không văn dịch máy hoặc văn mẫu AI.

Ưu tiên:

- rhythm biến thiên theo scene;
- Hán Việt đúng ngữ cảnh;
- emotion qua hành vi/lựa chọn/body;
- dialogue theo địa vị + DNA;
- worldbuilding qua action/consequence;
- positive texture khi hợp cảnh: interruption, unfinished sentence, practical humor, embarrassment, irrational attachment, sensory messiness, misunderstanding, silence, spontaneous choice.

Cảnh giác:

- transition máy móc;
- recap;
- mọi đoạn kết bằng phán quyết;
- `Không X. Mà Y.` / `Không phải X. Là Y.` quá dày;
- `Đúng. Nhưng... / Vậy... / Cho nên...` thành nhịp mặc định;
- Q&A quá sạch;
- aphorism density cao;
- hypothesis-loop lặp;
- mọi nhân vật cùng giọng;
- cùng opening/ending shape.

## 10. Calibration contract

Không auto-calibrate chỉ từ Ch.1–3.

Chỉ khóa calibration set khi có:

- 4–6 đoạn final/được user duyệt;
- ít nhất 4 Narrative Engine khác nhau;
- narration + dialogue + pressure/wonder phù hợp truyện.

Mỗi chapter dùng 2–3 sample phù hợp và xoay vòng. Học texture/rhythm/diction, không copy câu/rhetorical frame.

## 11. Relaxed Scene contract

Mọi scene biết tối thiểu:

- POV;
- time/place;
- cast;
- knowledge boundary;
- focal tension/pressure/curiosity;
- sensory anchor;
- scene đi ra bằng gì.

### Conflict/transaction scene

Có thể plan goal, obstacle, stakes, leverage, turn, choice, consequence.

### Quiet/discovery/emotional scene

Không bắt buộc đủ goal + obstacle + stakes + turn + choice + consequence + state delta.

Được tồn tại nếu tạo emotional residue, relationship texture, wonder, character revelation, meaningful decompression, meaning change hoặc unresolved movement.

## 12. Emotional Residue contract

Không ép emotional climax mỗi chapter.

Nhưng rolling 3–5 chapter cần có thay đổi có bằng chứng về ít nhất một:

- emotional state;
- relationship meaning;
- self-image;
- attachment/grief/joy/shame/fear;
- object/memory meaning;
- costly mistake scar.

Nếu chỉ knowledge/inventory/cultivation đổi, Reader Retention Editor cảnh báo.

## 13. Three-mode Quality Gate

Mỗi chapter trong v2 enforcement window phải có:

1. `continuity_report.md`;
2. `reader_retention_report.md`;
3. `style_fingerprint_report.md`;
4. `quality_report.md` aggregate.

Aggregate không PASS nếu reviewer còn BLOCKER/MAJOR.

### Continuity Auditor

Canon, timeline, geography, cultivation/power, techniques/items, injury/fatigue, knowledge, relationship/faction state, POV boundary, hard DNA/runtime contradiction.

### Reader Retention Editor

Story Promise magnitude/drought, Narrative Engine + 3/4 rule, Dramatic Geometry, Competence Friction, Aspiration, Heat Curve, Binge Test, Xianxia Density, opening/movement/drag, agency/humanity, costly mistakes, Xianxia Experience, Emotional Residue, ending/reason-to-continue.

Binge Test bắt buộc trả lời:

1. **Khoảnh khắc sướng nhất chương là gì?**
2. **Nếu bỏ ending hook, bản thân chương này có đủ đáng đọc không?** (`YES / WEAK / NO`)

`NONE` ở câu 1 hoặc `NO` ở câu 2 là MAJOR trừ explicit structural waiver hợp lệ theo spec v3.

Xianxia Density Gate bắt buộc kiểm `X0–X3`, Replaceability, rolling 3 và rolling 5 theo `docs/XIANXIA_DENSITY_CONTROLLER.md`.

### Style Fingerprint Auditor

Rhetorical tics, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph/cadence repetition, dialogue sameness, positive texture, calibration drift.

## 14. Rolling 3-Chapter Audit

Trước final các chapter chia hết cho 3: `3, 6, 9, 12, 15...`

Đọc full final N-2 + final N-1 + rewrite candidate N, rồi tạo:

`chapters/NNNN/rolling_3_chapter_audit.md`

Kiểm opening, engine, Dramatic Geometry, dialogue geometry, conflict solution, ending, rhetorical tics, Story Promise magnitude, Competence Friction, Aspiration, Heat trend, Binge Test trend, Xianxia Density/Replaceability, Xianxia Experience, Emotional Residue, costly mistake pattern.

Batch size 5 **không thay cadence này**.

Nếu candidate gây MAJOR, rewrite candidate; không retcon hai final trước chỉ để tạo variety.

## 15. Rewrite contract

Rewrite phải:

1. sửa toàn bộ BLOCKER/MAJOR từ ba reviewer + rolling audit nếu có;
2. giữ canon đúng;
3. không thêm twist lớn ngoài outline để cứu prose;
4. sửa structure nếu lỗi là Narrative Engine/geometry, không synonym-spin;
5. sửa root cause nếu lỗi là friction/aspiration/heat/binge, không chỉ thêm một câu hook;
6. nếu thiếu Xianxia Density, sửa supernatural causality/constraint/consequence, không rắc thêm vocabulary;
7. re-check vùng sửa và continuity liên quan.

## 16. Memory contract

Sau mỗi final, cập nhật story memory trước chapter tiếp.

Bắt buộc nếu thay đổi:

- time/location;
- character state/injury/emotion/goal;
- cultivation;
- inventory;
- relationship;
- knowledge;
- faction;
- promises/debts/tasks in-world;
- foreshadowing/unresolved;
- canon fact.

`memory/reader_experience.md` phải ghi:

- promise `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`;
- pay drought + major payoff debt;
- last_major_payoff;
- last_wonder_beat;
- last_emotional_hit;
- last_costly_mistake;
- recent engines;
- Dramatic Geometry signatures;
- competence outcomes;
- aspiration beats;
- peak heat;
- `xianxia_peak` sequence;
- Ambient / Active / Aspirational Xianxia summary;
- replaceability sequence;
- last `X2+`, last `X3`, genre_density_debt;
- Binge Test result;
- dialogue geometries;
- ending shapes;
- rhetorical tics;
- Xianxia Experience;
- reader appetite/payoff debt.

## 17. Batch 5 contract

**Default batch size = 5.**

Lệnh “viết batch tiếp theo” mà user không nêu số khác được hiểu là **5 chapter**.

Transaction:

```text
Ch.N: plan → draft → 3-mode QC → rewrite → rolling audit if due → final → story+reader memory
Ch.N+1: đọc memory mới → lặp lại
...
đến đủ 5 chapter
→ batch audit
```

Không plan/draft 5 chapter song song rồi update memory cuối batch.

Các range mặc định:

- 1–5
- 6–10
- 11–15
- 16–20
- ...

Cuối batch tạo:

`chapters/batch_NNNN_NNNN_audit.md`

Audit: artifact completion, arc progress, Story Promise magnitude/drought, Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration coverage, Heat Curve rolling-5, Xianxia Density peak sequence/replaceability/Active+Strong counts, Binge Test health, Xianxia/Emotional experience, continuity, character agency/irrationality, power/resource economy, style fingerprint, threads/setup/payoff, Reader Experience consistency, next-batch handoff.

Nếu technical gate sạch nhưng retention hoặc Xianxia Density controller còn MAJOR → `REPAIR_REQUIRED`, không PASS.

Nếu user explicit yêu cầu range/batch size khác, ưu tiên yêu cầu user cho lần chạy đó.

## 18. Orchestration completion gate

Không báo stage/batch complete chỉ vì final đã viết.

### Per chapter v2 artifacts

- scene plan;
- draft;
- 3 reviewer reports;
- aggregate quality report;
- rewrite nếu required;
- rolling audit nếu N%3==0;
- final;
- story memory + reader experience update.

### Per batch artifacts

- đủ 5 final mặc định hoặc đủ requested range;
- memory phản ánh last chapter;
- `batch_NNNN_NNNN_audit.md`;
- arc revision nếu cần;
- next-batch handoff.

Thiếu artifact bắt buộc → `INCOMPLETE`.

### Legacy batch-size compatibility

Existing `batch_0001_0010_audit.md` không invalid khi default đổi 10 → 5.

Khi migrate story:

- set manifest `pipeline.batch_size: 5`;
- giữ audit lịch sử;
- next batch bắt đầu tại `next_chapter` và lấy 5 chapter;
- không fake retroactive split audit.

## 19. Final file contract

Final UTF-8 plain text:

`stories/<slug>/final/Chương X: <Tiêu đề>.txt`

Chỉ chứa title + story prose. Không QC note/metadata/prompt/markdown report.

## 20. Automation discipline

“Tự động” nghĩa ChatGPT tự chạy đầy đủ stage **trong lượt làm việc hiện tại**. Không bỏ kiểm tra, không bịa missing data, không giả có background process, không làm song song stage phụ thuộc nhau.

## 21. Retention Controllers v3 contract

Sáu controller dưới đây là **binding**, không phải suggestion:

1. Dramatic Geometry Controller;
2. Payoff Magnitude;
3. Competence Friction Meter;
4. Aspiration Controller;
5. Heat Curve;
6. Binge Test.

Rule chi tiết và severity mặc định nằm tại `docs/RETENTION_CONTROLLERS_V3.md`.

Không được kết luận batch/chapter PASS chỉ vì continuity, style và artifact completion đều sạch nếu một retention controller còn `MAJOR`.

Core principle:

**PASS kỹ thuật ≠ PASS trải nghiệm đọc.**

## 22. Xianxia Density Controller v3 contract

Controller này là **binding cho truyện mới framework v3**.

Nó kiểm:

1. Ambient Xianxia;
2. Active Xianxia causality;
3. Aspirational Xianxia;
4. `xianxia_peak X0–X3`;
5. Replaceability Test;
6. rolling 3 Active requirement;
7. rolling 5 `2×X2+ + 1×X3` requirement;
8. genre_density_debt.

Rule chi tiết và severity tại `docs/XIANXIA_DENSITY_CONTROLLER.md`.

Không được coi việc có nhiều danh từ “linh khí / linh thạch / công pháp / pháp bảo” là đủ density nếu supernatural law không thay đổi lựa chọn hoặc hậu quả.

Core principle:

**Truyện phải có nhân quả tu tiên, không chỉ skin tu tiên.**