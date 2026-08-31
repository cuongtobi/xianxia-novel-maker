# Framework v3.1 Migration — Promise-Only

Framework v3.1 đơn giản hóa v3: **chỉ Story Promise Controller còn active**.

## Retired controller state

Các field/report liên quan Narrative Engine, Dramatic Geometry, Competence Friction, Aspiration, Heat, Binge, Xianxia Experience/Density, Emotional Residue và Human Irrationality Controller là historical data. Không cần xóa khỏi final cũ, nhưng không tiếp tục enforce/update.

## Migration steps

1. giữ nguyên canon/final;
2. cập nhật manifest `version: 3.1`;
3. `controllers: [story_promise]`;
4. `qc_modes: [continuity, story_promise, style_fingerprint]`;
5. bỏ requirement `rolling_audit_every`, `retention_v3_required`, `xianxia_density_required` và các controller flags;
6. rút `memory/reader_experience.md` về Story Promise state;
7. rút current/future arc về Promise PAY windows + story beats bình thường;
8. không backfill/xóa historical controller reports;
9. production tiếp theo dùng `docs/BATCH_5_WORKFLOW.md`.

## Compatibility

Filename `reader_retention_report.md` được giữ để không phá story/tooling cũ, nhưng nội dung native v3.1 là **Story Promise Review**.

`rolling_3_chapter_audit.md` cũ vẫn có giá trị lịch sử nhưng không còn artifact bắt buộc.

## Goal

Giảm cognitive load cho Writer và tránh tình trạng prose được tạo để chứng minh compliance với nhiều metric thay vì phục vụ câu chuyện.
