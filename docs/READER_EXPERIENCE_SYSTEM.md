# Story Promise System

File này định nghĩa **controller duy nhất** của framework: Story Promise Controller.

## 1. Mục tiêu

Story Promise trả lời: **độc giả chọn và tiếp tục truyện này để nhận điều gì?**

Mỗi truyện khóa 3–5 promises từ Genesis. Promise không phải topic; nó là cam kết trải nghiệm/kết quả dài hạn.

## 2. Promise contract

Mỗi promise có:

- `Promise ID` ổn định;
- `promise` — lời hứa cụ thể;
- `reader_value` — vì sao độc giả quan tâm;
- `PAY definition` — điều kiện thực sự được tính payoff;
- `ADVANCE definition` — setup/pressure/clue/progress nhưng chưa trả;
- `false pay` — thứ trông giống payoff nhưng không đủ;
- `drought_warning` — số chương tối đa không PAY trước khi cảnh báo;
- `escalation_path` — promise lớn dần thế nào qua saga/arc.

## 3. Per-chapter states

- `UNTOUCHED` — chapter không chạm promise;
- `ADVANCE` — tăng setup/pressure/clue/progress;
- `PAY_MINOR` — payoff thật phạm vi nhỏ;
- `PAY_MAJOR` — payoff đáng kể, reader cảm thấy lời hứa được trả rõ;
- `PAY_ARC` — payoff đóng/tái định nghĩa một objective/threshold cấp arc.

Magnitude là thuộc tính của Promise Controller, không phải controller riêng.

## 4. PAY rule

Chỉ đánh PAY khi chapter tạo ít nhất một thứ hữu hình đối với reader:

- kết quả;
- reveal;
- acquisition/loss;
- chiến thắng/thất bại có hậu quả;
- progression có bằng chứng;
- relationship/status/state change;
- trải nghiệm trung tâm mà promise đã cam kết.

Không tính PAY cho:

- nói về điều sẽ làm;
- setup chưa convert thành result;
- hook cuối hứa chương sau;
- đổi wording nhưng state không đổi;
- một chi tiết quá nhỏ so với PAY definition.

## 5. Drought

Theo dõi cho từng core promise:

- `last_touch_chapter`;
- `last_pay_chapter`;
- `last_major_pay_chapter`;
- `pay_drought`;
- `drought_warning`.

Vượt drought warning → finding. Severity tùy mức độ core của promise và arc context.

Không ép fake payoff chỉ để reset drought. Nếu current chapter không organic cho PAY, sửa future outline/window.

## 6. Planning locations

Story Promise được dùng tại:

1. Genesis → master outline khóa contract;
2. Arc → planned PAY windows;
3. Chapter plan → target trạng thái;
4. Story Promise Review → xác nhận thực tế;
5. Memory → lưu last touch/pay/drought;
6. Batch Audit → xem balance và debt.

## 7. Writer boundary

Writer chỉ cần biết:

- promise nào chapter này phục vụ;
- chapter dự kiến ADVANCE hay PAY;
- payoff cụ thể nếu có.

Writer không cần biết rolling metrics/controller khác. Story Promise không được biến thành checklist nhồi vào prose.

## 8. Memory schema

`memory/reader_experience.md` được giữ tên để tương thích story cũ, nhưng nội dung runtime chỉ cần:

```text
Story Promise State
- Promise ID
- Last status
- Last touch chapter
- Last pay chapter
- Last major pay chapter
- Current pay drought
- Drought warning
- Next planned payoff window
- Notes
```

Có thể lưu recent 5–10 promise events để audit, không cần lưu Engine/Geometry/Heat/Density/Binge/etc.

## 9. Retired systems

Các hệ thống sau không còn active controller/gate/quota:

- Narrative Engine;
- Dramatic Geometry;
- Competence Friction;
- Aspiration;
- Heat Curve;
- Binge Test;
- Xianxia Experience;
- Xianxia Density;
- Emotional Residue;
- Human Irrationality Controller.

Không migrate dữ liệu cũ của chúng thành yêu cầu mới. Artifact cũ giữ nguyên như historical evidence.
