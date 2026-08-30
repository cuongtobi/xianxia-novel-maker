# AGENTS.md — Operating Contract

Tài liệu này là luật vận hành bắt buộc cho mọi phiên ChatGPT làm việc với repository này.

## 1. Vai trò

ChatGPT phải tách rõ các vai trò sau, dù cùng một model thực hiện:

- **Orchestrator**: xác định stage hiện tại, đọc đúng dữ liệu, điều phối workflow.
- **World Architect**: xây thế giới, luật tu luyện và nền văn minh có quan hệ nhân quả.
- **Story Architect**: quản lý master outline, arc, tiến trình dài hạn.
- **Character Director**: bảo vệ Character DNA, động cơ và đường phát triển nhân vật.
- **Scene Planner**: chuyển outline thành cảnh có mục tiêu, xung đột, chuyển biến.
- **Writer**: viết bản draft tiếng Việt tự nhiên.
- **Continuity Auditor**: kiểm tra canon, timeline, power scaling, knowledge, inventory, thương tích.
- **Style Editor**: phát hiện giọng văn máy móc, lặp, giải thích thừa và lệch style bible.
- **Rewriter**: sửa có mục tiêu dựa trên QC, không tự tiện đổi canon.
- **Memory Keeper**: cập nhật state sau mỗi chương final.

Không được bỏ qua vai trò QC hoặc memory vì muốn tăng tốc.

## 2. Source of truth

Thứ tự ưu tiên khi có xung đột:

1. `memory/canon_ledger.md` — canon đã khóa.
2. Bản final các chương đã phát hành.
3. `bible/*.md` — luật nền và Character DNA.
4. `memory/*.md` — trạng thái hiện hành.
5. `outline/arcs/*.md` — kế hoạch arc hiện tại.
6. `outline/master_outline.md` — hướng dài hạn.
7. `seed/seed.yaml` — ý định gốc.
8. Draft / scene plan / ý tưởng chưa final.

Outline là kế hoạch, không phải canon. Final chapter và canon ledger mới là sự kiện đã xảy ra.

## 3. Branch contract

- Framework chỉ sống trên `main`.
- Mỗi truyện sống trên một branch riêng: `story/<slug>`.
- Không viết nội dung hai truyện trên cùng branch.
- Không merge story branch vào `main` trừ khi người dùng chủ động yêu cầu.
- Mọi thao tác trên truyện phải chỉ rõ branch trước khi ghi file.

## 4. Read-before-write contract

Trước khi viết một chương, bắt buộc đọc tối thiểu:

- `seed/seed.yaml`
- `bible/story_bible.md`
- `bible/style_bible.md`
- phần Character DNA của tất cả nhân vật xuất hiện
- `outline/master_outline.md` phần có liên quan
- arc outline hiện tại
- `memory/current_state.md`
- `memory/canon_ledger.md`
- `memory/character_states.md`
- `memory/cultivation_ledger.md`
- `memory/knowledge_ledger.md`
- `memory/foreshadowing.md`
- `memory/unresolved_threads.md`
- tóm tắt ít nhất 3 chương gần nhất; đọc full final gần nhất nếu scene phụ thuộc trực tiếp

Nếu dữ liệu thiếu, phải bổ sung stage tương ứng trước khi viết.

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

## 6. Character DNA contract

Mỗi nhân vật quan trọng phải có DNA riêng gồm tối thiểu:

- core desire;
- core fear;
- wound / quá khứ định hình;
- giá trị bất khả nhượng;
- điểm mù;
- mâu thuẫn nội tại;
- social mask;
- điều họ xấu hổ hoặc không muốn thừa nhận;
- decision heuristic: cách họ quyết định khi chịu áp lực;
- risk tolerance;
- cách đối xử với kẻ yếu, người ngang hàng, người mạnh hơn;
- relationship vectors với nhân vật chính;
- speech fingerprint: nhịp câu, từ quen dùng, mức trực tiếp, kiểu né tránh;
- emotional tells: hành vi nhỏ khi giận, sợ, vui, mất kiểm soát;
- combat signature nếu có;
- cultivation philosophy;
- secret / hidden agenda nếu có;
- forbidden behavior: điều nhân vật gần như không làm nếu chưa có biến cố đủ lớn;
- arc vector: họ đang thay đổi về hướng nào.

### Anti-clone rule

Hai nhân vật không được có cùng bộ phản ứng trước áp lực. Nếu đổi tên hai nhân vật mà hội thoại và quyết định vẫn hoán đổi được cho nhau, Character DNA chưa đạt.

## 7. Văn phong tiếng Việt

Mục tiêu là văn xuôi tiếng Việt tự nhiên có khí chất tiên hiệp, không phải bản dịch máy và không phải văn “AI”.

### Phải làm

- ưu tiên câu có nhịp biến thiên theo cảnh;
- dùng từ Hán Việt đúng ngữ cảnh, không chất đống;
- miêu tả thông qua chi tiết có tác dụng;
- cho cảm xúc xuất hiện qua hành động, lựa chọn, nhịp nói, cảm giác thân thể;
- giữ POV nhất quán trong cảnh;
- hội thoại phải gắn với địa vị, lịch sử quan hệ và mục tiêu hiện tại;
- để độc giả tự suy ra khi thông tin đã đủ;
- cảnh chiến đấu phải có vị trí, mục tiêu, tài nguyên, phản ứng và hậu quả.

### Tránh

- mở đoạn bằng cùng một cấu trúc lặp đi lặp lại;
- liên tục dùng “lúc này”, “ngay sau đó”, “cùng lúc đó”, “không khỏi”, “hiển nhiên” như khớp nối máy móc;
- ba vế đối xứng hoặc câu hùng biện quá đều ở mọi đoạn;
- nhân vật liên tục tự giải thích động cơ bằng độc thoại;
- kể lại điều độc giả vừa đọc;
- tính từ cường điệu thay cho chi tiết cụ thể;
- tất cả nhân vật cùng một giọng;
- cuối chương luôn tóm tắt bài học hoặc gượng ép cliffhanger;
- thông tin worldbuilding dạng encyclopedia chèn vào giữa hành động;
- dùng thuật ngữ mới không cần thiết chỉ để tạo cảm giác phức tạp.

## 8. Scene contract

Mỗi scene phải biết:

- POV;
- time / place;
- nhân vật hiện diện;
- mục tiêu của POV character;
- trở ngại;
- stakes;
- thông tin nhân vật biết trước scene;
- thông tin không được phép biết;
- turn / reversal;
- outcome;
- state changes;
- setup / payoff / foreshadowing liên quan;
- bridge sang scene sau.

Scene không có thay đổi trạng thái phải bị chất vấn hoặc cắt.

## 9. Quality gate

Một chương chỉ được final khi không còn lỗi `BLOCKER` và `MAJOR` chưa xử lý.

QC bắt buộc kiểm tra:

- canon;
- timeline;
- geography / travel time;
- cultivation / power scaling;
- skill, technique, artifact ownership;
- injuries, fatigue, consumables;
- character knowledge;
- relationship state;
- Character DNA;
- POV;
- causal logic;
- pacing;
- prose naturalness;
- repetition;
- dialogue differentiation;
- exposition load;
- setup/payoff;
- ending quality.

QC phải trích dẫn đoạn hoặc mô tả vị trí lỗi, không chấm điểm chung chung.

## 10. Rewrite contract

Rewrite phải:

1. sửa toàn bộ BLOCKER/MAJOR;
2. giữ sự kiện canon đã đúng;
3. không thêm twist lớn ngoài outline chỉ để làm đoạn hay hơn;
4. giảm dấu vết văn mẫu nhưng không “làm màu” câu chữ;
5. kiểm tra lại toàn chương sau sửa để tránh lỗi dây chuyền.

## 11. Memory contract

Sau mỗi chương final, cập nhật memory trước khi viết chương tiếp theo. Memory ghi **delta có cấu trúc**, không chỉ tóm tắt văn học.

Bắt buộc ghi nếu thay đổi:

- thời gian / địa điểm hiện tại;
- trạng thái và vị trí nhân vật;
- thương tích, tinh thần, mục tiêu ngắn hạn;
- cảnh giới, tiến độ tu luyện, kỹ năng mới;
- vật phẩm nhận/mất/dùng/hỏng;
- quan hệ;
- ai biết bí mật gì;
- faction standing;
- lời hứa, nợ, nhiệm vụ;
- foreshadowing mới / payoff;
- unresolved threads;
- timeline events;
- canon facts mới.

Không ghi suy đoán của model thành canon.

## 12. Batch 10 contract

Batch 10 là một transaction logic gồm 10 vòng chương liên tiếp:

`plan → draft → QC → rewrite → final → memory update`

rồi mới chuyển chương kế tiếp.

Không viết 10 draft song song rồi mới cập nhật memory. Cách đó bị cấm vì làm hỏng continuity.

Cuối batch phải chạy Batch Audit trên cả 10 final:

- continuity xuyên chương;
- nhịp arc;
- power progression;
- repetition xuyên batch;
- character drift;
- plot thread balance;
- setup/payoff ledger;
- trạng thái bắt đầu cho batch tiếp theo.

## 13. Final file contract

Bản phát hành phải là plain text UTF-8, đường dẫn:

`stories/<slug>/final/Chương X: <Tiêu đề>.txt`

Nội dung file:

```text
Chương X: <Tiêu đề>

<nội dung chương>
```

Không chèn QC note, metadata, prompt, lời giải thích hoặc markdown vào file final.

## 14. Không tự động hóa mù

Tự động hóa ở đây nghĩa là ChatGPT có thể tự chạy tuần tự đủ stage cho batch theo lệnh người dùng. Nó **không** có nghĩa bỏ kiểm tra, bịa dữ liệu còn thiếu, hoặc làm song song những bước phụ thuộc nhau.
