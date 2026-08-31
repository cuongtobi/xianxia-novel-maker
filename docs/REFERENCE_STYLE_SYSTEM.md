# Reference Style System — Framework v3

Mục tiêu của hệ thống này là cho phép pipeline học **đặc điểm văn phong cấp cao** từ một hoặc nhiều tác phẩm tham chiếu rồi chuyển chúng thành **house style riêng của story**.

Reference Style **không** phải lệnh “viết y hệt tác giả/tác phẩm X”. Không copy câu chữ, đoạn văn, rhetorical frame đặc trưng, nhân vật, tình tiết hoặc cấu trúc cảnh cụ thể.

Luồng chuẩn:

`reference work → high-level style decomposition → reference style profile → story-specific Style Bible → project-owned calibration samples → Style Fingerprint QC`

---

# 1. Reference Style Profile được phép học gì

Chỉ học đặc điểm cấp cao như:

- POV và narrative distance;
- nhịp câu/đoạn;
- tỷ lệ hành động / quan sát / nội tâm / exposition;
- độ trực diện của prose;
- dialogue density và độ ngắn/dài;
- cách xử lý cultivation, combat, wonder, Dao/insight;
- cách chuyển từ đời thường sang siêu phàm;
- cách tạo emotional pressure/release;
- cách thể hiện power gap;
- cách mở rộng world scale;
- chapter movement và transition pattern ở mức trừu tượng;
- mức Hán Việt / cổ phong / hiện đại;
- texture nên giữ và lỗi nên lọc.

Không học/copy:

- câu chữ cụ thể;
- đoạn văn cụ thể;
- phép ví von độc đáo nhận diện được;
- catchphrase;
- tên riêng / pháp bảo / công pháp / worldbuilding IP;
- chuỗi beat hoặc plot riêng của reference;
- cùng một opening/ending frame lặp lại từ reference;
- các đoạn dài dùng làm few-shot trực tiếp.

---

# 2. Hai tầng profile

## 2.1 Reference Profile

File framework:

`docs/reference_profiles/<PROFILE>.md`

Đây là phân tích trừu tượng, không phải prose sample.

## 2.2 Story Style Bible

Mỗi story tạo:

`stories/<slug>/bible/style_bible.md`

Style Bible phải **adapt** profile theo:

- premise;
- Character DNA;
- Xianxia Density identity;
- target audience;
- pacing/retention requirement;
- tiếng Việt tự nhiên;
- những điều user muốn/không muốn.

Không được copy nguyên Reference Profile rồi coi là Style Bible hoàn chỉnh.

---

# 3. Reference Decomposition Schema

Mỗi profile nên mô tả:

1. narrative stance;
2. prose movement;
3. sentence/paragraph rhythm;
4. dialogue behavior;
5. cultivation prose;
6. combat prose;
7. emotional architecture;
8. Dao/philosophical writing;
9. world-scale reveal;
10. mortal/immortal contrast;
11. xianxia texture;
12. chapter pacing;
13. strengths to preserve;
14. weaknesses to filter;
15. adaptation rules;
16. QC red flags.

---

# 4. Adaptation Rule

Khi Reference Profile và story-specific need xung đột:

1. canon/Character DNA;
2. story premise/promise;
3. Xianxia Density + Reader Retention;
4. story Style Bible;
5. Reference Profile.

Reference chỉ là **input**, không phải source of truth cao hơn story.

Ví dụ: reference thiên bi kịch/lạnh nhưng story seed yêu cầu ấm áp gia tộc, pipeline chỉ học sự trực diện/cultivation texture/causal clarity, không ép toàn bộ truyện thành bi kịch.

---

# 5. Project-owned Calibration

Reference Profile không thay thế calibration.

Sau khi story có đủ final tốt và được chấp nhận, calibration phải dùng **chính prose của story hiện tại**:

- 4–6 đoạn;
- ít nhất 4 Narrative Engine khác nhau;
- không lấy câu/đoạn nguyên văn từ tác phẩm tham chiếu;
- học texture/rhythm từ output đã trở thành giọng riêng của project.

Reference mạnh nhất ở Genesis/Style Bible và early chapters. Về sau project-owned calibration phải dần chiếm ưu tiên.

---

# 6. Style Drift QC

Style Fingerprint Auditor kiểm hai loại drift:

## Drift away

- prose trở lại giọng AI sạch/đều;
- cultivation thành giải thích kỹ thuật khô;
- combat thành log skill;
- cảm xúc bị narrator gắn nhãn;
- Dao trở thành aphorism rỗng.

## Overfit to reference

- lặp nhiều stock gesture/cụm từ giống nguồn tham chiếu;
- cố bắt chước cú pháp dịch cứng;
- reuse rhetorical frame dễ nhận diện;
- mọi emotional peak cùng một kiểu;
- reference làm nhân vật mất DNA riêng.

Cả hai đều cần sửa.

---

# 7. Default profile cho xianxia mới

Framework hiện cung cấp:

`docs/reference_profiles/TIEN_NGHICH_HIGH_LEVEL_STYLE.md`

Profile này được dùng như **baseline cấp cao** cho truyện tiên hiệp/tu tiên mới nếu seed không override.

Nó không yêu cầu Writer “viết giống Nhĩ Căn”. Writer phải học các đặc điểm đã được trừu tượng hóa, đồng thời dùng Style Bible của story làm contract trực tiếp.

Story cũ không tự động nhận profile này nếu user không yêu cầu migrate/update.