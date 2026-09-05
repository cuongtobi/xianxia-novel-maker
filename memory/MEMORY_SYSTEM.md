# Memory System — v4.0 State-Centric

## 1. Purpose

Memory stores current runtime reality and continuity evidence. Memory does not replace Final or Canon Ledger.

## 2. Active files

Recommended structure:

```text
memory/
├── story_state.md
├── arc_state.md
├── character_states.md
├── canon_ledger.md
├── timeline.md
├── relationships.md
├── cultivation_ledger.md
├── inventory_artifacts.md
├── factions_locations.md
├── knowledge_ledger.md
├── foreshadowing.md
├── unresolved_threads.md
├── chapter_summaries.md
├── batch_summaries.md
├── arc_summaries.md
└── saga_summaries.md
```

Legacy `current_state.md` or `reader_experience.md` may remain in migrated stories but should not be the active v4 runtime source once migration is complete.

## 3. Source hierarchy

```text
Canon Ledger
> Final Chapters
> Bibles
> Story/Arc/Character State
> Continuity Ledgers
> Master Outline
> Seed
> Chapter/Scene State snapshots
> Draft
```

## 4. story_state.md

Compact global runtime snapshot:

- last finalized chapter;
- current time/location;
- current arc;
- protagonist global position;
- major active pressures;
- faction positions;
- current cultivation/resource position;
- major relationships;
- active mysteries/obligations;
- reader expectations currently alive;
- next handoff.

Do not turn it into a full novel summary.

## 5. arc_state.md

Strategic state of current arc:

- arc question;
- current phase;
- protagonist/antagonist/faction positions;
- active pressures;
- cultivation/resource pressure;
- relationship motion;
- mysteries/reveals in play;
- unresolved obligations;
- soft reader expectations;
- likely pressure directions;
- exit conditions.

Arc State reflects current reality, not merely old outline intention.

## 6. character_states.md

Runtime state for active/recent characters:

- current goals;
- emotions;
- beliefs/bias;
- knowledge/suspicions/errors;
- injury/fatigue/body;
- resources/status;
- relationship context;
- recent consequential memories;
- current behavioral pressure.

Stable identity and deep baseline remain in Character Bible.

## 7. Continuity ledgers

- `timeline.md`: event/time/order;
- `relationships.md`: relationship changes and current durable state;
- `cultivation_ledger.md`: realm/progress/technique/bottleneck;
- `inventory_artifacts.md`: ownership/resources/artifacts;
- `factions_locations.md`: faction and location facts;
- `knowledge_ledger.md`: who knows/suspects what and since when;
- `foreshadowing.md`: setup and resolution state;
- `unresolved_threads.md`: open obligations and unresolved consequences.

## 8. Update order after Final

1. read Final as truth;
2. update Canon Ledger if a new stable fact is locked;
3. update timeline and affected ledgers;
4. update affected Character States;
5. update Story State;
6. update Arc State;
7. append compact Chapter Summary;
8. update batch/arc/saga summary only when boundary is reached;
9. update manifest pointers;
10. verify no state describes draft-only or edited-out events.

## 9. Memory compaction

Long stories must not grow every runtime file indefinitely.

Use hierarchy:

```text
recent chapter detail
→ batch summary
→ completed arc summary
→ completed saga summary
```

Suggested behavior:

- keep recent 10–15 chapter summaries detailed enough for local continuity;
- after a batch, preserve batch-level consequences;
- after an arc, compact old transient details into arc summary;
- after a saga, compact completed arc summaries into saga-level consequences when safe.

Never compact away:

- canon facts;
- active injuries/debts/resources;
- unresolved promises/obligations;
- knowledge boundaries still plot-relevant;
- ownership;
- relationship consequences;
- foreshadowing still unpaid;
- cultivation constraints still active.

## 10. State quality rules

State should be:

- factual;
- compact;
- current;
- consequence-oriented;
- free of prose-style instructions;
- free of speculative events not in Final.

Avoid report bloat. Store only what future decisions/continuity actually need.

## 11. Legacy v3 reader experience

Old `reader_experience.md` Story Promise data may be preserved as historical evidence.

If useful, migrate it into soft Story/Arc State fields such as:

- reader expectation;
- last meaningful delivery;
- currently rising pressure;
- likely future opportunity.

Do not continue per-chapter PAY status/drought enforcement in v4.
