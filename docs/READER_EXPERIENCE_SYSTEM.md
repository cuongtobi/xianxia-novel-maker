# Story Promise System

Controller duy nhất của framework: **Story Promise Controller**.

## 1. Purpose

Story Promise trả lời: **độc giả chọn và tiếp tục truyện này để nhận điều gì?**

Mỗi story khóa 3–5 promises từ Genesis.

## 2. Promise contract

Mỗi promise có:

- stable ID;
- promise;
- reader value;
- PAY definition;
- ADVANCE definition;
- false pay;
- drought warning;
- escalation path.

## 3. Per-chapter status

- `UNTOUCHED`
- `ADVANCE`
- `PAY_MINOR`
- `PAY_MAJOR`
- `PAY_ARC`

Magnitude là thuộc tính của Story Promise, không phải controller riêng.

## 4. PAY rule

Chỉ đánh PAY khi chapter tạo result/reveal/acquisition/loss/progression/relationship/status/state change hoặc trải nghiệm trung tâm mà promise đã cam kết.

Không tính PAY cho setup, lời hứa tương lai, hook chưa thành result hoặc state change quá nhỏ so với PAY definition.

## 5. Drought

Theo dõi:

- `last_touch_chapter`;
- `last_pay_chapter`;
- `last_major_pay_chapter`;
- `pay_drought`;
- `drought_warning`;
- next planned payoff window.

Không ép fake payoff để reset drought. Nếu chapter hiện tại không organic cho PAY, sửa future arc/window.

## 6. Pipeline integration

Story Promise được dùng tại:

1. Genesis → master outline;
2. Arc → planned PAY windows;
3. Scene plan → Promise target;
4. **Combined QC / Story Promise section** → xác nhận actual status;
5. Memory → update runtime promise state;
6. Batch Audit → xem payoff/drought.

Không có Story Promise report riêng trong v3.2.

## 7. Writer boundary

Writer chỉ cần biết promise chapter phục vụ, target ADVANCE/PAY và concrete payoff nếu có. Không expose metric/controller đã retire.

## 8. Promise memory

`memory/reader_experience.md` giữ tên để tương thích nhưng chỉ cần:

```text
Promise ID
Last status
Last touch chapter
Last pay chapter
Last major pay chapter
Current pay drought
Drought warning
Next planned payoff window
Notes
```

## 9. Retired systems

Không còn active controller/gate/quota cho Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration, Heat, Binge, Xianxia Experience/Density, Emotional Residue hay Human Irrationality Controller.

Historical artifacts được giữ làm lịch sử nhưng không tiếp tục enforce.
