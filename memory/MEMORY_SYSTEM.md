# Memory System — Promise-Only

## 1. Mục tiêu

Memory giữ continuity dài hạn và Story Promise runtime state. Memory không thay thế final/canon.

## 2. Files

```text
memory/
├── current_state.md
├── canon_ledger.md
├── timeline.md
├── character_states.md
├── relationships.md
├── cultivation_ledger.md
├── inventory_artifacts.md
├── factions_locations.md
├── knowledge_ledger.md
├── foreshadowing.md
├── unresolved_threads.md
├── chapter_summaries.md
└── reader_experience.md
```

## 3. Source hierarchy

Canon Ledger > Final > Bibles > Memory > Arc > Master Outline > Seed > Draft.

## 4. current_state.md

Lưu last finalized chapter, current time/location, current arc/objective, protagonist state, active injuries/resources/relationships/threads và next chapter pointer.

## 5. Ledgers

- timeline: event/time/order;
- character_states: runtime emotion/goal/injury/status;
- relationships: current relationship state;
- cultivation: realm/progress/technique/bottleneck;
- inventory: resources/artifacts/ownership;
- factions_locations: faction/location facts;
- knowledge: who knows what and since when;
- foreshadowing: setup/payoff state;
- unresolved_threads: open story obligations;
- summaries: compact chapter truth.

## 6. reader_experience.md

Tên file được giữ vì compatibility, nhưng native v3.1 chỉ lưu **Story Promise runtime state**.

Mỗi promise:

- ID;
- current status;
- last touch chapter;
- last pay chapter;
- last major pay chapter;
- pay drought;
- drought warning;
- next planned payoff window;
- recent promise events;
- notes.

Không lưu hoặc tiếp tục cập nhật Narrative Engine, Geometry, Competence outcome, Aspiration, Heat, Binge, Xianxia Experience/Density hay Emotional Residue metrics.

## 7. Update order after final

1. read final as truth;
2. update canon if new locked facts;
3. update timeline/state/ledgers;
4. append summary;
5. update Promise runtime state;
6. update manifest pointers;
7. verify no memory file describes draft-only events.

Không sang chapter kế nếu memory chưa current.

## 8. Legacy data

Retired controller fields trong story cũ có thể giữ làm historical evidence. Khi migrate, không cần xóa lịch sử; chỉ dừng update/enforcement và tạo khu vực `Current Promise State` rõ ràng.
