# Pipeline Prompts — Atomic Combined QC + Prose Mechanics Reference

Controller duy nhất: **Story Promise Controller**.

Reference Style chỉ là **prose mechanics**. Không được ảnh hưởng plot, arc, Character DNA, worldbuilding, cultivation design hoặc payoff design.

## P0 — Orchestrator

1. Xác định exact repo/branch/slug.
2. Đọc manifest/source of truth.
3. Resolve requested range; `batch tiếp theo` mặc định = 5 chapters.
4. Với từng chapter, giữ intermediate work trong session memory.
5. Chỉ persist khi scene plan + draft + combined QC + final + memory/manifest đều sẵn sàng.
6. Persist chapter bằng one tree/commit + one branch ref update.
7. Không sang chapter mới trước khi commit chapter hiện tại verify thành công.
8. Không tạo retired QC artifacts/controllers.

## P1 — Seed Validator

Validate premise, protagonist, world/cultivation intent, tone, boundaries, target length và user decisions.

Nếu Reference Style bật, verify:

- profile path;
- `reference_style_mode: prose_mechanics_only`;
- reference không được dùng như plot/story template.

## P2 — Story Bible Architect

Build world bằng causal logic tự nhiên: `law → resource/limit → institution/behavior → conflict`. Khóa cultivation, factions, history, geography, crafts, economy, social order, hard rules và mystery foundations.

**Không đọc Reference Prose Profile để quyết định world/story.**

## P3 — Style Bible Director

Đây là stage duy nhất được phép chuyển hóa Reference Prose Profile vào house style.

Nếu dùng `TIEN_NGHICH_HIGH_LEVEL_STYLE.md`, chỉ chọn prose mechanics:

- sentence architecture;
- sentence-length rhythm;
- clause flow/transitions;
- diction/Hán Việt balance;
- paragraph rhythm;
- narration stance;
- internal monologue compression;
- dialogue prose;
- description density;
- action/combat prose;
- cultivation/craft exposition prose;
- emotional understatement ở cấp câu chữ;
- repetition limits;
- Vietnamese adaptation filter.

Không lấy từ reference:

- mortal anchor;
- Dao/insight architecture;
- emotional arc;
- progression structure;
- world-scale reveal;
- protagonist temperament;
- plot/scene pattern.

Style Bible là direct writing contract.

## P4 — Character DNA Architect

Khóa desire, need, fear, wound, value, blind spot, contradiction, decision logic, speech, relationships, cultivation/combat identity, secrets và arc vector.

Reference prose không override Character DNA.

## P5 — Master Outline + Story Promise Architect

Khóa 3–5 Story Promises. Build saga map, protagonist/antagonist progression, cultivation progression, reveals, relationships, ending direction và flex zones.

**Không dùng Reference Prose Profile ở stage này.**

## P6 — Arc Outline Architect

Build arc question, start/end state, conflict ladder, character/faction moves, cultivation/resources, reveals, setup/payoff, Story Promise PAY windows, chapter intents và flex points.

**Không dùng Reference Prose Profile ở stage này.**

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
- continuity constraints;
- style constraints;
- hook nếu organic.

Style reminder chỉ được là **prose reminder**, tối đa 1–2 dòng, ví dụ:

- giữ câu trung bình làm trục, impact mới rút ngắn;
- nén expert reasoning;
- giảm adjective, ưu tiên động từ;
- exposition ngắn rồi quay lại action.

Không thêm story-DNA reminder từ reference.

Output destined for `chapters/NNNN/scene_plan.md`, chưa persist.

## P8 — Vietnamese Xianxia Writer

Direct style contract = story `bible/style_bible.md`.

Không tự prompt `viết giống Nhĩ Căn/Tiên Nghịch`; không copy wording, rhetorical frame, đoạn văn, scene shape hoặc translation syntax.

Core prose rules:

- prose Việt tự nhiên;
- câu trung bình làm trục;
- câu ngắn chỉ dùng khi cần impact/chốt trạng thái;
- câu dài giữ syntax Việt rõ;
- ưu tiên động từ/danh từ cụ thể hơn adjective stack;
- narrator được nói thẳng khi clarity cần;
- experienced MC chỉ nghĩ thành lời những gì ảnh hưởng quyết định;
- dialogue gọn, theo địa vị và DNA;
- miêu tả chọn chi tiết có chức năng;
- action/combat giảm exposition giữa đòn;
- cultivation/craft exposition: `state → relevant difference → action → result` khi phù hợp;
- cảm xúc ưu tiên body/action/silence hơn narrator labeling;
- tránh convert syntax, connector lặp, stock gesture, spectator shock, fragment spam.

Reference Prose Profile **không quyết định chuyện gì xảy ra trong chapter**.

Output destined for `chapters/NNNN/draft.txt`, chưa persist.

## P9 — Combined QC Reviewer

Đọc draft và tạo một report với ba phần.

### A. Continuity
Kiểm canon, timeline/geography, power/cultivation, items/resources/injury, knowledge, relationship/faction, POV, hard DNA contradiction.

### B. Story Promise
Kiểm promise target, `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`, concrete payoff, false pay, magnitude, drought.

### C. Style
Kiểm:

- sentence architecture/rhythm;
- fragment/cadence abuse;
- clause/connector repetition;
- diction/adjective density;
- paragraph rhythm;
- narration directness/recap;
- internal-monologue overlogging;
- dialogue sameness/Q&A cleanliness;
- description bloat;
- action/combat readability;
- exposition bloat;
- stock tics;
- Vietnamese convert syntax;
- Style Bible drift;
- direct imitation risk.

**Không chấm plot/Dao/emotional arc/world-scale/progression theo reference.**

Decision:

- `PASS` nếu không có BLOCKER/MAJOR cần sửa trong chapter;
- `REWRITE_REQUIRED` nếu có.

## P10 — Rewrite + Quick Recheck

Chỉ chạy khi P9 = `REWRITE_REQUIRED`.

Sửa candidate trong working memory. Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`.

Không “sửa cho giống reference”; chỉ sửa finding prose cụ thể theo Style Bible.

Nếu P9 = PASS, bỏ qua hoàn toàn rewrite và dùng draft nguyên văn làm final.

## P11 — Final + Memory Builder

Chuẩn bị final TXT, memory/ledger/summary, promise memory, manifest và batch audit nếu chapter đóng batch. Chưa write GitHub.

## P12 — Atomic Git Committer

1. create_blob cho mọi changed/new file;
2. create_tree từ chapter-start base tree;
3. create_commit với chapter-start HEAD làm parent;
4. update_ref exact story branch đúng một lần;
5. verify branch HEAD.

## P13 — Batch Auditor

Sau chapter cuối requested batch, kiểm artifact completeness, Combined QC PASS, memory current, continuity handoff, Story Promise payoff/drought và style caution.

Không có rolling audit/checkpoint Ch.3.
