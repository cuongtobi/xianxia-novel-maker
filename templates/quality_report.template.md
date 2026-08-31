# Quality Gate Aggregate Template

> File đích: `stories/<slug>/chapters/NNNN/quality_report.md`
> File này **không thay thế** ba reviewer report. Nó aggregate kết quả để quyết định rewrite/final.

Một chapter QC đầy đủ phải có:

- `continuity_report.md` — Continuity Auditor;
- `reader_retention_report.md` — Reader Retention Editor;
- `style_fingerprint_report.md` — Style Fingerprint Auditor;
- `quality_report.md` — aggregate gate này.

Nếu `N % 3 == 0`, trước final còn phải có:

- `rolling_3_chapter_audit.md`.

# Metadata

- Chapter:
- Draft/rewrite reviewed:
- Arc:
- Continuity report:
- Reader retention report:
- Style fingerprint report:
- Rolling audit required: yes/no
- Rolling audit path if required:
- Result: PASS / REWRITE_REQUIRED

# Severity

- `BLOCKER`: phá canon, logic nền, timeline, knowledge, power system hoặc release contract; không được final.
- `MAJOR`: làm hỏng nhân vật, reader promise, nhịp, narrative engine diversity, causal logic hoặc tạo style fingerprint rõ; phải sửa.
- `MINOR`: nên sửa nếu không gây tác dụng phụ.
- `NOTE`: theo dõi, không bắt buộc sửa ngay.

Không được hạ severity chỉ vì một reviewer khác PASS. Ba reviewer có mục tiêu độc lập.

# 1. Continuity Auditor Summary

- BLOCKER:
- MAJOR:
- Key data findings:
- Knowledge/POV findings:
- Character-state findings:

# 2. Reader Retention Editor Summary

- Core promise targeted:
- Promise ADVANCE/PAY:
- Core promise drought:
- Primary narrative engine:
- 3/4 same-engine risk:
- Xianxia Experience delivered:
- Emotional Residue:
- Drag/retention findings:
- Ending / reason to continue:
- MAJOR findings:

# 3. Style Fingerprint Auditor Summary

- Dominant rhetorical tics:
- Q&A/dialogue cleanliness:
- Hypothesis-loop risk:
- Aphorism density:
- Paragraph/sentence fingerprint:
- Positive prose texture present:
- Calibration drift:
- MAJOR findings:

# 4. Rolling 3-Chapter Audit Summary

Chỉ điền nếu `N % 3 == 0`.

- Compared chapters:
- Opening repetition:
- Narrative engine repetition:
- Dialogue geometry repetition:
- Ending repetition:
- Rhetorical tic repetition:
- Promise drought:
- Xianxia drought:
- Emotional residue drought:
- BLOCKER/MAJOR findings:

# 5. Cross-Reviewer Conflict Resolution

Nếu reviewer bất đồng, ghi rõ.

Ví dụ:

- Continuity PASS nhưng Retention MAJOR vì chapter thứ ba liên tiếp là audit/Q&A → vẫn phải rewrite.
- Retention thích một reveal nhưng Continuity đánh knowledge leak → continuity thắng.
- Style muốn cắt giải thích nhưng cắt làm mất knowledge boundary → giữ fact, đổi cách thể hiện.

Findings:

# 6. Consolidated Issue List

| ID | Source reviewer | Severity | Location | Problem | Required fix | Constraints |
|---|---|---|---|---|---|---|

Mỗi BLOCKER/MAJOR phải có vị trí và directive sửa cụ thể.

# 7. Rewrite Directive

Ưu tiên:

1. BLOCKER continuity/data;
2. MAJOR character/knowledge/causality;
3. MAJOR Story Promise / Narrative Engine / retention;
4. MAJOR Style Fingerprint;
5. Xianxia Experience / Emotional Residue thiếu kéo dài;
6. MINOR có lợi rõ.

Rewrite không được chữa repetition bằng synonym-spin. Nếu issue là engine/geometry, phải sửa cấu trúc hoặc cách conflict vận hành.

# 8. Critical Re-QC

Sau rewrite:

- Continuity issues fixed?:
- Retention issues fixed?:
- Style fingerprint issues fixed?:
- Rolling audit issues fixed if required?:
- Rewrite có tạo contradiction mới?:

Nếu sửa lớn ở structure, chạy lại reviewer bị ảnh hưởng; không tự tick PASS bằng cảm giác.

# 9. Final Gate

- Continuity report exists: yes/no
- Reader retention report exists: yes/no
- Style fingerprint report exists: yes/no
- Rolling audit exists when required: yes/no/NA
- BLOCKER remaining: 0 / >0
- MAJOR remaining: 0 / >0
- Rewrite required: yes/no
- Ready for final: yes/no

**Final bị cấm nếu thiếu artifact reviewer bắt buộc, kể cả nội dung chương có vẻ ổn.**
