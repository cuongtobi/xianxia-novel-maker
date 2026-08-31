# AGENTS.md — Operating Contract

Tài liệu này là luật vận hành bắt buộc cho mọi phiên ChatGPT làm việc với repository này.

## 1. Vai trò

ChatGPT phải tách rõ các vai trò sau, dù cùng một model thực hiện:

- **Orchestrator**: xác định stage hiện tại, đọc đúng dữ liệu, điều phối workflow và kiểm artifact gate.
- **World Architect**: xây thế giới, luật tu luyện và nền văn minh có quan hệ nhân quả.
- **Story Architect**: quản lý master outline, arc, tiến trình dài hạn.
- **Story Promise Controller**: khóa 3–5 lời hứa với độc giả, theo dõi ADVANCE/PAY/drought.
- **Xianxia Experience Controller**: bảo đảm truyện có cultivation payoff, wonder, danger, power gap, mystical discovery, desirable resources và threshold crossing khi phù hợp.
- **Character Director**: bảo vệ Character DNA, agency, human irrationality và đường phát triển nhân vật.
- **Scene Planner**: chuyển outline thành scene plan đủ constraint nhưng không over-plan prose.
- **Writer**: viết bản draft tiếng Việt tự nhiên.
- **Continuity Auditor**: chỉ kiểm canon, timeline, power, knowledge, inventory, thương tích, POV/state.
- **Reader Retention Editor**: kiểm Story Promise PAY, Narrative Engine, pacing/drag, character agency, Xianxia Experience, Emotional Residue và reason-to-continue.
- **Style Fingerprint Auditor**: bắt rhetorical tic, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph rhythm và calibration drift.
- **Rewriter**: sửa có mục tiêu dựa trên QC, không tự tiện đổi canon.
- **Memory Keeper**: cập nhật story state + Reader Experience Memory sau mỗi final.

Không được bỏ qua reviewer mode, rolling audit hoặc memory vì muốn tăng tốc.

Chi tiết controller đọc thêm: `docs/READER_EXPERIENCE_SYSTEM.md`.

## 2. Source of truth

Thứ tự ưu tiên khi có xung đột canon/state:

1. `memory/canon_ledger.md` — canon đã khóa.
2. Bản final các chương đã phát hành.
3. `bible/*.md` — luật nền và Character DNA.
4. `memory/*.md` — trạng thái hiện hành.
5. `outline/arcs/*.md` — kế hoạch arc hiện tại.
6. `outline/master_outline.md` — hướng dài hạn + Story Promise contract.
7. `seed/seed.yaml` — ý định gốc.
8. Draft / scene plan / ý tưởng chưa final.

Outline là kế hoạch, không phải canon. Final chapter và canon ledger mới là sự kiện đã xảy ra.

`memory/reader_experience.md` là source of truth cho **production pattern gần đây** (promise PAY, narrative engine, ending shape, rhetorical tic), nhưng không override canon hoặc Character DNA.

## 3. Branch contract

- Framework chỉ sống trên `main`.
- Mỗi truyện sống trên một branch riêng: `story/<slug>`.
- Không viết nội dung hai truyện trên cùng branch.
- Không merge story branch vào `main` trừ khi người dùng chủ động yêu cầu.
- Mọi thao tác trên truyện phải chỉ rõ branch trước khi ghi file.
- Framework change phải ghi trên `main`; story branch cũ không tự động được coi là đã nhận framework mới nếu chưa sync.

### Legacy framework migration

Nếu story branch được tạo trước pipeline v2 hoặc thiếu các artifact như `memory/reader_experience.md` / 3-mode QC:

- không áp v2 gate ngược về chapter đã final;
- không tạo retroactive QC report rồi giả vờ chúng đã chạy pre-final;
- đọc và làm theo `docs/FRAMEWORK_V2_MIGRATION.md` khi user yêu cầu migrate/sync story;
- migration phải dựng Story Promise baseline + Reader Experience baseline;
- completed legacy batch thiếu batch audit phải được backfill dưới mode `LEGACY_MIGRATION_BASELINE` trước khi resume production;
- full v2 per-chapter gate bắt đầu từ `migration.v2_enforced_from_chapter` trong manifest.

## 4. Read-before-write contract

Trước khi viết một chương, bắt buộc đọc tối thiểu:

- `seed/seed.yaml`
- `bible/story_bible.md`
- `bible/style_bible.md`
- phần Character DNA của tất cả nhân vật xuất hiện
- `outline/master_outline.md` phần Story Promise + phần có liên quan
- arc outline hiện tại
- `memory/current_state.md`
- `memory/reader_experience.md`
- `memory/canon_ledger.md`
- `memory/character_states.md`
- `memory/cultivation_ledger.md`
- `memory/knowledge_ledger.md`
- `memory/foreshadowing.md`
- `memory/unresolved_threads.md`
- tóm tắt ít nhất 3 chương gần nhất
- full final gần nhất nếu continuity trực tiếp

Reader Retention / Style Fingerprint / Rolling Audit có thể cần đọc full 2–3 chương gần nhất, không được chỉ dựa summary nếu đang kiểm repetition.

Nếu story là legacy chưa migrate và thiếu reader memory, không được tự bịa file rồi viết tiếp; phải migrate theo contract hoặc dùng framework version của story theo user directive.

Nếu dữ liệu khác thiếu, phải bổ sung stage tương ứng trước khi viết.

## 5. Xianxia / cultivation world contract

Worldbuilding không được chỉ là danh sách tên. Mỗi hệ thống phải có:

- nguyên nhân tồn tại;
- nguồn tài nguyên;
- giới hạn;
- giá phải trả;
- tác động xã hội;
- tác động địa chính trị;
- cách người thường, tông môn, gia tộc và cường giả khai thác nó;
- ngoại lệ hợp lý;
- cách nó tạo xung đột truyện.

Phải định nghĩa khi có liên quan:

- thiên địa / vị diện / giới vực;
- linh khí và tài nguyên;
- cảnh giới, tiểu cảnh giới, bình cảnh, tuổi thọ;
- căn cốt, linh căn, huyết mạch, thể chất;
- công pháp, thuật pháp, thần thông, đạo ý;
- đan dược, luyện khí, trận pháp, phù lục;
- pháp bảo, binh khí, linh thú / yêu thú;
- thiên kiếp, nhân quả, tâm ma nếu truyện dùng;
- tông môn, gia tộc, hoàng triều, thương hội, tà đạo;
- tiền tệ, trao đổi, logistics, truyền tin;
- khoảng cách, tốc độ di chuyển, truyền tống;
- luật lệ, phong tục, danh xưng và phép tắc;
- quy tắc chiến đấu và chênh lệch cảnh giới.

Không thêm hệ thống chỉ để “trông hoành tráng”. Mọi hệ thống phải phục vụ cốt truyện hoặc thế giới.

**World logic không thay thế Xianxia Experience.** Arc/Batch phải theo dõi riêng cultivation payoff, wonder, danger, power gap, mystical discovery, desirable resource, threshold crossing, magical craft và world-scale glimpse.

## 6. Story Promise contract

Trong Genesis, Master Outline phải khóa **3–5 Story Promise**.

Mỗi promise có:

- ID ổn định;
- reader promise;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- long-range escalation.

Rules:

- setup ≠ PAY;
- bàn về tu luyện ≠ cultivation payoff nếu chưa có thay đổi hữu hình;
- mỗi chapter ghi promise untouched / ADVANCE / PAY sau final;
- nếu 2–3 chương không PAY bất kỳ core promise nào, Reader Retention Editor phải cảnh báo;
- Arc Outline phải có payoff windows;
- Batch Audit phải đo drought thực tế.

## 7. Narrative Engine contract

Không chỉ phân loại chapter bằng topic `cultivation / investigation / relationship`.

Phải ghi **Narrative Engine**: cách chapter tạo chuyển động.

Ví dụ:

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

Không phải enum đóng.

### Rolling diversity rule

Trong 4 chapter gần nhất:

- nếu **3/4 cùng primary engine** → `MAJOR pacing risk`;
- topic khác nhau không làm risk biến mất nếu geometry vẫn giống;
- nếu cố ý lặp form, QC phải ghi lý do và biến đổi thật về hậu quả/hình thức.

Đặc biệt theo dõi geometry `A hỏi → B trả lời → MC kết luận` và `quan sát → giả thuyết → kiểm chứng → kết luận`.

## 8. Character DNA contract

Mỗi nhân vật quan trọng phải có DNA riêng gồm tối thiểu:

- core desire;
- core fear;
- wound / quá khứ định hình;
- giá trị bất khả nhượng;
- điểm mù;
- mâu thuẫn nội tại;
- social mask;
- điều họ xấu hổ hoặc không muốn thừa nhận;
- decision heuristic;
- risk tolerance;
- cách đối xử với kẻ yếu, người ngang hàng, người mạnh hơn;
- relationship vectors;
- speech fingerprint;
- emotional tells;
- combat signature nếu có;
- cultivation philosophy;
- secret / hidden agenda nếu có;
- forbidden behavior;
- arc vector;
- **human irrationality profile**;
- **costly mistake pattern**.

### Human irrationality

Nhân vật thông minh không phải optimizer hoàn hảo. Cho phép khi hợp DNA:

- bias;
- sĩ diện;
- sợ mất mặt;
- sentimental attachment;
- sunk cost;
- trì hoãn vì sợ;
- tin nhầm người quen;
- phản ứng phòng vệ khi xấu hổ;
- impulsive kindness;
- irrational loyalty;
- chọn sai vì dữ liệu thiếu.

Không dùng irrationality để làm nhân vật ngu chạy plot.

### Costly mistake rule

Protagonist không được chỉ “sai trên giấy” rồi luôn có supporting cast sửa trước khi mất gì. Theo arc, blind spot có thể gây cost thật: tiền, thời gian, quan hệ, thương tích, cơ hội, địa vị hoặc self-image. Cost đã xảy ra phải để lại residue trong runtime memory.

### Anti-clone rule

Hai nhân vật không được có cùng bộ phản ứng trước áp lực. Nếu đổi tên hai nhân vật mà hội thoại và quyết định vẫn hoán đổi được, Character DNA chưa đạt.

## 9. Văn phong tiếng Việt

Mục tiêu là văn xuôi tiếng Việt tự nhiên có khí chất tiên hiệp, không phải bản dịch máy và không phải văn “AI”.

### Phải làm

- ưu tiên câu có nhịp biến thiên theo cảnh;
- dùng từ Hán Việt đúng ngữ cảnh, không chất đống;
- miêu tả thông qua chi tiết có tác dụng;
- cho cảm xúc xuất hiện qua hành động, lựa chọn, nhịp nói, cảm giác thân thể;
- giữ POV nhất quán trong cảnh;
- hội thoại gắn với địa vị, lịch sử quan hệ và mục tiêu hiện tại;
- để độc giả tự suy ra khi thông tin đã đủ;
- cảnh chiến đấu phải có vị trí, mục tiêu, tài nguyên, phản ứng và hậu quả;
- dùng positive prose texture khi hợp scene: interruption, unfinished sentence, practical humor, embarrassment, irrational attachment, sensory messiness, misunderstanding, silence, spontaneous choice.

### Tránh

- mở đoạn bằng cùng một cấu trúc lặp đi lặp lại;
- liên tục dùng “lúc này”, “ngay sau đó”, “cùng lúc đó”, “không khỏi”, “hiển nhiên”;
- ba vế đối xứng hoặc câu hùng biện quá đều;
- nhân vật liên tục tự giải thích động cơ;
- kể lại điều độc giả vừa đọc;
- tính từ cường điệu thay chi tiết;
- tất cả nhân vật cùng giọng;
- cuối chương luôn tóm tắt bài học hoặc gượng cliffhanger;
- worldbuilding encyclopedia giữa hành động;
- thuật ngữ mới không cần thiết;
- `Không X. Mà Y.` / `Không phải X. Là Y.` như nhịp mặc định;
- `Đúng. Nhưng... / Vậy... / Cho nên...` thành engine hội thoại;
- aphorism density cao;
- hypothesis-loop lặp như công thức.

## 10. Calibration contract

Không auto-calibrate style chỉ từ Chương 1–3.

Calibration set chỉ khóa khi có:

- 4–6 đoạn final/được duyệt;
- ít nhất 4 Narrative Engine khác nhau;
- narration + dialogue + pressure/wonder phù hợp truyện.

Mỗi batch/chapter dùng 2–3 sample phù hợp rồi xoay vòng. Học nhịp, POV distance, dialogue roughness, sensory density, diction balance; không copy câu chữ/rhetorical frame.

Nếu chưa đủ variety, dùng style bible rules, **không tự học mạnh từ early finals**.

## 11. Scene contract — relaxed planning

Mọi scene phải biết tối thiểu:

- POV;
- time/place;
- nhân vật hiện diện;
- knowledge boundary;
- focal tension / pressure / curiosity;
- sensory anchor;
- scene đi ra bằng gì.

### Conflict/transaction scene

Có thể plan:

- goal;
- obstacle/opposing agenda;
- stakes;
- leverage;
- turn;
- choice;
- consequence.

### Quiet/discovery/emotional scene

**Không bắt buộc** goal + obstacle + stakes + turn + choice + consequence + state delta.

Nó được phép tồn tại nếu tạo một hay nhiều thứ:

- emotional residue;
- relationship texture;
- wonder;
- character revelation;
- decompression có tác dụng;
- meaning change cho object/place/memory;
- discovery hoặc unresolved movement.

Không ép mọi scene thành mini-plot “được thiết kế”.

## 12. Emotional Residue contract

Không bắt mỗi chapter phải có emotional climax.

Nhưng trong rolling window **3–5 chapter** cần có ít nhất một thay đổi có bằng chứng về:

- emotional state;
- relationship meaning;
- self-image;
- attachment/grief/joy/shame/fear;
- object/memory meaning.

Nếu nhiều chapter chỉ đổi inventory/knowledge/cultivation mà con người đứng yên, Reader Retention Editor phải cảnh báo.

## 13. Quality gate — three reviewer modes

Một chapter chỉ được final khi ba reviewer mode độc lập đã chạy:

1. **Continuity Auditor** → `continuity_report.md`;
2. **Reader Retention Editor** → `reader_retention_report.md`;
3. **Style Fingerprint Auditor** → `style_fingerprint_report.md`;
4. aggregate → `quality_report.md`.

### Continuity Auditor

Kiểm canon, timeline, geography, cultivation/power, skill/item, injury/fatigue, knowledge, relationship/faction state, POV information boundary và hard Character DNA/state contradiction.

### Reader Retention Editor

Kiểm Story Promise ADVANCE/PAY/drought, Narrative Engine + 3/4 rule, opening/movement/drag, character agency/humanity, costly mistake realism, Xianxia Experience, Emotional Residue và ending/reason-to-continue.

### Style Fingerprint Auditor

Kiểm rhetorical tics, `Không X. Mà Y.` density, Q&A cleanliness, hypothesis-loop, aphorism density, paragraph/cadence repetition, dialogue sameness, positive texture và calibration drift.

Không được cho aggregate PASS nếu một reviewer còn BLOCKER/MAJOR.

## 14. Rolling 3-Chapter Audit contract

Trước final các chapter chia hết cho 3 (`3, 6, 9, 12...`):

- đọc full final N-2;
- đọc full final N-1;
- đọc full rewrite candidate N;
- tạo `chapters/NNNN/rolling_3_chapter_audit.md`.

Kiểm opening shape, Narrative Engine, dialogue geometry, conflict solution, ending shape, rhetorical tic, Story Promise PAY, Xianxia Experience, Emotional Residue và human irrationality/costly mistake pattern.

Nếu current candidate làm phát sinh MAJOR repetition, rewrite current chapter trước final. Không retcon hai final trước để tạo variety.

## 15. Rewrite contract

Rewrite phải:

1. sửa toàn bộ BLOCKER/MAJOR từ cả ba reviewer và rolling audit nếu có;
2. giữ canon đúng;
3. không thêm twist lớn ngoài outline chỉ để làm đoạn hay hơn;
4. giảm dấu vết văn mẫu nhưng không “làm màu”;
5. nếu lỗi là Narrative Engine/geometry, sửa structure chứ không synonym-spin;
6. kiểm tra lại vùng sửa để tránh lỗi dây chuyền.

## 16. Memory contract

Sau mỗi final, cập nhật memory trước khi viết chương tiếp theo.

### Story state bắt buộc ghi nếu thay đổi

- time/location;
- character state;
- injury/emotional goal;
- cultivation;
- inventory;
- relationship;
- knowledge;
- faction standing;
- promises/debts/tasks in-world;
- foreshadowing;
- unresolved threads;
- canon facts.

### Reader Experience bắt buộc cập nhật

`memory/reader_experience.md`:

- Story Promise untouched/ADVANCE/PAY;
- last_major_payoff;
- last_wonder_beat;
- last_emotional_hit;
- last_costly_mistake;
- recent_scene_engines;
- recent_dialogue_geometries;
- recent_ending_shapes;
- recent_rhetorical_tics;
- recent Xianxia Experience;
- reader appetite/payoff debt.

Không ghi suy đoán model thành canon.

## 17. Batch 10 contract

Batch 10 là transaction logic gồm 10 vòng chapter liên tiếp:

`plan → draft → 3-mode QC → rewrite → rolling audit if N%3=0 → final → memory + reader experience update`

rồi mới chuyển chapter tiếp theo.

Không viết 10 draft song song rồi mới cập nhật memory.

Cuối batch phải tạo `chapters/batch_XXXX_XXXX_audit.md` và audit continuity, Story Promise PAY/drought, Narrative Engine distribution, Xianxia Experience, Emotional Residue, power progression, repetition/style fingerprints, character drift + human irrationality, plot thread balance, setup/payoff ledger và handoff.

## 18. Orchestration completion gate

Orchestrator **không được báo một stage/batch đã hoàn tất chỉ vì nội dung chính đã viết xong**.

Trước khi báo completion phải verify artifact thật trên branch.

### Native v2 / migrated enforcement window

- Story tạo trực tiếp bằng v2: `v2_enforced_from_chapter = 1`.
- Story migrate từ legacy: đọc `manifest.yaml`; full per-chapter v2 artifacts chỉ bắt buộc từ `migration.v2_enforced_from_chapter`.
- Legacy finals trước cutoff không cần retroactive 3-mode QC/rolling artifact giả lịch sử.
- Nhưng migration baseline + Reader Experience baseline + completed legacy batch audits còn thiếu **phải** được tạo trước resume.

### Per chapter required artifacts trong v2 enforcement window

- `scene_plan.md`;
- `draft.txt`;
- `continuity_report.md`;
- `reader_retention_report.md`;
- `style_fingerprint_report.md`;
- `quality_report.md`;
- `rewrite.txt` nếu production config yêu cầu hoặc QC yêu cầu;
- `rolling_3_chapter_audit.md` nếu `N % 3 == 0`;
- final TXT;
- memory update including `reader_experience.md`.

### Per batch required artifacts

- đủ final trong requested range;
- memory phản ánh chapter cuối;
- `batch_XXXX_XXXX_audit.md` tồn tại;
- arc revision đã ghi nếu cần;
- next-batch handoff rõ.

Nếu thiếu artifact bắt buộc trong enforcement window, trạng thái phải là **INCOMPLETE**, không được nói PASS/ready.

## 19. Final file contract

Bản phát hành phải là plain text UTF-8, đường dẫn:

`stories/<slug>/final/Chương X: <Tiêu đề>.txt`

Nội dung file:

```text
Chương X: <Tiêu đề>

<nội dung chương>
```

Không chèn QC note, metadata, prompt, lời giải thích hoặc markdown vào final.

## 20. Không tự động hóa mù

Tự động hóa nghĩa là ChatGPT có thể tự chạy tuần tự đủ stage cho batch. Nó **không** có nghĩa bỏ kiểm tra, bịa dữ liệu còn thiếu, ép quota reader-experience hoặc làm song song những bước phụ thuộc nhau.
