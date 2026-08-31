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

Bắt buộc đọc `docs/RETENTION_CONTROLLERS_V3.md` và `docs/XIANXIA_DENSITY_CONTROLLER.md`.

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
- `MAJOR`: làm hỏng nhân vật, reader promise, payoff magnitude, nhịp, Narrative Engine/Dramatic Geometry diversity, competence friction, aspiration, heat, bingeability, Xianxia Density/genre identity, causal logic hoặc tạo style fingerprint rõ; phải sửa.
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
- Promise magnitude: UNTOUCHED / ADVANCE / PAY_MINOR / PAY_MAJOR / PAY_ARC
- Reward score:
- Core pay drought:
- Core major payoff debt:
- Primary narrative engine:
- 3/4 same-engine risk:
- Dramatic geometry short signature:
- 3/4 same-geometry risk:
- Competence outcome:
- CLEAN_WIN streak/risk:
- Aspiration beat:
- Aspiration drought risk:
- Peak heat:
- Rolling-5 H2+ healthy?:
- Xianxia peak: X0 / X1 / X2 / X3
- Replaceability: LOW / MEDIUM / HIGH
- Rolling-3 Xianxia Density healthy?:
- Rolling-5 Xianxia Density healthy?:
- Genre density debt:
- Binge Test best reward moment:
- Binge Test without ending hook: YES / WEAK / NO
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
- Dramatic geometry repetition:
- Dialogue geometry repetition:
- Ending repetition:
- Rhetorical tic repetition:
- Promise magnitude/drought:
- Competence friction trend:
- Aspiration trend:
- Heat trend:
- Xianxia Density/replaceability trend:
- Binge Test trend:
- Xianxia drought:
- Emotional residue drought:
- BLOCKER/MAJOR findings:

# 5. Technical Gate vs Reader-Reward vs Xianxia Density Gate

## Technical Gate

- continuity/canon clean?:
- knowledge/POV clean?:
- style fingerprint acceptable?:
- required artifacts present?:

## Reader-Reward Gate

- core promise receives enough magnitude?:
- geometry not over-repeated?:
- competence has friction?:
- aspiration/fantasy desire alive?:
- heat curve alive?:
- intrinsic chapter reward exists?:
- Binge Test passes?:

## Xianxia Density Gate

- current xianxia_peak appropriate?:
- Active Xianxia causal beat real, not terminology?:
- Replaceability acceptable?:
- rolling 3 has `X2+`?:
- rolling 5 has `2×X2+ + 1×X3`?:
- aspiration/wonder keeps cultivation fantasy alive?:
- genre_density_debt acceptable?:

**Technical Gate PASS không override Reader-Reward hoặc Xianxia Density MAJOR.**

# 6. Cross-Reviewer Conflict Resolution

Nếu reviewer bất đồng, ghi rõ.

Ví dụ:

- Continuity PASS nhưng Retention MAJOR vì chapter thứ ba liên tiếp cùng geometry → vẫn phải rewrite.
- Retention thích một reveal nhưng Continuity đánh knowledge leak → continuity thắng.
- Style muốn cắt giải thích nhưng cắt làm mất knowledge boundary → giữ fact, đổi cách thể hiện.
- Engine khác nhau nhưng Dramatic Geometry giống → geometry finding vẫn giữ.
- Chapter có PAY_MINOR nhưng major payoff debt vượt planned window → không được coi là healthy chỉ vì có PAY.
- Ending hook mạnh nhưng Binge Test `NO` → rewrite nội dung chapter, không chỉ sửa hook.
- Chapter có nhiều từ “linh khí/pháp bảo/công pháp” nhưng Replaceability HIGH và không có Active causal beat → Xianxia Density finding vẫn giữ.

Findings:

# 7. Consolidated Issue List

| ID | Source reviewer/controller | Severity | Location | Problem | Required fix | Constraints |
|---|---|---|---|---|---|---|

Mỗi BLOCKER/MAJOR phải có vị trí và directive sửa cụ thể.

# 8. Rewrite Directive

Ưu tiên:

1. BLOCKER continuity/data;
2. MAJOR character/knowledge/causality;
3. MAJOR Story Promise / Payoff Magnitude;
4. MAJOR Narrative Engine / Dramatic Geometry;
5. MAJOR Xianxia Density / Replaceability;
6. MAJOR Competence Friction / Aspiration / Heat / Binge Test;
7. MAJOR Style Fingerprint;
8. Xianxia Experience / Emotional Residue thiếu kéo dài;
9. MINOR có lợi rõ.

Rewrite không được chữa repetition bằng synonym-spin. Nếu issue là engine/geometry, phải sửa cấu trúc hoặc cách conflict vận hành. Nếu issue là aspiration/heat/binge, không được chỉ thêm một câu hook cuối. Nếu issue là Xianxia Density, phải sửa supernatural causality/constraint/consequence, không rắc thêm vocabulary.

# 9. Critical Re-QC

Sau rewrite:

- Continuity issues fixed?:
- Retention issues fixed?:
- Style fingerprint issues fixed?:
- Payoff magnitude issues fixed?:
- Dramatic geometry issues fixed?:
- Competence friction issues fixed?:
- Aspiration/heat issues fixed?:
- Xianxia Density issues fixed?:
- Replaceability reduced by causal change?:
- Binge Test fixed?:
- Rolling audit issues fixed if required?:
- Rewrite có tạo contradiction mới?:

Nếu sửa lớn ở structure, chạy lại reviewer bị ảnh hưởng; không tự tick PASS bằng cảm giác.

# 10. Final Gate

- Continuity report exists: yes/no
- Reader retention report exists: yes/no
- Style fingerprint report exists: yes/no
- Rolling audit exists when required: yes/no/NA
- BLOCKER remaining: 0 / >0
- MAJOR remaining: 0 / >0
- Technical Gate: PASS / FAIL
- Reader-Reward Gate: PASS / FAIL
- Xianxia Density Gate: PASS / FAIL
- Rewrite required: yes/no
- Ready for final: yes/no

**Final bị cấm nếu thiếu artifact reviewer bắt buộc hoặc Reader-Reward/Xianxia Density Gate còn MAJOR, kể cả nội dung chapter technically correct.**

**PASS kỹ thuật ≠ PASS trải nghiệm đọc. PASS retention ≠ PASS genre density.**