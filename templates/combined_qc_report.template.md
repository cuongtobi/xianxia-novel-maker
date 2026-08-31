# Combined QC Report Template

> File: `stories/<slug>/chapters/NNNN/combined_qc_report.md`
> Reviewer: Combined QC Reviewer

# Metadata

- Story:
- Chapter:
- Candidate reviewed: draft / rewritten candidate
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

Check:

- repeated rhetorical frames;
- fragment/cadence abuse;
- Q&A quá sạch;
- hypothesis-loop lặp;
- aphorism/recap/exposition;
- lexical/stock tics;
- dialogue sameness;
- house-style drift;
- Reference Style drift/overfit nếu enabled.

# D. Decision

- BLOCKER remaining:
- MAJOR remaining:
- MINOR/NOTE:
- Decision: PASS / REWRITE_REQUIRED
- Why:

Rule:

- không BLOCKER/MAJOR cần sửa trong chapter → `PASS`;
- có BLOCKER/MAJOR → `REWRITE_REQUIRED`;
- MINOR/NOTE không tự động kích hoạt rewrite.

Nếu `PASS`, draft đi thẳng thành final và không tạo rewrite artifact.

# E. Rewrite Recheck — only if rewrite ran

- Original failing finding IDs:
- Fix summary:
- Recheck result for each finding:
- New BLOCKER/MAJOR introduced?:
- Final decision: PASS / REWRITE_REQUIRED

Không tạo report re-QC riêng. Recheck được ghi ngay trong file này trước atomic commit.
