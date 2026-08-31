# Architecture — Promise-Only Controller

## 1. Overview

Xianxia Novel Maker chạy trên ChatGPT Web + GitHub connector. GitHub là persistent state; ChatGPT là execution engine.

Framework hiện hành chỉ có **Story Promise Controller**.

```text
Human Seed
↓
Genesis
  ├─ Story Bible
  ├─ Style Bible
  ├─ Characters Bible
  ├─ Master Outline + 3–5 Story Promises
  ├─ Arc Outline + Promise PAY windows
  └─ Story Memory + Promise Memory
↓
Sequential Chapter Transaction
  ├─ Context Assembly
  ├─ Scene Plan
  ├─ Draft
  ├─ Continuity Auditor
  ├─ Story Promise Reviewer
  ├─ Style Fingerprint Auditor
  ├─ Aggregate Quality Gate
  ├─ Rewrite if needed + critical re-QC
  ├─ Final TXT
  └─ Memory Commit
↓
Batch Audit every 5 default chapters
```

## 2. Controller boundary

Controller duy nhất: `Story Promise Controller`.

Không có active controller/gate/quota cho Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration, Heat, Binge, Xianxia Experience, Xianxia Density, Emotional Residue hay Human Irrationality.

Continuity Auditor và Style Fingerprint Auditor là reviewer kỹ thuật, không phải controller sáng tác.

## 3. Data layers

### Canon / slow-changing

- bibles;
- canon ledger;
- Character DNA;
- Story Promise contract;
- final chapters.

### Planning

- master outline;
- arc outlines;
- planned Promise PAY windows;
- chapter intents.

### Runtime story state

- current state;
- timeline;
- character states;
- relationships;
- cultivation;
- inventory;
- faction/location;
- knowledge;
- foreshadowing;
- unresolved threads;
- chapter summaries.

### Promise runtime state

`memory/reader_experience.md` giữ:

- status của 3–5 promises;
- last ADVANCE/PAY;
- last major PAY;
- pay drought;
- recent payoff notes;
- next expected payoff window.

## 4. Story branch lifecycle

Framework ở `main`; mỗi truyện ở `story/<slug>`.

Genesis:

1. validate seed;
2. story bible;
3. style bible;
4. characters bible;
5. master outline + Story Promises;
6. opening arc + Promise PAY windows;
7. story memory;
8. promise memory.

## 5. Context Assembly

Always read seed, bibles, Story Promises, current arc, current state, promise memory, canon và recent summaries.

Đọc thêm final/ledger khi continuity hoặc style cần bằng chứng trực tiếp.

## 6. Scene architecture

Scene planning có chủ đích nhưng nhẹ:

- objective;
- conflict/pressure;
- POV/time/place/cast;
- start/end state;
- key beats/turn;
- choice/consequence nếu có;
- Story Promise target;
- intended payoff nếu có;
- continuity/style constraints.

Không expose metric labels của controller đã loại bỏ cho Writer.

## 7. QC architecture

### Continuity Auditor
Canon/state/knowledge/power/POV.

### Story Promise Reviewer
Kiểm target, ADVANCE/PAY, false pay, magnitude và drought.

### Style Fingerprint Auditor
Kiểm rhetorical patterns, cadence, dialogue sameness, AI-like prose, calibration, Reference Style drift/overfit.

Aggregate Gate chỉ nhận findings từ ba reviewer này.

## 8. Rewrite

Rewrite là sửa chữa, không phải stage mở rộng worldbuilding.

Ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`; mặc định final:draft <= khoảng 1.25. Structural failure → re-plan/re-draft.

## 9. Batch 5

Chapter transactions chạy tuần tự. Cuối 5 chương tạo batch audit kiểm artifact completion, continuity handoff, Promise delivery/drought, style risk và next-batch priorities.

Batch boundary là operational, không phải arc boundary.

## 10. Completion semantics

`PASS/READY` là artifact state. Thiếu artifact hoặc memory stale → `INCOMPLETE`.

Framework tối ưu cho:

**continuity + promise delivery + prose quality + writer freedom**.
