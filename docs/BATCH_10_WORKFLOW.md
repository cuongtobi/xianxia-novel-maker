# Batch 10 Chapters Workflow

## 1. Mục tiêu

Cho phép người dùng ra một lệnh như:

> Viết tiếp batch 10 chương cho truyện hiện tại.

ChatGPT tự chạy đủ pipeline cho 10 chương **trong cùng story branch**, vẫn xử lý từng chương tuần tự để story memory và Reader Experience Memory của chương N trở thành input của chương N+1.

Pipeline tối ưu đồng thời cho:

- continuity;
- Story Promise delivery;
- Narrative Engine diversity;
- Xianxia Experience;
- Emotional Residue;
- prose/style naturalness.

## 2. Nguyên tắc cốt lõi

Sai:

```text
plan 10 chương
→ draft cả 10
→ QC cả 10
→ final cả 10
→ update memory
```

Đúng:

```text
Ch. N:
assemble context
→ plan
→ draft
→ 3 reviewer QC
→ aggregate gate
→ rewrite
→ critical re-QC
→ rolling 3-chapter audit if N%3=0
→ final
→ story memory + reader experience update

Ch. N+1: đọc memory mới → lặp lại
```

Batch chỉ là đơn vị **điều phối và audit**, không phải đơn vị bỏ dependency.

## 3. Batch Preflight

Trước chương đầu của batch:

1. xác nhận branch `story/<slug>`;
2. đọc `AGENTS.md`;
3. đọc `docs/READER_EXPERIENCE_SYSTEM.md` nếu framework branch có file này;
4. đọc `seed/seed.yaml`;
5. đọc toàn bộ ba bible;
6. đọc phần Story Promise + master outline liên quan;
7. đọc arc hiện tại;
8. đọc `memory/current_state.md`;
9. đọc `memory/reader_experience.md`;
10. đọc các ledger liên quan;
11. đọc summaries 3–10 chương gần nhất;
12. đọc full final chương gần nhất;
13. khi cần đánh repetition, đọc full 2–3 final gần nhất;
14. xác định chapter range của batch;
15. **verify artifact state thật** của chapter/batch trước đó, không suy ra từ lời chat.

### Preflight output nội bộ

- start chapter;
- end chapter;
- active arc;
- major canon constraints;
- active threads;
- Story Promise state + last PAY/drought;
- recent Narrative Engines;
- recent dialogue geometries;
- recent ending shapes;
- recent rhetorical tics;
- last Xianxia Experience beats;
- last Emotional Residue;
- current reader appetite / payoff debt;
- likely payoff windows;
- cultivation constraints;
- character drift + human irrationality risks;
- pacing risks từ batch trước.

Không cần tạo file preflight riêng trừ khi audit/debug cần.

## 4. Story Promise Controller — Batch View

Đọc 3–5 promise đã khóa trong `outline/master_outline.md`.

Trước batch xác định:

- promise nào là core;
- chapter cuối cùng mỗi promise được PAY;
- current drought;
- promise nào phải PAY trong batch này;
- promise nào chỉ ADVANCE;
- promise nào dễ bị worldbuilding/logistics che lấp.

### Warning/gate

- `ADVANCE ≠ PAY`.
- Nếu 2–3 chapter liên tiếp không PAY bất kỳ core promise nào → Reader Retention Editor phải cảnh báo.
- Nếu arc beat chỉ setup kéo dài nhưng premise chính đang đói payoff → sửa beat tương lai chưa final.
- Không ép một PAY giả chỉ để tick checklist.

## 5. Arc Coverage Check

Trước batch, xác định:

- 10 chương nằm trọn một arc hay cắt arc boundary;
- nếu arc hiện tại hết giữa batch, phải tạo/đọc arc tiếp theo **trước chương vượt boundary**;
- không kéo dài arc chỉ để đủ 10 chương;
- không kết arc sớm chỉ vì hết batch;
- Story Promise và Xianxia Experience của arc mới phải được initialized trước khi viết.

## 6. Chapter Loop

Với mỗi chương `N`:

### Stage A — Assemble Context

Đọc:

- current state mới nhất;
- `memory/reader_experience.md` mới nhất;
- arc beat dự kiến cho N;
- Story Promise target;
- Character DNA nhân vật tham gia;
- ledgers liên quan;
- summary gần nhất;
- final chương N-1 khi continuity trực tiếp;
- full N-1/N-2 nếu reader/style pattern cần kiểm.

Tạo context constraints trong reasoning, không ghi thành prose.

Bắt buộc biết trước plan:

- recent primary Narrative Engines;
- current 3/4 repetition risk;
- recent ending shapes;
- recent rhetorical tics;
- current promise drought;
- last wonder/emotional hit.

### Stage B — Scene Plan

Tạo:

`stories/<slug>/chapters/NNNN/scene_plan.md`

Planner phải dùng `templates/chapter_scene.template.md` mới.

Plan chapter-level nêu:

- primary/secondary Narrative Engine;
- Story Promise target ADVANCE/PAY;
- knowledge/canon constraints;
- Xianxia Experience target nếu organic;
- Emotional movement nếu có;
- human irrationality/blind spot nếu relevant;
- ending shape.

#### Scene planning rule

Không ép mọi scene có đủ:

`goal + obstacle + stakes + turn + choice + consequence + state delta`.

- Conflict/transaction scene có thể dùng structure đó.
- Quiet/discovery/emotional scene chỉ cần focal tension/curiosity, sensory anchor, knowledge boundary và movement/residue hợp lý.

Nếu current chapter sẽ tạo `3/4 same primary Narrative Engine`, redesign plan trước khi draft, trừ khi deliberate pattern đã được arc + QC biện minh.

### Stage C — Draft

Tạo:

`stories/<slug>/chapters/NNNN/draft.txt`

Draft chỉ chứa title + truyện, không tự đánh giá trong file.

Writer được tự do micro-prose và human texture nhưng không phá constraint.

Writer phải tránh biến plan thành prose checklist; không cần biểu diễn mọi field trong scene plan bằng một câu rõ ràng.

### Stage D1 — Continuity Auditor

Đọc draft + canon/state.

Tạo:

`stories/<slug>/chapters/NNNN/continuity_report.md`

Dùng `templates/continuity_report.template.md`.

Chỉ tập trung:

- canon;
- timeline;
- geography;
- cultivation/power;
- techniques/items;
- injury/fatigue;
- knowledge/epistemics;
- relationship/faction state;
- POV boundary;
- hard Character DNA/runtime contradiction.

Không dùng reviewer này để tuyên bố chapter “cuốn”.

### Stage D2 — Reader Retention Editor

Tạo:

`stories/<slug>/chapters/NNNN/reader_retention_report.md`

Dùng `templates/reader_retention_report.template.md`.

Kiểm:

- Story Promise ADVANCE/PAY/drought;
- chapter payoff;
- primary Narrative Engine;
- rolling 3/4 same-engine risk;
- opening/movement/drag;
- conflict solution repetition;
- character agency/humanity;
- protagonist costly mistake pattern;
- Xianxia Experience;
- Emotional Residue;
- ending/reason-to-continue.

### Stage D3 — Style Fingerprint Auditor

Tạo:

`stories/<slug>/chapters/NNNN/style_fingerprint_report.md`

Dùng `templates/style_fingerprint_report.template.md`.

Kiểm:

- `Không X. Mà Y.` / phủ định đối xứng;
- `Đúng. Nhưng... / Vậy... / Cho nên...` rhythm;
- Q&A cleanliness;
- hypothesis-loop;
- aphorism density;
- paragraph/sentence shape;
- lexical/rhetorical tic;
- positive prose texture;
- calibration drift.

### Stage D4 — Aggregate Quality Gate

Tạo:

`stories/<slug>/chapters/NNNN/quality_report.md`

Dùng `templates/quality_report.template.md`.

Aggregate ba reviewer.

Không được cho PASS nếu một reviewer còn BLOCKER/MAJOR.

### Stage E — Rewrite

Nếu có BLOCKER hoặc MAJOR từ bất kỳ reviewer nào, tạo full rewrite:

`stories/<slug>/chapters/NNNN/rewrite.txt`

Nếu production config `require_rewrite: true`, vẫn tạo rewrite như pass biên tập cuối dù draft không có BLOCKER/MAJOR.

Rewrite priority:

1. canon/data;
2. Character DNA/knowledge;
3. causality;
4. Story Promise/retention;
5. Narrative Engine structure;
6. Xianxia Experience/Emotional Residue nếu đang drought;
7. style fingerprint;
8. minor polish.

Không synonym-spin để chữa structural repetition.

### Stage F — Critical Re-QC

Kiểm lại:

- tất cả BLOCKER;
- tất cả MAJOR;
- vùng rewrite lớn;
- continuity bị ảnh hưởng;
- reader promise/payoff classification;
- engine/geometry nếu đã đổi structure;
- style fingerprint nếu đã rewrite mạnh prose.

Nếu reviewer bị ảnh hưởng đáng kể, cập nhật/rerun report tương ứng.

Không final nếu còn BLOCKER/MAJOR.

### Stage G — Rolling 3-Chapter Audit

Chạy **trước final** nếu `N % 3 == 0`.

Đọc full:

- final N-2;
- final N-1;
- rewrite candidate N.

Tạo:

`stories/<slug>/chapters/NNNN/rolling_3_chapter_audit.md`

Dùng `templates/rolling_3_chapter_audit.template.md`.

Kiểm:

- opening shape;
- Narrative Engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- Story Promise PAY;
- Xianxia Experience;
- Emotional Residue;
- human irrationality/costly mistake pattern.

#### Rolling gate

Nếu current candidate tạo MAJOR repetition/drought:

1. rewrite current candidate;
2. rerun affected reviewer + aggregate;
3. rerun rolling audit;
4. chỉ final khi MAJOR = 0.

Không retcon N-2/N-1 chỉ để tạo variety.

### Stage H — Final

Tạo:

`stories/<slug>/final/Chương N: <Tiêu đề>.txt`

Plain text:

```text
Chương N: <Tiêu đề>

<nội dung>
```

### Stage I — Memory Update

Ngay sau final cập nhật story state:

- chapter summary;
- timeline;
- character states;
- relationships;
- cultivation;
- inventory;
- factions/locations;
- knowledge;
- foreshadowing;
- unresolved threads;
- canon ledger nếu có fact mới;
- current_state.

Đồng thời cập nhật:

`stories/<slug>/memory/reader_experience.md`

Bắt buộc ghi:

- Story Promise untouched/ADVANCE/PAY;
- last_major_payoff;
- last_wonder_beat;
- last_emotional_hit;
- last_costly_mistake;
- recent primary/secondary engines;
- dialogue geometry;
- ending shape;
- rhetorical tics đáng theo dõi;
- Xianxia Experience delivered;
- current reader appetite/payoff debt.

Không sang chương N+1 nếu `reader_experience.md` chưa phản ánh final N.

### Stage J — Commit checkpoint

Có thể commit theo từng chương hoặc nhóm thay đổi nhỏ, nhưng branch state phải luôn phản ánh chapter transaction hoàn tất.

## 7. Dynamic Outline Adaptation

Sau mỗi final + memory update, kiểm beat chương kế tiếp còn hợp state mới không.

Nếu không:

- không ép nhân vật trở về plan cũ;
- giữ arc goal và hard constraint quan trọng;
- điều chỉnh beat tương lai;
- cập nhật arc outline nếu thay đổi đáng kể;
- cập nhật planned Story Promise PAY windows;
- cập nhật Narrative Engine distribution nếu repetition risk thay đổi;
- ghi revision log.

## 8. Narrative Engine Controller — Batch Level

Theo dõi **engine**, không chỉ topic.

Vocabulary gợi ý:

- Q&A meeting;
- audit;
- negotiation;
- hypothesis-test;
- training calibration;
- chase;
- reveal;
- ritual;
- domestic;
- combat;
- grief;
- wonder;
- investigation;
- survival task;
- repair/build;
- travel discovery;
- aftermath;
- rescue;
- moral choice;
- competition.

Có thể thêm engine mới.

### Hard warning

Trong rolling window 4 chapter:

**3/4 cùng primary engine = MAJOR pacing risk.**

Không được nói “topic khác nên ổn” nếu geometry giống nhau.

## 9. Xianxia Experience Controller — Batch Level

Theo dõi riêng:

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

Không quota cứng.

Nhưng nếu nhiều chapter liên tiếp chỉ logistics/họp/giấy tờ/điều tra đời thường, cần xác định truyện có đang đói fantasy experience không.

## 10. Emotional Residue Controller — Batch Level

Theo rolling 3–5 chapter:

- emotional state có đổi?;
- relationship meaning có đổi?;
- self-image có đổi?;
- attachment/grief/joy/shame/fear có để lại residue?;
- object/memory có đổi nghĩa?;

Nếu chỉ knowledge/inventory/cultivation đổi, cảnh báo.

Không tạo bi kịch giả chỉ để tick emotional beat.

## 11. Batch-Level Character Controller

Cuối mỗi 3–4 chapter, tự kiểm:

- ai biến mất quá lâu;
- ai mất agency;
- ai có giọng hội thoại trôi về narrator;
- relationship change có earned không;
- antagonist/faction có hành động ngoài màn hình hợp lý không;
- ai đang trở thành optimizer quá hoàn hảo;
- bias/pride/shame/attachment có biến mất khỏi DNA không;
- MC có liên tục được người khác sửa sai trước khi trả giá không.

## 12. Batch-Level Power Controller

Theo dõi:

- tài nguyên nhận vs tiêu;
- technique mastery;
- injury recovery;
- realm progress;
- breakthrough setup;
- đối thủ tương quan;
- cheat/special trait usage frequency;
- cultivation PAY frequency vs chỉ discussion/training setup.

Không để special trait thành đáp án cho mọi vấn đề.

## 13. End-of-Batch Audit

Sau chapter cuối batch, bắt buộc tạo:

`stories/<slug>/chapters/batch_NNNN_NNNN_audit.md`

Template nội dung tối thiểu:

```md
# Batch Audit — Ch. A–B

## 1. Arc progress
- Start state:
- End state:
- Arc question progress:
- Outline deviation:

## 2. Story Promise Controller
| Promise | ADVANCE chapters | PAY chapters | Last PAY | Drought | Risk |

## 3. Narrative Engine Distribution
| Chapter | Primary engine | Secondary engine | Dialogue geometry | Ending shape |
- Any 3/4 same-engine windows?:
- Repeated conflict solution?:

## 4. Xianxia Experience
- cultivation payoff:
- wonder:
- danger:
- power gap:
- mystical discovery:
- desirable resource:
- threshold crossing:
- magical craft:
- world-scale glimpse:
- drought risk:

## 5. Emotional Residue
- relationship changes:
- self-image changes:
- emotional hits:
- costly mistakes:
- 3–5 chapter flat windows:

## 6. Continuity
- Timeline:
- Geography:
- Knowledge:
- Inventory:
- Injuries:
- Relationships:

## 7. Character
- MC drift:
- Supporting cast agency:
- Human irrationality retained?:
- Antagonist movement:
- Voice differentiation:

## 8. Cultivation
- Progress earned?:
- Resource economy:
- Power scaling anomalies:

## 9. Style Fingerprint
- Repeated words/phrases:
- Rhetorical tics:
- Q&A cleanliness:
- Hypothesis-loop:
- Aphorism density:
- Repeated openings/endings:
- Calibration rotation:

## 10. Threads
- Opened:
- Advanced:
- Paid:
- Forgotten risk:

## 11. Next batch handoff
- Required arc beats:
- Core promise PAY debt:
- Narrative engines to rest:
- Xianxia experience debt:
- Emotional residue needs:
- Immediate constraints:
- Payoffs approaching:
- Characters requiring attention:
- Power constraints:
- Style corrections:
```

## 14. Batch Completion Criteria

Batch chỉ hoàn tất khi **Orchestrator verify artifact thật**:

- đủ final files trong requested range;
- mỗi chapter có `scene_plan.md`;
- mỗi chapter có `draft.txt`;
- mỗi chapter có 3 reviewer reports;
- mỗi chapter có aggregate `quality_report.md`;
- rewrite tồn tại khi required;
- chapter `3/6/9/...` có rolling audit;
- không final nào còn BLOCKER/MAJOR;
- story memory phản ánh chapter cuối;
- `reader_experience.md` phản ánh chapter cuối;
- `batch_NNNN_NNNN_audit.md` tồn tại;
- arc outline đã cập nhật nếu deviation;
- next-batch handoff rõ.

**Thiếu một artifact bắt buộc = INCOMPLETE.** Không được báo batch PASS/ready.

## 15. Resume After New Chat

Trong phiên ChatGPT mới, user chỉ cần chỉ repo + story branch và nói tiếp tục batch.

ChatGPT phải đọc:

1. `AGENTS.md` từ framework/source branch phù hợp;
2. story seed;
3. current state;
4. `memory/reader_experience.md`;
5. batch audit gần nhất;
6. arc hiện tại;
7. Story Promise section master outline;
8. bible cần thiết;
9. recent summaries/final;
10. verify artifact tree chapter gần nhất.

Không dựa vào memory hội thoại ChatGPT cũ như source of truth.

Nếu story branch được tạo trước một framework upgrade, không giả định branch đã có controller/template mới; phải kiểm file thực tế hoặc sync framework theo quy trình repo.

## 16. User Commands

Các lệnh tự nhiên được hỗ trợ:

- `Khởi tạo truyện mới từ seed này.`
- `Xây story bible, style bible, characters bible.`
- `Lập master outline và arc 1.`
- `Viết chương 1 hoàn chỉnh qua QC.`
- `Viết batch 10 chương tiếp theo.`
- `Tiếp tục từ current_state.`
- `Audit continuity 20 chương gần nhất.`
- `Audit reader retention 10 chương gần nhất.`
- `Audit Narrative Engine repetition.`
- `Kiểm Story Promise payoff debt.`
- `Kiểm Xianxia Experience drought.`
- `Kiểm tra power scaling.`
- `Kiểm tra Character DNA drift.`
- `Sửa arc outline theo diễn biến final, không retcon.`

## 17. Stop Conditions

Tự dừng trước khi tạo final nếu:

- canon conflict không thể giải quyết mà không retcon;
- seed có constraint `user_must_decide` chưa có đáp án và ảnh hưởng trực tiếp;
- chapter outcome bắt buộc phá hard rule;
- final filename/title không xác định được;
- một trong ba reviewer còn BLOCKER/MAJOR;
- rolling audit required nhưng chưa tồn tại hoặc còn MAJOR.

Trong các trường hợp khác, ưu tiên tự giải quyết sáng tạo theo bible/controller và tiếp tục batch.
