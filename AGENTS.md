# AGENTS.md — v4.0 State + Example Driven Operating Contract

## 1. Creative architecture

Framework hiện hành dùng **state-driven generation + example-driven prose**.

Creative core:

```text
SEED
→ STORY BIBLE
→ CHARACTER BASELINES
→ MASTER OUTLINE
→ INITIAL STORY/ARC STATE
→ CHAPTER STATE
→ SCENE STATE
→ STYLE EXAMPLES + CHARACTER STATE
→ WRITER
→ DRAFT
→ CONTINUITY CHECK
→ PROSE EDIT
→ FINAL
→ STATE UPDATE
→ ONE ATOMIC GIT COMMIT
```

Rule-driven logic chỉ giữ ở lớp **hard guardrails**: canon precedence, factual continuity, file protocol, originality và Git safety. Không dùng checklist sáng tác để điều khiển Writer.

## 2. Three-layer model

### State-driven — what is true now

State quyết định tình hình hiện tại: vị trí, thời gian, mục tiêu, pressure, knowledge, injuries, resources, relationships, unresolved tensions, arc motion và character condition.

Writer không được biến state thành report; state là reality của scene.

### Example-driven — how good project prose feels

Writer nhận style example phù hợp scene. Examples calibrate rhythm, narrative distance, dialogue texture, descriptive density, action/exposition handling và Vietnamese prose feel.

Không copy wording, image, rhetorical frame, scene structure hoặc plot move từ example.

### Rule-driven — hard boundary only

Rules không được trở thành creative checklist. Chỉ giữ:

- canon/source-of-truth precedence;
- knowledge/timeline/power/resource consistency;
- originality/content boundaries;
- state/file schema tối thiểu;
- atomic Git transaction.

## 3. Source of truth

1. `memory/canon_ledger.md`
2. final chapters
3. `bible/*.md`
4. current story/arc/character state
5. continuity ledgers
6. master outline
7. seed
8. chapter/scene state snapshots
9. draft

Master Outline là direction. State là present reality. Final + canon ledger là chuyện đã xảy ra.

## 4. Genesis

Genesis tạo:

- seed;
- story bible;
- character baselines;
- minimal style bible;
- master outline;
- project style example bank;
- initial story state;
- initial arc state;
- initial character states;
- continuity ledgers;
- manifest.

Trước `READY_TO_WRITE`, chạy **Genesis Consistency Audit** giữa world, cultivation, characters, master direction và initial state. Đây là consistency gate, không phải creative controller.

## 5. Arc State

Arc State là runtime strategic state, không phải chapter script. Tối thiểu chứa:

- arc question;
- current phase;
- protagonist/antagonist/faction positions;
- active pressures;
- resource/cultivation pressure;
- relationship motion;
- mysteries/unresolved obligations;
- reader expectations đáng chú ý;
- likely pressure directions;
- exit conditions.

Không bắt mọi expectation phải xuất hiện hoặc PAY theo quota.

## 6. Chapter State

Chapter State được derive từ current story + arc + character states. Nó mô tả:

- chapter entry reality;
- current pressures;
- relevant characters and knowledge;
- ripe tensions/opportunities;
- plausible meaningful state changes;
- continuity anchors.

Không khóa beat sequence nếu không thật sự cần.

## 7. Scene State

Scene State là snapshot sống, không phải checklist plot. Tối thiểu:

- POV/time/place/cast;
- entry physical/emotional/relationship state;
- immediate desires;
- knowledge/suspicions/wrong beliefs;
- pressure/resources/limitations;
- what just happened;
- possible directions nếu hữu ích;
- exit expectation dưới dạng **state change**, không phải beat list.

Writer được phép tìm đường đi tự nhiên miễn không vi phạm canon và chapter/arc state.

## 8. Character State

Character Bible giữ baseline ổn định. Writer ưu tiên runtime Character State:

- immediate/medium goals;
- emotions;
- beliefs and current bias;
- knowledge/suspicions/errors;
- body/injury/fatigue;
- resources;
- relationship context;
- recent consequential memories;
- behavioral pressure.

Không feed toàn bộ response-rule matrix của character vào Writer mỗi chapter.

## 9. Style Examples

Framework calibration mặc định:

- profile: `examples/calibration/PROFILE.md`;
- calibrated-original index: `examples/calibration/index.md`.

Mỗi story vẫn có `examples/style/index.md` riêng và dần thay framework examples bằng prose tốt của chính project.

Selection priority:

1. user-approved project final đúng function;
2. project-owned curated example;
3. calibrated original từ `examples/calibration/`;
4. generic bootstrap từ `examples/default/`.

Thông thường chỉ load **1 primary example**. Chỉ thêm example thứ hai khi scene thật sự có hai prose functions ngang nhau; tối đa 3 cho chapter mixed-mode dài.

Current calibrated functions:

- tactical/survival reasoning;
- cultivation/artifact discovery;
- combat escalation;
- pragmatic negotiation/dialogue;
- world consequence / scale transition.

Examples là demonstration, không phải template.

## 9.1 External sample calibration boundary

Khi user cung cấp prose sample ngoài project:

- đọc sample để distill high-level prose mechanics;
- tách mechanics tốt khỏi lỗi dịch/convert/format;
- tạo `PROFILE.md` trừu tượng;
- tạo **original synthetic examples** để Writer dùng;
- không đưa raw external corpus vào Writer;
- không copy wording, image, rhetorical frame, scene sequence, plot beat, character/world identity;
- không học Chinese-convert clause order, punctuation lỗi, connector spam, spectator spam hoặc onomatopoeia spam.

Raw external samples không cần persist trong repo. Framework dùng derived profile + original calibrated examples.

## 10. Writer boundary

Writer nhận **state + selected example(s)**, không nhận QC checklist hay full calibration profile.

Writer phải:

- coi supplied state là reality;
- để hành động, thoại, perception và consequence mang scene;
- chỉ explicate reasoning khi nó tự nhiên với POV và có ảnh hưởng đến decision/tactic;
- giữ nhân vật trong knowledge/relationship/body/resource state hiện tại;
- viết fiction, không viết plan, analysis hoặc report;
- không copy example.

Current calibration ưu tiên causal prose movement và decision-bound reasoning, nhưng không expose chúng như per-paragraph formula.

Không expose retired controller/metric/style-check list vào Writer prompt.

## 11. Continuity Check

Sau draft chỉ kiểm factual/state contradiction:

- canon;
- timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction state;
- POV identity;
- hard character-baseline contradiction.

Decision:

- `PASS` nếu không có contradiction phải sửa;
- `FIX_REQUIRED` nếu có.

Continuity Checker không chấm literary quality, pacing, payoff quota hay prose style.

## 12. Prose Edit

Sau Continuity PASS, chạy một prose edit nhẹ dựa trên cùng selected examples.

Editor:

- preserve event, decision, dialogue intent và scene shape;
- ưu tiên để prose tốt nguyên trạng;
- cắt explanation mà scene đã thể hiện;
- nén reasoning mang giọng report nhưng giữ suy luận thật sự đổi quyết định;
- sửa tiếng Việt gượng/convert-like;
- cải thiện local causal/spatial clarity khi cần;
- không đồng nhất paragraph length/cadence;
- không manufacture punchline/aphorism;
- không thêm plot hoặc state mới;
- không tái tạo lỗi dịch/convert, connector spam, spectator spam hoặc sound-effect spam từ source samples.

Không cần persist prose-edit report; edited candidate trở thành final.

## 13. State update

Sau final:

1. final là truth;
2. update canon nếu có fact mới được khóa;
3. update timeline/knowledge/inventory/cultivation/relationship ledgers nếu affected;
4. update character states;
5. update story state;
6. update arc state;
7. append compact chapter summary;
8. update manifest pointers;
9. verify state chỉ mô tả event tồn tại trong final.

## 14. Atomic Git chapter transaction

Không write GitHub từng artifact giữa chapter.

1. lấy chapter-start branch HEAD + base tree;
2. assemble state/context;
3. tạo chapter state, scene state, draft, continuity result;
4. fix factual contradiction nếu cần;
5. prose edit;
6. tạo final + toàn bộ state/memory updates;
7. nếu chapter cuối requested batch, tạo batch audit;
8. create blobs;
9. create tree từ chapter-start tree;
10. create commit với chapter-start HEAD làm parent;
11. update branch ref đúng một lần;
12. verify HEAD + manifest/state.

Chapter commit tối thiểu chứa:

- `chapters/NNNN/chapter_state.md`
- `chapters/NNNN/scene_state.md`
- `chapters/NNNN/draft.txt`
- `chapters/NNNN/continuity_check.md`
- final TXT
- changed state/ledgers/summary
- manifest update
- batch audit nếu đóng requested batch.

## 15. Batch 5

Default batch = 5 chapters. Mỗi chapter là một atomic commit tuần tự. Chỉ bắt đầu N+1 sau khi N verify thành công. Batch audit nằm trong commit chapter thứ 5 của requested range.

## 16. Completion

Chapter COMPLETE khi atomic commit chứa state snapshots, draft, Continuity PASS, final và current state/manifest.

Batch COMPLETE khi đủ 5 requested finals/commits, state current qua chapter cuối và batch audit tồn tại.

## 17. Retired active mechanisms

Không còn active:

- Story Promise Controller;
- Combined QC;
- separate style/retention/quality controllers;
- mandatory rewrite stage;
- Writer prose checklist;
- per-chapter payoff quota;
- `rewrite.txt`.

Historical artifacts vẫn được giữ làm lịch sử.