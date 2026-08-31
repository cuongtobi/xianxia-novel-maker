# Reader Experience System

Tài liệu này định nghĩa các controller dùng để giữ truyện dài **cuốn, có nhịp sống và có chất tiên hiệp**, thay vì chỉ đúng canon và logic.

Các controller này không thay thế continuity. Chúng bổ sung một lớp khác: **độc giả vừa được hứa gì, vừa được trả gì, vừa trải qua kiểu chương nào và đang thiếu cảm giác gì**.

## 1. Story Promise Controller

### 1.1 Mục tiêu

Mỗi truyện khóa **3–5 lời hứa với độc giả** từ Genesis. Đây là lý do người đọc chọn và tiếp tục truyện.

Ví dụ dạng promise:

- family rise;
- cultivation wisdom;
- old ancestor second life;
- institutional conflict;
- loot dopamine;
- cultivation progression;
- corpse mystery;
- hidden conspiracy.

Tên promise trong artifact nên viết bằng tiếng Việt hoặc nhãn ngắn dễ hiểu; không cần dùng đúng ví dụ trên.

### 1.2 Promise contract

Mỗi promise phải có:

- `Promise ID` ổn định;
- lời hứa cụ thể;
- vì sao độc giả quan tâm;
- **PAY definition**: sự kiện nào thực sự được tính là trả promise;
- `advance ≠ pay`: thế nào chỉ là chuẩn bị;
- false pay: thứ trông giống payoff nhưng không đủ;
- drought warning: tối đa bao nhiêu chương không có PAY trước khi cảnh báo;
- escalation path: promise này lớn dần thế nào qua các saga.

### 1.3 PAY rule

Một chapter chỉ được đánh dấu `PAY` nếu độc giả nhận được **thành quả, reveal, trải nghiệm hoặc thay đổi trạng thái hữu hình** thuộc promise đó.

Ví dụ:

- nói về việc sẽ tu luyện = advance;
- thực sự sửa công pháp và hậu bối nhận kết quả = PAY cultivation wisdom;
- thấy một ánh sáng lạ = advance mystery;
- ký ức người chết làm thay đổi cách hiểu một vụ tử vong = PAY corpse mystery.

Không dùng checklist để ép mỗi chương phải trả mọi promise.

### 1.4 Drought rule

- Nếu promise chính vượt `drought warning`, Reader Retention Editor phải cảnh báo.
- Nếu **2–3 chương liên tiếp không PAY bất kỳ promise chính nào**, ít nhất `MINOR`; nếu đồng thời chapter chỉ setup/administration, có thể là `MAJOR`.
- Arc Outline phải có planned payoff windows, nhưng final chapter mới quyết định PAY thật.

### 1.5 Controller locations

Story Promise được khóa và dùng ở:

1. Genesis → `outline/master_outline.md`;
2. Arc → `outline/arcs/arc_NNN.md`;
3. Chapter plan → promise target;
4. QC → xác nhận PAY thật hay chỉ advance;
5. Memory → `reader_experience.md` lưu last paid;
6. Batch Audit → đo drought và promise balance.

---

## 2. Narrative Engine Controller

### 2.1 Narrative Engine là gì

Narrative Engine mô tả **cách một chương/cảnh tạo chuyển động**, không phải chủ đề của nó.

Hai chương đều nói về tu luyện nhưng một chương có thể là `training calibration`, chương kia là `ritual`, `combat` hoặc `mentor confrontation`.

Hai chương nói về gia tộc nhưng có thể là `Q&A meeting`, `negotiation`, `domestic`, `grief` hoặc `crisis response`.

### 2.2 Engine vocabulary gợi ý

Không phải enum đóng. Có thể thêm engine mới nếu mô tả chính xác hơn.

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
- social humiliation
- repair/build
- heist/infiltration
- travel discovery
- aftermath
- rescue
- moral choice
- competition

Mỗi chapter ghi:

- primary engine;
- secondary engine nếu có;
- dialogue geometry nếu hội thoại là trọng tâm.

### 2.3 Diversity rule

Trong rolling window 4 chương:

- nếu **3/4 chương dùng cùng primary engine** → `MAJOR pacing risk`;
- không được hạ severity chỉ vì topic khác nhau;
- chỉ được chấp nhận nếu arc cố ý tạo pattern lặp và mỗi lần có biến đổi hình thức/hậu quả rõ; lý do phải ghi trong QC.

Ví dụ không được coi là đa dạng:

- chương 4 audit nợ;
- chương 5 audit nhân sự;
- chương 6 audit thị trường.

Topic khác nhưng engine vẫn là audit/Q&A.

### 2.4 Geometry check

Ngoài tên engine, theo dõi:

- nhân vật ngồi hay di chuyển;
- ai chủ động đặt câu hỏi;
- thông tin đi một chiều hay va chạm;
- conflict được giải bằng lý lẽ, hành động, kỹ năng, may rủi, cảm xúc hay sức mạnh;
- scene có bị “A hỏi → B trả lời → MC kết luận” lặp lại không.

---

## 3. Rolling 3-Chapter Audit

### 3.1 Trigger

Trước final các chương chia hết cho 3: `3, 6, 9, 12, 15...`

### 3.2 Read

Đọc full:

- final N-2;
- final N-1;
- current rewrite candidate N.

Không chỉ đọc summary.

### 3.3 Check

So sánh ba chương về:

- opening shape;
- primary/secondary narrative engine;
- dialogue geometry;
- conflict solution;
- ending shape;
- rhetorical tics;
- paragraph cadence;
- hypothesis/verification loop;
- aphorism density;
- Story Promise PAY;
- Xianxia Experience;
- Emotional Residue.

### 3.4 Gate

Nếu repetition tạo `MAJOR`, current chapter N phải rewrite trước final. Hai chương trước đã final là canon; không sửa quá khứ chỉ để tạo variety.

Output:

`stories/<slug>/chapters/NNNN/rolling_3_chapter_audit.md`

---

## 4. Xianxia Experience Controller

World logic không tự động tạo fantasy experience. Controller này theo dõi riêng những trải nghiệm khiến truyện thật sự có cảm giác tu tiên/tiên hiệp.

### 4.1 Experience types

- cultivation payoff;
- wonder / awe;
- danger mang tính siêu nhiên;
- power gap được cảm nhận bằng hậu quả;
- mystical discovery;
- desirable resource: thứ độc giả cũng muốn nhân vật có;
- threshold crossing: bước qua một ngưỡng đời sống/cảnh giới/địa vị;
- dao/cultivation insight có tác dụng thật;
- magical craft: đan/khí/trận/phù được dùng như nghề thật;
- world-scale glimpse: thấy lớp thế giới lớn hơn hiện tại.

### 4.2 Rules

- Không quota cứng mỗi chương.
- Arc phải xác định trải nghiệm tiên hiệp trụ cột và payoff windows.
- Nếu nhiều chương chỉ có logistics, họp, giấy tờ, điều tra đời thường mà không có xianxia experience, Reader Retention Editor phải cảnh báo.
- Một `cultivation discussion` không được tính là `cultivation payoff` nếu không tạo thay đổi cảm nhận, năng lực, hiểu biết ứng dụng hoặc lựa chọn có giá.

---

## 5. Emotional Residue

### 5.1 Định nghĩa

Emotional Residue là thứ còn lại trong nhân vật hoặc người đọc sau một chương/cụm chương:

- quan hệ đổi cách nhìn nhau;
- self-image thay đổi;
- một nỗi sợ có khuôn mặt cụ thể;
- xấu hổ, tiếc nuối, thương, giận, biết ơn, ghen, nhẹ nhõm;
- một ký ức hoặc đồ vật trở nên mang nghĩa khác;
- một lựa chọn để lại cảm giác chưa giải quyết.

### 5.2 Rule

Không bắt mỗi chương phải có emotional climax.

Nhưng trong rolling window **3–5 chương** cần có ít nhất một thay đổi cảm xúc/quan hệ/self-image có bằng chứng. Nếu chỉ inventory/knowledge/cultivation đổi còn con người đứng yên, Reader Retention Editor phải cảnh báo.

Với truyện dùng người chết/ký ức/di vật, thỉnh thoảng phải có residue **không tối ưu sức mạnh**: ký ức tầm thường, lời chưa nói, attachment, hối hận, món nợ, sự thương tiếc hoặc lựa chọn khiến MC không được lợi ngay.

---

## 6. Human Irrationality Contract

Nhân vật thông minh vẫn là con người.

Cho phép và khuyến khích khi phù hợp DNA:

- bias;
- sĩ diện;
- sợ mất mặt;
- sentimental attachment;
- sunk-cost thinking;
- quá tin người quen;
- phản ứng phòng vệ khi bị chạm nỗi xấu hổ;
- chọn sai vì dữ liệu thiếu;
- trì hoãn vì sợ;
- impulsive kindness;
- irrational loyalty;
- ham thắng một tranh luận dù biết không có lợi.

Không dùng irrationality để biến nhân vật thành ngu nhằm chạy plot.

### Costly mistake rule

Đặc biệt với protagonist:

- không chỉ “đề xuất sai rồi người khác sửa trước khi mất gì”;
- theo từng arc phải có khả năng xuất hiện sai lầm thật, phù hợp blind spot, và có cost thực: tiền, thời gian, quan hệ, thương tích, cơ hội hoặc self-image;
- lỗi phải tạo learning hoặc scar, không reset như chưa xảy ra.

---

## 7. Positive Style Targets

Anti-AI blacklist chỉ nói cái gì không nên làm. Writer còn cần texture tích cực.

Tùy scene, có thể dùng tự nhiên một hoặc vài texture:

- awkward conversation;
- interruption;
- unfinished sentence;
- practical humor;
- embarrassment;
- irrational attachment;
- sensory messiness;
- misunderstanding;
- silence that changes meaning;
- spontaneous choice;
- failed joke;
- wrong first impression;
- physical inconvenience;
- asymmetrical emotion: một người thấy chuyện lớn, người kia coi bình thường.

Không biến danh sách này thành quota. Mục tiêu là cho prose có ma sát người thật, không phải “điền texture”.

---

## 8. Calibration Policy

Không auto-calibrate chỉ từ Chương 1–3.

Một calibration set hợp lệ cần:

- 4–6 đoạn đã final/được duyệt;
- đến từ **ít nhất 4 narrative engine khác nhau**;
- có tối thiểu narration, dialogue và một scene có áp lực hoặc wonder;
- không lấy toàn bộ từ cùng một batch opening nếu chưa có variety.

Mỗi batch chỉ dùng 2–3 sample phù hợp scene hiện tại làm reference. Xoay vòng sample để tránh style collapse.

Calibration học:

- nhịp;
- độ gần POV;
- độ thô/mượt của hội thoại;
- mật độ sensory;
- mức Hán Việt;
- cách cắt paragraph.

Không tái sử dụng câu chữ hoặc rhetorical frame đặc trưng của sample.

---

## 9. Reader Experience Memory

Mỗi story phải có:

`memory/reader_experience.md`

Memory này không phải canon. Nó là state về trải nghiệm đọc gần đây để planner/writer tránh lặp và biết promise nào đang đói payoff.

Bắt buộc cập nhật sau mỗi final:

- last_major_payoff;
- promise last-paid state;
- last_wonder_beat;
- last_emotional_hit;
- last_costly_mistake;
- recent_scene_engines;
- recent_dialogue_geometries;
- recent_ending_shapes;
- recent_rhetorical_tics;
- recent xianxia experiences;
- reader appetite / payoff debt.

Không dùng file này để override canon hoặc Character DNA.