# Retention Controllers v3

Tài liệu này bổ sung sáu cơ chế bắt buộc để ngăn tình trạng **PASS kỹ thuật nhưng trải nghiệm đọc phẳng**. Các rule dưới đây áp dụng cho Genesis, Arc planning, per-chapter Reader Retention QC, Rolling Audit, Reader Experience Memory và Batch Audit.

Mục tiêu không phải ép truyện thành power fantasy hoặc cliffhanger liên tục. Mục tiêu là phân biệt rõ:

- đúng logic với đáng đọc;
- thay đổi topic với thay đổi cách vận hành drama;
- payoff nhỏ với payoff thật sự làm độc giả thỏa mãn;
- competence hấp dẫn với competence frictionless;
- scarcity với fantasy desire;
- nhịp yên có chủ đích với flatness;
- ending hook với giá trị nội tại của chapter.

---

# 1. Dramatic Geometry Controller

## 1.1 Vì sao cần

`Narrative Engine` trả lời chapter chuyển động bằng loại hoạt động nào: audit, negotiation, combat, repair-build, training calibration...

Nhưng hai chapter có engine khác nhau vẫn có thể tạo cùng trải nghiệm nếu cùng geometry, ví dụ:

`có vấn đề → mọi người trình bày → MC hỏi → MC phân tích → thử nhỏ → MC kết luận`.

Dramatic Geometry theo dõi **cấu trúc quyền lực và chuyển động của conflict**, không chỉ topic hoặc label engine.

## 1.2 Geometry signature

Mỗi chapter phải ghi tối thiểu:

- `pressure_source`: áp lực đến từ ai/cái gì;
- `decision_locus`: ai thực sự phải chọn;
- `movement_mode`: discussion / physical task / pursuit / discovery / ritual / conflict / mixed;
- `information_flow`: ai biết, ai hỏi, ai che, ai hiểu sai;
- `opposition_shape`: người đối đầu / môi trường / deadline / bản thân / institution / unknown;
- `resolution_mode`: argument / test / sacrifice / force / bargain / discovery / escape / cooperation / failure / other;
- `reversal_type`: knowledge / status / resource / relationship / physical / none;
- `kinetic_level`: low / medium / high.

Có thể thêm story-specific fields nếu cần.

## 1.3 Similarity rule

Không yêu cầu geometry khác hoàn toàn mỗi chapter.

Cảnh báo khi rolling window cho thấy cùng một pattern cốt lõi lặp lại dù engine label khác:

- `3 consecutive chapters` có cùng `decision_locus + information_flow + resolution_mode` → `WATCH`;
- `3/4 chapters` có cùng geometry signature cốt lõi → `MAJOR pacing risk`;
- đổi bối cảnh hoặc topic **không** đủ để xóa finding nếu conflict vẫn vận hành giống nhau.

Ví dụ cần bắt:

- audit bằng bàn sổ;
- training bằng hỏi đáp;
- negotiation bằng hỏi đáp;

nếu cả ba đều thực chất là `others present facts → MC diagnoses → MC gives clean answer`.

## 1.4 Fix rule

Không synonym-spin.

Nếu geometry lặp, sửa một hoặc nhiều trục:

- chuyển decision locus sang supporting cast;
- làm thông tin bất cân xứng;
- cho hành động vật lý chen vào;
- để giải pháp thất bại/partial;
- buộc đổi leverage;
- thêm misunderstanding hợp DNA;
- để hậu quả đến trước kết luận;
- thay resolution mode.

---

# 2. Payoff Magnitude

## 2.1 Trạng thái mới

Story Promise không còn chỉ dùng `UNTOUCHED / ADVANCE / PAY`.

Dùng:

- `UNTOUCHED` — không chạm promise;
- `ADVANCE` — tăng setup, pressure, clue hoặc chuẩn bị;
- `PAY_MINOR` — payoff thật nhưng phạm vi nhỏ, tạo kết quả cảm nhận được;
- `PAY_MAJOR` — payoff đáng kể, trả rõ lý do độc giả theo promise;
- `PAY_ARC` — payoff cấp arc, đóng hoặc tái định nghĩa một objective/threshold lớn.

## 2.2 Định nghĩa

### PAY_MINOR

Có state/reveal/result thật, nhưng scope nhỏ.

Ví dụ:

- giảm hao linh khí đo được;
- kiếm được khoản tiền nhỏ đầu tiên;
- một clue mới thu hẹp mystery;
- một quan hệ chuyển một nấc.

### PAY_MAJOR

Tạo thay đổi độc giả thực sự cảm thấy “đã được trả”.

Ví dụ:

- một hậu bối breakthrough;
- mở được nguồn thu đáng kể;
- giành tài nguyên ai cũng muốn;
- reveal làm đổi mô hình hiểu biết;
- thắng một conflict có cost;
- family status thay đổi rõ.

### PAY_ARC

Đóng hoặc đổi trạng thái mục tiêu cấp arc.

Ví dụ:

- trả/restructure được nút nợ chính;
- first Trúc Cơ của arc;
- chiếm/khai thác được linh mạch mục tiêu;
- quan hệ trung tâm đạt threshold mới.

## 2.3 Reward score

Để audit dễ so sánh:

- `PAY_MINOR = 1`;
- `PAY_MAJOR = 2`;
- `PAY_ARC = 3`.

Score không thay thế phán đoán biên tập.

## 2.4 Drought rule

Theo dõi **hai loại nợ riêng**:

1. `pay_drought`: số chapter từ bất kỳ PAY thật gần nhất;
2. `major_payoff_debt`: số chapter từ `PAY_MAJOR` hoặc `PAY_ARC` gần nhất cho core promise.

Không được dùng chuỗi `PAY_MINOR` để giả rằng truyện đã trả đủ một core promise đang đói `PAY_MAJOR`.

Master Outline và Arc Outline phải nêu:

- PAY definition;
- mức PAY tối thiểu ở từng planned window;
- major payoff windows;
- false-pay examples.

Batch Audit phải tổng hợp reward score và chỉ ra nếu batch toàn `PAY_MINOR` nhưng thiếu payoff lớn.

---

# 3. Competence Friction Meter

## 3.1 Mục tiêu

MC thông minh, cổ lão, thiên tài hoặc có hệ thống không cần giả ngu. Nhưng competence nếu luôn đúng, luôn được xác nhận và luôn không mất gì sẽ làm conflict phẳng.

Meter theo dõi **kết quả của các competence conversion**, tức mỗi lần MC dùng tri thức/kỹ năng/quyền lực để giải quyết một vấn đề thật.

## 3.2 Outcome labels

Mỗi conversion chính ghi một nhãn:

- `CLEAN_WIN` — nhận định đúng, thực thi đúng, gần như không cost ngoài dự kiến;
- `COSTLY_WIN` — đúng nhưng phải trả cost thật;
- `PARTIAL` — chỉ giải được một phần hoặc tạo vấn đề mới;
- `WRONG_MODEL` — logic/kiến thức đầu tiên sai hoặc lỗi thời;
- `DEPENDENT_ON_OTHER` — chỉ thành công nhờ agency/knowledge/innovation của người khác;
- `FAILURE` — không đạt objective;
- `NO_CONVERSION` — chapter không dùng competence để giải quyết vấn đề chính.

## 3.3 Rolling rule

- `3 consecutive competence conversions = CLEAN_WIN` → `WATCH`;
- `4/5 recent competence conversions = CLEAN_WIN` → `MAJOR flattening risk`;
- nếu MC được người khác sửa trước khi hậu quả chạm tới mình, vẫn tính gần với `CLEAN_WIN`, không được giả thành mistake;
- một chosen cost mà MC chủ động biết trước không tự động là `costly mistake`.

Exception: comfort/power-fantasy arc có thể giữ nhiều CLEAN_WIN nếu promise của truyện là domination, nhưng phải bù bằng ít nhất một trong: scale escalation, enemy adaptation, hidden cost, relationship friction, resource pressure hoặc mystery uncertainty.

## 3.4 Good friction

Ưu tiên sai lầm cấp cao:

- đúng kỹ thuật, sai về consent;
- biết quy luật cũ nhưng market/world đã đổi;
- giải quyết local problem nhưng làm xấu political position;
- thắng bằng sức mạnh nhưng lộ vị trí;
- tối ưu tài nguyên nhưng đụng giá trị tình cảm;
- phán đúng người nhưng sai timing;
- cần supporting cast hoàn tất phần mình không biết.

Không làm MC ngu chỉ để cân bằng meter.

---

# 4. Aspiration Controller

## 4.1 Tách scarcity khỏi desire

`Scarcity` trả lời: nhân vật đang thiếu gì / sợ mất gì.

`Aspiration` trả lời: độc giả và nhân vật **muốn có gì** vì nó đẹp, mạnh, hiếm, mở khóa khả năng hoặc đổi địa vị.

Nợ, đói, ruộng xấu, thương thế, pháp khí hỏng tạo pressure nhưng không tự động tạo fantasy desire.

## 4.2 Aspiration beat fields

Mỗi beat đáng kể ghi:

- `object_of_desire`: tài nguyên/cảnh giới/nghề/địa vị/địa điểm/khả năng;
- `why_desirable`: vì sao nhân vật và độc giả muốn nó;
- `sensory_or_status_proof`: bằng chứng khiến nó đáng ham;
- `distance_to_acquire`: near / medium / far;
- `cost_or_gate`: phải trả gì;
- `future_use_image`: có được rồi sẽ làm được gì;
- `status`: glimpse / target / contested / acquired / used / lost.

## 4.3 Rolling rule

Trong progression xianxia:

- rolling 5 chapter phải có ít nhất một aspiration beat đáng nhớ **hoặc** một wonder beat đủ mạnh tạo fantasy desire;
- `5 chapters` chỉ có scarcity/admin/problem-fixing mà không có thứ gì đáng thèm → `MAJOR appetite risk`;
- resource chỉ được tính aspiration nếu prose cho thấy tại sao nó đáng muốn, không phải chỉ ghi tên vào inventory.

Aspiration có thể là:

- linh mạch;
- bí cảnh;
- lò đan;
- pháp khí;
- giống linh thực;
- truyền thừa;
- địa vị;
- năng lực sau breakthrough;
- một cảnh giới/địa phương khiến nhân vật nhìn thấy chân trời lớn hơn.

---

# 5. Heat Curve

## 5.1 Heat không chỉ là combat

Heat đo **cường độ trải nghiệm**, gồm:

- danger;
- wonder;
- power display;
- emotional rupture;
- reversal;
- threshold crossing;
- high-stakes choice;
- reveal đủ mạnh;
- chase/combat/survival.

## 5.2 Heat level

Mỗi chapter ghi `peak_heat`:

- `H0 — quiet`: setup/decompression, ít áp lực;
- `H1 — active`: tension/chuyển động rõ nhưng chưa có beat mạnh;
- `H2 — strong`: ít nhất một beat intensity/wonder/danger/reversal đủ rõ để nhớ;
- `H3 — peak`: threshold lớn, combat/reveal/wonder/emotional rupture cấp arc/batch.

Không cần chapter nào cũng H2/H3.

## 5.3 Rolling-5 rule

- rolling 5 chapter phải có ít nhất một `H2+`;
- nếu `max(peak_heat) < H2` trong 5 chapter → `MAJOR flatness risk`;
- nếu có quá nhiều H3 liên tiếp, cảnh báo saturation; heat curve phải có contrast;
- quiet/bridge chapter hợp lệ nếu nằm trong curve có chủ đích và trả emotion/meaning/texture.

Batch Audit phải vẽ chuỗi heat dạng:

`H1 → H0 → H1 → H2 → H1`

và chỉ ra peak có đúng promise/arc không.

---

# 6. Binge Test

Binge Test là phần bắt buộc ở cuối Reader Retention QC, trước aggregate gate.

## 6.1 Câu 1

**“Khoảnh khắc sướng nhất chương là gì?”**

Phải trả lời bằng một khoảnh khắc cụ thể đã xảy ra trong chapter.

Không được trả lời bằng:

- hook cuối;
- thứ hứa sẽ xảy ra chapter sau;
- “worldbuilding hay” chung chung;
- setup chưa có result.

Có thể là:

- cultivation payoff;
- reveal;
- character win;
- emotional release;
- competence flex;
- resource acquisition;
- wonder;
- revenge/status reversal;
- craft success;
- một lựa chọn rất đúng DNA.

Nếu không tìm được khoảnh khắc nào, ghi `NONE` và ít nhất `MAJOR retention risk` trừ khi chapter là decompression có emotional payoff rất rõ.

## 6.2 Câu 2

**“Nếu bỏ ending hook, bản thân chương này có đủ đáng đọc không?”**

Trả lời:

- `YES` — chapter có giá trị nội tại rõ;
- `WEAK` — có một số giá trị nhưng phần lớn sức kéo đến từ hook;
- `NO` — bỏ hook thì chapter chủ yếu là setup/bridge.

`NO` → `MAJOR` và rewrite required, trừ khi có explicit structural waiver do Arc Outline ghi trước; waiver không được dùng hai chapter liên tiếp.

`WEAK` → WATCH/MINOR hoặc MAJOR tùy promise drought/heat/payoff context.

## 6.3 Bingeability không đồng nghĩa cliffhanger

Chapter có thể không cliffhanger vẫn bingeable nếu có:

- payoff đáng nhớ;
- state change;
- emotional residue;
- wonder;
- new desire;
- strong consequence;
- một câu hỏi mới sinh tự nhiên từ thay đổi vừa xảy ra.

---

# 7. Integration Rules

## 7.1 Genesis / Master Outline

Phải khóa:

- Story Promise + Payoff Magnitude definitions;
- major payoff windows;
- aspiration identity;
- heat identity/expected curve theo saga;
- protagonist competence friction sources.

## 7.2 Arc Outline

Phải có:

- planned PAY magnitude;
- geometry map/check;
- competence-friction opportunities;
- aspiration beats;
- heat curve;
- planned Binge Test risk ở bridge/quiet chapters nếu có.

## 7.3 Scene Plan

Phải biết:

- intended geometry;
- intended payoff magnitude;
- competence conversion nếu có;
- aspiration/heat target nếu relevant;
- chapter intrinsic reward, không chỉ ending hook.

Không over-plan prose.

## 7.4 Reader Retention Report

Bắt buộc kiểm cả sáu controller.

Bất kỳ `MAJOR` nào chưa sửa → aggregate không PASS.

## 7.5 Rolling 3-Chapter Audit

Dùng để phát hiện sớm:

- geometry lặp;
- CLEAN_WIN streak;
- toàn PAY_MINOR;
- aspiration drought đang hình thành;
- heat phẳng;
- binge value yếu lặp lại.

Heat rolling rule chính thức vẫn tính 5 chapter; rolling-3 chỉ cảnh báo sớm.

## 7.6 Reader Experience Memory

Phải giữ đủ recent data để tính:

- geometry signatures;
- payoff magnitude + major payoff debt;
- competence outcomes;
- aspiration beats;
- peak heat;
- Binge Test result.

## 7.7 Batch Audit

Batch PASS không chỉ vì artifact đầy đủ/continuity đúng.

Batch phải kiểm:

- geometry diversity;
- PAY magnitude distribution;
- competence friction;
- aspiration coverage;
- rolling-5 heat;
- Binge Test health.

Nếu batch kỹ thuật sạch nhưng các controller cho `MAJOR` chưa giải quyết → `REPAIR_REQUIRED`, không PASS.

---

# 8. Severity Summary

Các trigger mặc định:

| Controller | WATCH | MAJOR |
|---|---|---|
| Dramatic Geometry | 3 consecutive near-same geometry | 3/4 same core geometry |
| Payoff Magnitude | core promise chỉ có ADVANCE/PAY_MINOR kéo dài | major payoff debt vượt planned window |
| Competence Friction | 3 clean conversions liên tiếp | 4/5 clean conversions |
| Aspiration | desire beat yếu/xa dần | 5 chapter chỉ scarcity/admin, không aspiration/wonder đủ mạnh |
| Heat Curve | 3–4 chapter liên tiếp H0–H1 | rolling 5 không có H2+ |
| Binge Test | `WEAK` | `NONE` ở câu 1 hoặc `NO` ở câu 2 nếu không có waiver hợp lệ |

Severity có thể tăng nếu nhiều controller cùng báo cùng một root cause.

Không hạ `MAJOR` chỉ vì continuity/style đều PASS.

---

# 9. Core Principle

Framework phải tối ưu đồng thời hai lớp:

1. **Technical correctness** — canon, logic, POV, state, style, consistency.
2. **Reader reward** — desire, payoff, friction, escalation, wonder, emotional consequence, chapter value.

`PASS kỹ thuật ≠ PASS trải nghiệm đọc.`
