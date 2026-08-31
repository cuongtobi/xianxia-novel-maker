# Combined QC Report Template

> File: `stories/<slug>/chapters/NNNN/combined_qc_report.md`
> Reviewer: Combined QC Reviewer

# Metadata

- Story:
- Chapter:
- Candidate reviewed: draft / rewritten candidate
- Style Bible:
- Reference Style enabled: yes/no
- Reference profile if enabled:
- Relevant selected reference traits for this chapter:
- Result: PASS / REWRITE_REQUIRED

# A. Continuity

Kiểm chỉ những gì có thể làm sai canon/state.

| ID | Severity | Location | Finding | Required fix |
|---|---|---|---|---|

Check:

- canon/facts;
- timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction;
- POV;
- hard Character DNA contradiction.

# B. Story Promise

| Promise ID | Target | Actual status | Concrete evidence | False pay? | Drought after chapter | Finding |
|---|---|---|---|---|---:|---|

Statuses:

`UNTOUCHED / ADVANCE / PAY_MINOR / PAY_MAJOR / PAY_ARC`

Check:

- target có được chạm thật không?;
- PAY có result/reveal/state change hữu hình không?;
- magnitude có bị phóng đại không?;
- có false pay không?;
- drought có vượt contract không?;
- nếu drought là vấn đề của future plan chứ không phải chapter hiện tại, ghi NOTE/ACTION cho arc thay vì ép fake payoff.

# C. Style

| ID | Severity | Location | Finding | Required fix |
|---|---|---|---|---|

## C1. Core house-style checks

- repeated rhetorical frames;
- fragment/cadence abuse;
- Q&A quá sạch;
- hypothesis-loop lặp;
- aphorism/recap/exposition;
- lexical/stock tics;
- dialogue sameness;
- story Style Bible drift;
- Reference Style overfit/imitation nếu enabled.

## C2. Tiên Nghịch High-Level Style DNA — only if selected in Story Style Bible

Không chapter nào phải pass đủ toàn bộ trait. Chỉ kiểm trait đã được Style Bible chọn và relevant với scene.

- **Grounded concrete event:** prose có bám người/vật/hành động/quyết định cụ thể hay trôi thành generic xianxia abstraction?:
- **Mortal anchor:** nếu scene cần ordinary-life contrast, nó có cụ thể và có meaning không?:
- **Pressure/release:** nếu chapter là conflict lớn, pressure có tích lũy bằng thay đổi risk/leverage hay chỉ kéo dài?:
- **Qualitative cultivation:** nếu cultivation là payoff chính, progression có đổi capability/perception/status/choice hay chỉ tăng số?:
- **Expert compression:** experienced MC có bị log quá nhiều suy luận/mechanism không?:
- **Power gap:** chênh lệch cảnh giới có đổi lựa chọn/resource/tactics thật không?:
- **Dao/insight:** câu triết lý có lived event/concrete image phía dưới không? insight có consequence không?:
- **Emotion:** peak có concrete attachment/action/body/silence và hậu quả kéo dài không?:
- **World scale:** reveal có revalue điều đã biết/stakes hiện tại hay chỉ thêm map/bigger number?:
- **Wonder:** có concrete impossible proof trước khi adjective hóa không?:

## C3. Weakness / imitation filter

- translation/convert syntax?:
- exposition/recap dài không đổi scene?:
- spectator shock quá dày?:
- stock gestures/connectors?:
- repeated combat/tournament shape?:
- unsupported aphorism/Dao lecture?:
- artificial cliffhanger?:
- direct imitation of reference wording/rhetorical frame/scene?:

# D. Decision

- BLOCKER remaining:
- MAJOR remaining:
- MINOR/NOTE:
- Decision: PASS / REWRITE_REQUIRED
- Why:

Rule:

- không BLOCKER/MAJOR cần sửa trong chapter → `PASS`;
- có BLOCKER/MAJOR → `REWRITE_REQUIRED`;
- MINOR/NOTE không tự động kích hoạt rewrite;
- không tạo MAJOR chỉ vì chapter không biểu diễn một reference trait không relevant.

Nếu `PASS`, draft đi thẳng thành final và không tạo rewrite artifact.

# E. Rewrite Recheck — only if rewrite ran

- Original failing finding IDs:
- Fix summary:
- Recheck result for each finding:
- New BLOCKER/MAJOR introduced?:
- Reference imitation risk introduced by rewrite?:
- Final decision: PASS / REWRITE_REQUIRED

Không tạo report re-QC riêng. Recheck được ghi ngay trong file này trước atomic commit.
