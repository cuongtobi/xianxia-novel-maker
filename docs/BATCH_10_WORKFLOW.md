# Batch 10 Chapters Workflow

## 1. Mục tiêu

Cho phép người dùng ra một lệnh như:

> Viết tiếp batch 10 chương cho truyện hiện tại.

ChatGPT tự chạy đủ pipeline cho 10 chương **trong cùng story branch**, nhưng vẫn xử lý từng chương tuần tự để memory của chương N trở thành input của chương N+1.

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
Ch. N: plan → draft → QC → rewrite → final → memory update
Ch. N+1: read new memory → plan → draft → QC → rewrite → final → memory update
...
```

Batch chỉ là đơn vị **điều phối và audit**, không phải đơn vị bỏ qua dependency.

## 3. Batch Preflight

Trước chương đầu của batch:

1. xác nhận branch `story/<slug>`;
2. đọc `seed/seed.yaml`;
3. đọc toàn bộ ba bible;
4. đọc phần master outline liên quan;
5. đọc arc hiện tại;
6. đọc `memory/current_state.md`;
7. đọc các ledger liên quan;
8. đọc summaries 3–10 chương gần nhất;
9. đọc full final chương gần nhất;
10. xác định chapter range của batch.

### Preflight output nội bộ

- start chapter;
- end chapter;
- active arc;
- major constraints;
- active threads;
- likely payoff windows;
- cultivation constraints;
- character drift risks;
- pacing risks từ batch trước.

Không cần tạo file riêng trừ khi cần audit.

## 4. Arc Coverage Check

Trước batch, xác định:

- 10 chương này nằm trọn một arc hay cắt qua arc boundary;
- nếu arc hiện tại hết giữa batch, phải tạo/đọc arc tiếp theo **trước khi viết chương vượt boundary**;
- không kéo dài arc chỉ để đủ 10 chương;
- không kết arc sớm chỉ vì hết batch.

## 5. Chapter Loop

Với mỗi chương `N`:

### Stage A — Assemble Context

Đọc:

- current state mới nhất;
- arc beat dự kiến cho N;
- Character DNA nhân vật tham gia;
- ledgers liên quan;
- summary gần nhất;
- final chương N-1 khi continuity trực tiếp.

Tạo “context constraints” trong reasoning, không ghi thành prose.

### Stage B — Scene Plan

Tạo:

`stories/<slug>/chapters/NNNN/scene_plan.md`

Plan phải nêu:

- POV;
- goal;
- obstacle;
- stakes;
- knowledge constraints;
- causal chain;
- state changes;
- memory delta preview.

### Stage C — Draft

Tạo:

`stories/<slug>/chapters/NNNN/draft.txt`

Draft chỉ chứa title + truyện, không tự đánh giá trong file.

Writer được tự do micro-prose nhưng không phá scene constraints.

### Stage D — Quality Check

So sánh draft với:

- canon;
- bible;
- memory;
- scene plan;
- recent chapters.

Tạo:

`stories/<slug>/chapters/NNNN/quality_report.md`

QC phải phân loại severity.

### Stage E — Rewrite

Nếu có BLOCKER hoặc MAJOR, tạo:

`stories/<slug>/chapters/NNNN/rewrite.txt`

Rewrite là full chapter hoàn chỉnh, không phải patch.

Nếu draft không có BLOCKER/MAJOR, vẫn tạo rewrite như pass biên tập cuối nếu production config yêu cầu `require_rewrite: true`.

### Stage F — Critical Re-QC

Kiểm tra lại:

- tất cả BLOCKER;
- tất cả MAJOR;
- đoạn bị rewrite lớn;
- continuity bị ảnh hưởng.

Không final nếu còn BLOCKER/MAJOR.

### Stage G — Final

Tạo:

`stories/<slug>/final/Chương N: <Tiêu đề>.txt`

Nội dung plain text:

```text
Chương N: <Tiêu đề>

<nội dung>
```

### Stage H — Memory Update

Ngay sau final:

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
- current_state cuối cùng.

### Stage I — Commit checkpoint

Có thể commit theo từng chương hoặc nhóm thay đổi nhỏ, nhưng state trên branch phải luôn phản ánh chapter transaction đã hoàn tất.

## 6. Dynamic Outline Adaptation

Sau mỗi chương, kiểm tra beat chương kế tiếp còn hợp state mới không.

Nếu không:

- không ép nhân vật trở về plan cũ;
- giữ arc goal và constraint quan trọng;
- điều chỉnh beat tương lai;
- cập nhật arc outline nếu thay đổi đáng kể;
- ghi revision log.

## 7. Batch-Level Pacing Controller

Theo dõi pattern trong 10 chương:

- action;
- investigation/discovery;
- cultivation;
- relationship;
- politics;
- travel;
- aftermath;
- quiet tension.

Không dùng quota cứng, nhưng nếu 5–6 chương liền cùng function, phải có lý do rõ.

### Warning patterns

- 3 chapter openings cùng kiểu;
- 3 endings liên tiếp cùng cliffhanger structure;
- liên tục có người xuất hiện cứu nguy;
- liên tục nhận bảo vật để giải quyết conflict;
- mọi conflict kết bằng đánh nhau;
- breakthrough quá đều theo lịch;
- supporting cast chỉ phản ứng với MC.

## 8. Batch-Level Character Controller

Cuối mỗi 3–4 chương, tự kiểm tra:

- ai đang biến mất quá lâu;
- ai đang mất agency;
- ai có giọng hội thoại trôi về narrator;
- relationship change có earned không;
- antagonist/faction có đang hành động ngoài màn hình hợp lý không.

## 9. Batch-Level Power Controller

Theo dõi:

- tài nguyên nhận vs tiêu;
- technique mastery;
- injury recovery;
- realm progress;
- breakthrough setup;
- đối thủ tương quan;
- cheat/special trait usage frequency.

Không để special trait trở thành đáp án cho mọi vấn đề.

## 10. End-of-Batch Audit

Sau chương thứ 10 của batch, tạo:

`stories/<slug>/chapters/batch_NNNN_NNNN_audit.md`

Template:

```md
# Batch Audit — Ch. A–B

## 1. Arc progress
- Start state:
- End state:
- Arc question progress:
- Outline deviation:

## 2. Continuity
- Timeline:
- Geography:
- Knowledge:
- Inventory:
- Injuries:
- Relationships:

## 3. Character
- MC drift:
- Supporting cast agency:
- Antagonist movement:
- Voice differentiation:

## 4. Cultivation
- Progress earned?:
- Resource economy:
- Power scaling anomalies:

## 5. Style
- Repeated words/phrases:
- Repeated scene structures:
- Repeated endings:
- AI-like patterns detected:

## 6. Threads
- Opened:
- Advanced:
- Paid:
- Forgotten risk:

## 7. Next batch handoff
- Required arc beats:
- Immediate constraints:
- Payoffs approaching:
- Characters requiring attention:
- Power constraints:
- Style corrections:
```

## 11. Batch Completion Criteria

Batch hoàn tất khi:

- đủ 10 final files, trừ khi truyện kết thúc hoặc user chỉ định range khác;
- không final nào còn BLOCKER/MAJOR;
- memory phản ánh chương cuối batch;
- batch audit đã tạo;
- arc outline đã cập nhật nếu có deviation;
- next-batch handoff rõ.

## 12. Resume After New Chat

Trong một phiên ChatGPT mới, user chỉ cần chỉ repo + story branch và nói tiếp tục batch.

ChatGPT phải đọc:

1. `AGENTS.md` từ main/branch;
2. story seed;
3. current state;
4. batch audit gần nhất;
5. arc hiện tại;
6. bible cần thiết;
7. recent summaries/final.

Không dựa vào memory hội thoại ChatGPT cũ như source of truth.

## 13. User Commands

Các lệnh tự nhiên được hỗ trợ:

- `Khởi tạo truyện mới từ seed này.`
- `Xây story bible, style bible, characters bible.`
- `Lập master outline và arc 1.`
- `Viết chương 1 hoàn chỉnh qua QC.`
- `Viết batch 10 chương tiếp theo.`
- `Tiếp tục từ current_state.`
- `Audit continuity 20 chương gần nhất.`
- `Kiểm tra power scaling.`
- `Kiểm tra Character DNA drift.`
- `Sửa arc outline theo diễn biến final, không retcon.`

## 14. Stop Conditions

Tự dừng trước khi tạo final nếu:

- canon conflict không thể giải quyết mà không retcon;
- seed có constraint người dùng đánh dấu `user_must_decide` chưa có đáp án và ảnh hưởng trực tiếp;
- chapter outcome bắt buộc phá hard rule;
- final filename/title không xác định được.

Trong các trường hợp khác, ưu tiên tự giải quyết sáng tạo theo bible và tiếp tục batch.
