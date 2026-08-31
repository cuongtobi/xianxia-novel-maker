# Xianxia Density Controller — Framework v3

Tài liệu này là contract bắt buộc cho **truyện mới** dùng framework v3. Nó không retroactively áp vào story branch cũ nếu story đó chưa được user yêu cầu migrate.

Mục tiêu: ngăn tình trạng truyện có tên cảnh giới, linh thạch, công pháp, linh điền nhưng trải nghiệm thực tế vẫn có thể thay toàn bộ bằng tiền, hợp đồng, ruộng và kỹ thuật phàm tục mà gần như không đổi drama.

**Retention ≠ Genre Density.**

- Retention Controllers hỏi: chapter có cuốn, có payoff, có heat, có fantasy desire không?
- Xianxia Density hỏi: conflict, lựa chọn, hậu quả và cảm giác thế giới có thực sự chỉ có thể tồn tại trong một tu tiên giới không?

Không dùng controller này để spam danh từ Hán Việt, aura, dị tượng hoặc combat. Chất tiên hiệp phải đến từ **cơ chế siêu nhiên có nhân quả, power/cultivation consequence, wonder, resource law và thế giới quan của tu sĩ**.

---

# 1. Ba tầng Xianxia Density

## 1.1 Ambient Xianxia

Ambient trả lời: **nếu bỏ plot chính, môi trường sống có vẫn cho thấy đây là tu tiên giới không?**

Ví dụ hợp lệ:

- thần thức được dùng như giác quan;
- linh khí có hướng, nhiệt, độ thuần, chu kỳ;
- pháp khí/trận pháp/phù/linh thực/yêu thú có mặt như công cụ đời sống;
- cảnh giới làm thay đổi quyền đi lại, tuổi thọ, lao động, địa vị, giá trị con người;
- tu sĩ và phàm nhân có nhịp sống khác do luật tu luyện;
- địa hình/tài nguyên bị định hình bởi địa mạch, linh triều, bí cảnh, yêu khí;
- injury/cultivation state ảnh hưởng hành vi thường nhật.

Không tính Ambient nếu chỉ đổi danh từ:

- tiền → linh thạch;
- ruộng → linh điền;
- thuốc → đan dược;
- chủ đất → tu tiên gia tộc;

nhưng cơ chế và hậu quả vẫn hoàn toàn phàm tục.

## 1.2 Active Xianxia

Active trả lời: **yếu tố tu tiên có trực tiếp gây ra hoặc thay đổi quyết định/hậu quả của scene không?**

Một Active beat cần có ít nhất một causal chain thực:

`supernatural law/state → constraint/opportunity → character decision → observable consequence`

Ví dụ:

- trận dẫn thủy lệch địa khí → linh cốc hút tạp khí → phải chọn sửa trận hay hy sinh mùa vụ;
- thần thức bị thương → MC không thể dò toàn khu → buộc supporting cast điều tra;
- công pháp tương khắc → tu sĩ không thể chỉ “cố hơn” → phải đổi chu thiên/tài nguyên;
- yêu thú lột xác theo linh triều → cửa sổ săn/né xuất hiện;
- bí cảnh mở theo nhịp thiên tượng → logistics, alliance và deadline thay đổi;
- power gap khiến một lời hứa/đe dọa có trọng lượng khác vì người mạnh thật sự có khả năng cưỡng chế.

Không tính Active nếu yếu tố tu tiên chỉ trang trí hoặc giải thích sau khi quyết định vốn đã hoàn tất.

## 1.3 Aspirational Xianxia

Aspirational trả lời: **chapter có làm nhân vật/độc giả muốn chạm tới một tầng tu tiên cao hơn không?**

Có thể là:

- cảnh giới;
- linh mạch;
- bí cảnh/động thiên;
- pháp bảo;
- dị hỏa;
- công pháp/truyền thừa;
- giống linh thực;
- đan lô/trận bàn;
- huyết mạch/căn cốt;
- quyền vào một vùng tu luyện;
- khả năng phi hành, thần thức, lĩnh vực, luyện khí/luyện đan;
- một địa phương hoặc hiện tượng cho thấy thế giới lớn hơn nhiều so với hiện tại.

Aspirational beat phải có **proof of desire**: sensory proof, status proof, capability proof hoặc future-use image. Chỉ liệt kê tên vật phẩm không đủ.

---

# 2. Xianxia Beat Strength

Mỗi chapter ghi `xianxia_peak`:

- `X0 — skin only`: hầu hết chỉ có danh từ/skin tu tiên; conflict thay bằng bối cảnh phàm tục vẫn chạy gần nguyên vẹn.
- `X1 — ambient`: thế giới có texture tu tiên rõ, nhưng yếu tố siêu nhiên chưa quyết định outcome lớn.
- `X2 — active`: ít nhất một Active Xianxia beat làm đổi lựa chọn/hậu quả thật.
- `X3 — strong`: có beat đáng nhớ thuộc cultivation change, wonder, supernatural danger, mystical discovery, power display, desirable resource, threshold crossing, magical craft hoặc dao insight có consequence.

`X3` không đồng nghĩa combat hay đại cảnh giới. Một pháp khí cấp thấp được sửa khiến cả mảnh linh điền đổi trạng thái cũng có thể là X3 nếu được setup, có mechanism và consequence đủ mạnh.

---

# 3. Replaceability Test

Reader Retention Editor phải hỏi:

> **Nếu đổi linh thạch→tiền, linh điền→ruộng, công pháp→kỹ thuật, tông môn→công ty/gia tộc phàm tục, chapter này mất bao nhiêu causal logic?**

Trả lời:

- `LOW_REPLACEABILITY` — bỏ tu tiên là chapter gãy đáng kể; tốt.
- `MEDIUM_REPLACEABILITY` — một phần plot vẫn chạy nhưng nhiều constraint/consequence thay đổi; chấp nhận được.
- `HIGH_REPLACEABILITY` — chỉ đổi danh từ là chapter vẫn gần như nguyên vẹn; rủi ro genre dilution.

Rule:

- một chapter `HIGH_REPLACEABILITY` không tự động fail nếu là domestic/grief/aftermath có giá trị người thật;
- `3 consecutive HIGH_REPLACEABILITY` → `MAJOR genre dilution risk`;
- rolling 3 mà cả ba chỉ có `X0/X1` và không có Active Xianxia causal beat → `MAJOR` trừ explicit arc-level decompression waiver.

---

# 4. Rolling Density Rules

## 4.1 Rolling 3

Trong mọi rolling 3 chapter của truyện tiên hiệp/tu tiên:

- phải có ít nhất **1 Active Xianxia causal beat** (`X2+`);
- không được để cả ba chapter chỉ dùng danh từ tu tiên trong conflict vốn hoàn toàn phàm tục;
- nếu cả ba là `HIGH_REPLACEABILITY` → `MAJOR`.

Waiver chỉ hợp lệ cho intentional decompression/grief/romance/aftermath window đã được Arc Outline ghi trước hoặc phát sinh organic sau một peak lớn. Waiver phải nêu chapter kế tiếp dự kiến trả lại density, không dùng để kéo dài vô hạn.

## 4.2 Rolling 5

Trong mọi rolling 5 chapter:

- tối thiểu **2 chapter có Active Xianxia** (`X2+`);
- tối thiểu **1 chapter có Strong Xianxia beat** (`X3`);
- tối thiểu một beat phải tạo `Aspirational Xianxia` hoặc wonder/desire tương đương;
- nếu 5 chapter chủ yếu là admin/logistics/economy/relationship mà luật tu tiên không đổi causal chain → `MAJOR genre dilution risk`.

Không ép 2/5 thành combat. Active beat có thể đến từ cultivation, craft, supernatural ecology, power hierarchy, mystical discovery, resource law, ritual, injury, breakthrough, terrain, formation hoặc dao consequence.

---

# 5. Cultivation Presence Contract

“Có cultivation” không chỉ là nhân vật nói cảnh giới hoặc ngồi vận công.

Một cultivation beat mạnh nên thể hiện ít nhất một:

- body/kinh mạch/đan điền/thần hồn thay đổi;
- perception thay đổi;
- thuật pháp/pháp khí dùng khác đi;
- resource consumption/cost;
- failure mode;
- social meaning của realm;
- lựa chọn chiến thuật/đời sống bị realm constraint;
- breakthrough preparation/threshold;
- insight làm thay đổi cách hành động.

`talking about cultivation` hoặc `listing technique names` không được tính Active/Strong nếu không có consequence.

---

# 6. Ancient/High-Realm POV Aura

Nếu protagonist từng ở cảnh giới cao, sống lâu hoặc có trải nghiệm vượt xa môi trường hiện tại, prose phải thỉnh thoảng giữ **scale memory** mà không biến thành khoe lore.

Có thể thể hiện qua:

- nhận ra cấu trúc cấp thấp là biến thể của đại trận/pháp bảo lớn từng thấy;
- đọc dấu vết địa mạch/yêu thú/linh triều mà người địa phương không biết;
- nhớ một failure/cost từ thời đại khác;
- so sánh power hierarchy bằng consequence, không bằng adjective;
- biết một kiến thức cũ nhưng phát hiện nó đã lỗi thời;
- nhìn thấy potential của tài nguyên bị coi là rác;
- hiểu social meaning của breakthrough sâu hơn người trẻ.

Mục tiêu: giữ cảm giác nhân vật thật sự thuộc tu tiên giới và từng đi qua những tầng cao hơn, không chỉ là “chuyên gia quản trị có tuổi”.

Không bắt buộc mỗi chapter phải có high-realm aura. Nếu xuất hiện liên tục thành exposition flex, Style/Retention phải cảnh báo.

---

# 7. Planning Contract

## Genesis / Master Outline

Phải khóa:

- `Xianxia identity`: loại trải nghiệm tu tiên làm truyện này khác truyện phàm;
- `Active Xianxia causal sources`: linh mạch, công pháp, ecology, bí cảnh, power hierarchy, craft, thiên tượng... phù hợp premise;
- `Aspirational ladder`: thứ độc giả sẽ muốn nhìn nhân vật đạt được ở từng saga;
- `Strong Xianxia windows`: không để spectacle/wonder/breakthrough bị backload quá xa;
- các loại conflict dễ bị `HIGH_REPLACEABILITY` và cách chống dilution.

## Arc Outline

Mỗi chapter intent row nên ghi:

- `xianxia_peak target: X0–X3`;
- Ambient target nếu relevant;
- Active causal beat nếu relevant;
- Aspirational/desire beat nếu relevant;
- Replaceability risk;
- rolling-3/5 density pre-check.

Arc không được lên lịch 10–15 chapter đầu chỉ toàn debt/admin/training explanation rồi mới bắt đầu wonder/danger/craft nếu premise là progression xianxia.

## Scene Plan

Trước draft phải trả lời:

- yếu tố nào khiến chapter chỉ có thể tồn tại trong tu tiên giới?
- supernatural law/state nào có causal consequence?
- nếu chapter cố ý `X0/X1`, rolling window có còn hợp lệ không?
- có đang dùng cultivation như cơ chế hay chỉ dùng danh từ?

---

# 8. Reader Retention QC Integration

Reader Retention Report bắt buộc thêm section `Xianxia Density`:

- Ambient evidence:
- Active causal beat(s):
- Aspirational beat:
- `xianxia_peak: X0/X1/X2/X3`;
- Replaceability: LOW / MEDIUM / HIGH;
- Previous 2 peaks:
- Previous 4 peaks:
- Rolling-3 active requirement passed?:
- Rolling-5 `2×X2+ + 1×X3` requirement passed?:
- Genre dilution finding:

Severity:

- current chapter `X0` → NOTE/WATCH tùy context;
- 3 consecutive `HIGH_REPLACEABILITY` → MAJOR;
- rolling 3 không có Active Xianxia → MAJOR;
- rolling 5 thiếu 2 Active hoặc thiếu 1 Strong → MAJOR;
- fake density bằng danh từ/infodump không được dùng để clear finding.

---

# 9. Reader Experience Memory

Sau mỗi final lưu tối thiểu:

- `xianxia_peak` của chapter;
- Ambient / Active / Aspirational summary;
- replaceability;
- recent 5 xianxia peaks;
- chapters since last `X2+`;
- chapters since last `X3`;
- last strong cultivation/wonder/danger/discovery/craft/resource beat;
- current `genre_density_debt`;
- high-realm aura last used nếu protagonist thuộc archetype đó.

Memory không biến thành canon; nó chỉ giữ production pattern.

---

# 10. Rolling Audit + Batch Audit

## Rolling 3

Ngoài engine/geometry/style, kiểm:

- 3 chapter có bao nhiêu Active Xianxia beat;
- replaceability pattern;
- có phải topic thay đổi nhưng mọi conflict vẫn có thể chuyển sang bối cảnh phàm không;
- candidate hiện tại có cần tăng causal xianxia thay vì chỉ thêm lore.

## Batch 5

Báo cáo:

- peak sequence, ví dụ `X1 → X2 → X1 → X3 → X2`;
- Active count;
- Strong count;
- Aspirational beats;
- HIGH_REPLACEABILITY count;
- strongest genre-defining moment;
- genre density debt sang batch sau.

Batch không được PASS Reader-Reward Gate nếu rolling rules có MAJOR chưa xử lý.

---

# 11. Rewrite Rule

Nếu thiếu density:

**Không sửa bằng cách rắc thêm “linh khí / thiên địa / pháp bảo / đạo vận”.**

Sửa causal structure:

- cho địa mạch/cultivation/injury/power gap tạo constraint thật;
- đổi asset phàm thành resource có supernatural behavior và cost;
- cho craft/trận/phù/đan/yêu thú tác động outcome;
- mở aspiration qua capability/status/sensory proof;
- để một realm/technique thay cách nhân vật có thể hành động;
- dùng wonder/danger/discovery có mechanism;
- nếu MC từng ở cảnh giới cao, cho scale memory hoặc kiến thức cũ va với hiện tại.

Genre density phải đến từ **nhân quả**, không từ vocabulary.

---

# 12. Non-Goals

Controller này không yêu cầu:

- combat mỗi 2–3 chapter;
- breakthrough liên tục;
- buff miễn phí;
- dị tượng phô trương;
- spam pháp bảo/cảnh giới;
- power fantasy domination;
- giảm domestic/emotional chapters;
- biến mọi sinh hoạt thành phép thuật.

Một chapter gia đình hoàn toàn có thể `X0/X1` và rất hay. Vấn đề chỉ xuất hiện khi nhiều chapter liên tiếp khiến người đọc quên rằng đây là một truyện tu tiên.
