# Style Fingerprint Report Template

> File đích: `stories/<slug>/chapters/NNNN/style_fingerprint_report.md`
> Reviewer mode: **Style Fingerprint Auditor**. Reviewer này tìm dấu vân tay lặp của model/prose, không chấm canon và không khen chung chung.
> Nếu story bật Reference Style, bắt buộc đọc `docs/REFERENCE_STYLE_SYSTEM.md`, profile được manifest chỉ định và `bible/style_bible.md`.

# Metadata

- Chapter:
- Candidate reviewed: draft / rewrite
- Style bible:
- Reference style enabled: yes/no
- Reference profile if enabled:
- Active project calibration samples:
- Recent finals compared:
- Result: PASS / REWRITE_REQUIRED

# 1. Rhetorical Fingerprints

Đếm hoặc trích ví dụ cụ thể nếu xuất hiện dày:

- `Không X. Mà Y.` / `Không phải X. Là Y.`:
- câu phủ định ngắn đứng riêng liên tiếp:
- câu ba vế cân xứng:
- `Đúng. Nhưng...` / `Vậy...` / `Cho nên...` dạng kết luận:
- aphorism / câu “đóng gói chân lý”:
- narrator kết đoạn bằng phán quyết:
- recap ngay sau sự kiện:
- forced philosophy:

# 2. Hypothesis-loop Fingerprint

- Có pattern `quan sát → giả thuyết → kiểm chứng → kết luận`?:
- Số lần lặp trong chapter:
- Recent chapters cũng dùng pattern này?:
- Có thể thay bằng hành động, sai lầm, cảm xúc, surprise hay information asymmetry không?:

Nếu engine lặp qua nhiều chapter, phối hợp với Reader Retention Report; không chữa chỉ bằng synonym.

# 3. Dialogue Fingerprint

- Q&A cleanliness: hội thoại có quá sạch, từng câu như phục vụ đúng một argument?:
- A hỏi → B trả lời → MC chốt có lặp?:
- Có interruption tự nhiên?:
- Có unfinished sentence / né tránh / nói lệch trọng tâm hợp DNA?:
- Nhân vật có cùng độ logic / cùng nhịp?:
- Có speech fingerprint riêng?:
- Có subtext hoặc emotional asymmetry?:

# 4. Paragraph & Sentence Shape

- Paragraph length quá đều?:
- Nhiều paragraph 1 câu có cùng chức năng?:
- Opening sentence frames lặp recent chapters?:
- Câu mở bằng tên MC quá dày?:
- Transition máy móc?:
- Sensory anchor có thật hay chỉ placeholder?:
- Câu trung bình/câu ngắn impact/câu dài accumulation có được dùng có chủ đích không?:

# 5. Lexical Tics

- từ/cụm lặp nội chương:
- từ/cụm lặp xuyên 3–10 chương:
- Hán Việt bị dày / quá sạch:
- filler ánh mắt/khóe môi/khí tức:
- stock gesture `sắc mặt biến đổi / ánh mắt lóe / hít sâu` quá dày?:
- connector `lập tức / ngay sau đó / đồng thời` thành nhịp convert?:
- cliché tiên hiệp:

# 6. Positive Texture Check

Không dùng như quota. Chỉ kiểm prose có ma sát người thật hay không.

Có xuất hiện tự nhiên một vài texture phù hợp?:

- awkward conversation;
- interruption;
- unfinished sentence;
- practical humor;
- embarrassment;
- irrational attachment;
- sensory messiness;
- misunderstanding;
- silence changing meaning;
- spontaneous choice;
- physical inconvenience;
- asymmetrical emotion.

Findings:

# 7. Reference Style Alignment — HIGH LEVEL ONLY

Chỉ điền nếu Reference Style bật.

## 7.1 Traits nên giữ theo Style Bible

- Prose có đủ trực diện/event-forward không?:
- Cultivation có chạm mechanism/body/perception/resource/consequence không?:
- Combat có tôn trọng power gap/resource/timing/cost không?:
- Dao/insight có lived experience hoặc concrete image support không?:
- Mortal/immortal contrast có organic không?:
- Emotional pressure có attachment + consequence/scar không?:
- World-scale reveal có revalue stakes không?:

## 7.2 Drift-away

Có dấu hiệu prose trôi khỏi house style thành:

- giọng AI sạch/đều;
- cultivation = giải thích kỹ thuật khô;
- combat = skill log;
- emotion = narrator label;
- Dao = slogan/aphorism;
- wonder = adjective spam;
- mọi scene cùng cadence?

- Drift-away severity:
- Required correction:

## 7.3 Overfit / imitation risk

Có dấu hiệu cố bắt chước reference bằng:

- câu/cụm từ dễ nhận diện;
- rhetorical frame lặp từ nguồn;
- cú pháp dịch/convert cứng;
- stock gesture giống nguồn dùng quá dày;
- pattern emotional/ending bị clone;
- plot/scene beat bị kéo gần reference không cần thiết?

- Overfit severity:
- Required de-reference fix:

**Không bao giờ sửa drift bằng cách copy câu chữ từ reference.** Chỉ quay về high-level trait trong story Style Bible.

# 8. Calibration Drift

- Active calibration samples:
- Samples thuộc narrative engines nào?:
- Có đang copy rhetorical shape từ sample?:
- Có dùng quá nhiều sample từ Ch.1–3/cùng một engine?:
- Project-owned calibration đã đủ mạnh để ưu tiên hơn Reference Profile chưa?:
- Rotation needed?:

# 9. Issue List

| ID | Severity | Location | Fingerprint / drift | Cross-chapter evidence | Required fix |
|---|---|---|---|---|---|

Severity: `MAJOR / MINOR / NOTE`.

`MAJOR` khi:

- dấu vân tay lặp đủ mạnh để độc giả cảm thấy nhiều chapter do cùng một máy sinh ra;
- prose drift-away rõ khỏi Style Bible;
- hoặc reference overfit khiến văn giống bản sao/cú pháp dịch của nguồn, dù nội dung mới.

# 10. Gate

- MAJOR remaining:
- Dominant AI-like fingerprint removed?:
- Reference high-level alignment healthy?: yes/no/NA
- Reference overfit absent?: yes/no/NA
- Project-owned calibration respected?: yes/no/NA
- Dialogue geometry sufficiently human?:
- Ready for aggregate QC: yes/no
