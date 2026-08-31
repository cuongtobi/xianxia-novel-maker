# Batch 5 Chapters Workflow — Atomic Combined QC

## 1. Mục tiêu

Default batch = **5 chapters**. Chạy tuần tự, mỗi chapter là **một atomic Git transaction**.

Controller duy nhất: **Story Promise Controller**.

## 2. Chapter flow

```text
assemble context
→ scene plan
→ draft
→ combined QC
→ rewrite only if required
→ final
→ memory/manifest updates
→ one Git tree/commit
```

Không tạo report QC tách rời.

## 3. Preflight batch

Trước chapter đầu:

1. xác nhận repo/branch/slug;
2. đọc `AGENTS.md` + manifest;
3. verify `batch_size: 5` và transaction mode `atomic_git_commit`;
4. đọc seed + bibles + Story Promises + current arc;
5. đọc current state + promise memory + ledgers/summaries cần thiết;
6. xác định exact range `start ... start+4` nếu user không override;
7. verify batch audit trước nếu range trước đã hoàn tất.

## 4. Per-chapter context

Đọc đủ để viết đúng nhưng không reread dư thừa:

- current state;
- Story Promise state;
- arc beat;
- relevant character/cultivation/relationship/knowledge ledgers;
- 3 recent summaries;
- full final gần nhất khi continuity/style thực sự cần.

## 5. Scene plan

Plan gọn:

- chapter objective;
- POV/time/place/cast;
- start state;
- conflict/pressure;
- key beats/turn;
- important choice/consequence;
- Story Promise target + intended payoff nếu có;
- end state;
- continuity constraints;
- style constraints;
- ending hook nếu organic.

## 6. Draft

Viết complete chapter theo Style Bible/Character DNA/canon. Không viết cho metric đã retire.

## 7. Combined QC

Tạo đúng một file:

`chapters/NNNN/combined_qc_report.md`

Ba section:

### A. Continuity
Canon, timeline, geography, cultivation/power, resource/item/injury, knowledge, relationship/faction, POV, hard DNA contradiction.

### B. Story Promise
Promise target, `UNTOUCHED/ADVANCE/PAY_MINOR/PAY_MAJOR/PAY_ARC`, concrete payoff, false pay, magnitude, drought.

### C. Style
AI-like fingerprints, cadence/fragments, dialogue sameness, exposition/recap, lexical tics, house-style/reference drift.

Decision:

- `PASS`: không BLOCKER/MAJOR cần sửa;
- `REWRITE_REQUIRED`: có BLOCKER/MAJOR cần sửa trong chapter hiện tại.

MINOR/NOTE không tự động kích hoạt rewrite.

## 8. Rewrite only on failure

Nếu `PASS`:

```text
draft → final
```

Không tạo `rewrite.txt`; final giữ nguyên prose draft.

Nếu `REWRITE_REQUIRED`:

1. sửa candidate trong working memory;
2. ưu tiên `CUT > COMPRESS > REORDER > REPLACE > ADD`;
3. quick recheck chỉ các finding đã fail;
4. ghi kết quả recheck vào cuối cùng file `combined_qc_report.md`;
5. candidate pass trở thành final.

Không persist report/rewrite trung gian riêng.

## 9. Prepare memory before Git write

Sau khi final đã pass, tính toàn bộ thay đổi:

- current state;
- canon/timeline/character/relationship/cultivation/inventory/faction/knowledge/foreshadowing/unresolved ledgers nếu affected;
- chapter summaries;
- promise memory;
- manifest `last_finalized_chapter`, `next_chapter`, batch pointers.

Không write từng file ngay.

## 10. One atomic Git commit

Lấy branch HEAD/tree tại đầu chapter và giữ làm parent/base.

Sau khi tất cả nội dung đã sẵn sàng:

1. create blobs cho scene plan, draft, combined QC, final và mọi file memory/manifest changed;
2. nếu chapter đóng batch, create blob batch audit;
3. `create_tree(base_tree=<start tree>, tree_elements=[all changed paths])`;
4. `create_commit(parent=<start HEAD>, tree_sha=<new tree>)`;
5. `update_ref(branch, new commit)` đúng một lần;
6. verify branch HEAD.

Commit message gợi ý:

`story: finalize chapter N atomically`

Nếu chapter đóng batch:

`story: finalize chapter N and batch A-B`

Nếu fail trước `update_ref`, không coi chapter complete. Không tạo partial state trên branch.

## 11. Sequential guarantee

Chỉ bắt đầu chapter N+1 sau khi:

- commit N đã update ref thành công;
- manifest/memory trong commit N trỏ đúng `next_chapter`;
- combined QC result = PASS;
- final tồn tại.

## 12. Batch audit

Sau chapter thứ 5 của requested range, tạo `chapters/batch_NNNN_NNNN_audit.md` và **đưa vào cùng atomic commit của chapter thứ 5**.

Audit chỉ kiểm:

- 5 chapter commits/finals complete;
- combined QC PASS;
- memory current;
- continuity handoff;
- Story Promise payoff/drought;
- style caution xuyên batch;
- next-batch handoff.

Không có checkpoint Ch.3 và không có rolling audit.

## 13. Completion gate

Batch READY khi:

- đủ 5 requested finals;
- mỗi chapter có scene plan + draft + combined QC + final;
- mỗi chapter đã được atomic commit;
- memory current through last chapter;
- batch audit có trong commit cuối;
- không còn BLOCKER/MAJOR unresolved.
