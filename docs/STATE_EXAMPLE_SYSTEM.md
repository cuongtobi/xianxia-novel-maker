# State + Example System — v4.0

## 1. Purpose

v4.0 replaces creative rule pressure with two primary signals:

- **State**: what is true now;
- **Examples**: what good project prose feels like.

Rules remain only as hard guardrails outside the Writer.

## 2. State hierarchy

```text
Stable Canon
   ↓
Story State
   ↓
Arc State
   ↓
Chapter State
   ↓
Scene State
   ↓
Character State at scene time
```

Each layer compresses only what the next layer needs.

## 3. Story State

Story State is the compact runtime snapshot across arcs.

Recommended fields:

- last finalized chapter;
- current time/location;
- current arc;
- protagonist global position;
- active global pressures;
- major faction positions;
- current cultivation/resource position;
- major relationships;
- active mysteries/obligations;
- reader expectations currently alive;
- next-state handoff.

Story State is not a summary of the entire novel.

## 4. Arc State

Arc State describes strategic motion now:

- arc question;
- current phase;
- start reality and desired exit condition;
- protagonist position;
- antagonist/faction positions;
- active pressures;
- cultivation/resource pressure;
- relationship motion;
- mysteries/reveals in play;
- unresolved obligations;
- reader expectations worth remembering;
- likely next pressure directions;
- exit conditions.

Do not encode a compulsory chapter sequence.

## 5. Chapter State

Chapter State describes what makes the next chapter possible now:

- entry reality;
- chapter-local pressure;
- relevant cast;
- relevant knowledge asymmetry;
- current body/resource/relationship conditions;
- tensions currently ripe;
- plausible meaningful changes;
- hard continuity anchors;
- long-direction signal if currently relevant.

A good Chapter State leaves room for discovery.

## 6. Scene State

Scene State is a living snapshot.

Recommended shape:

```yaml
scene:
  pov:
  place:
  time:
  cast: []

what_just_happened: []

entry_state:
  physical: {}
  emotional: {}
  relationship: {}

desires:
  CHAR_ID:
    immediate:
    hidden_or_unspoken:

knowledge:
  CHAR_ID:
    knows: []
    suspects: []
    wrong_about: []

pressure: []
resources_and_limits: []
possible_directions: []

exit_expectation:
  meaningful_change_types: []
```

`possible_directions` are affordances, not mandatory beats.

## 7. Character State

Stable character baseline belongs in the Bible. Runtime state belongs in memory.

Recommended fields:

- immediate goal;
- medium goal;
- dominant/secondary emotion;
- current belief;
- current bias/blind spot under pressure;
- knows/suspects/wrong-about;
- injuries/fatigue/body condition;
- resources/status;
- relationship context;
- recent consequential memories;
- current behavioral pressure.

Do not turn Character State into a deterministic behavior rule table.

## 8. Meaningful state change

A chapter does not need a fixed dramatic formula, but it should normally change something material, for example:

- information;
- position;
- danger;
- resource;
- relationship;
- commitment;
- objective;
- status;
- power/cultivation;
- belief.

This is an observation for state extraction, not a quota enforced by Writer.

## 9. Example layers

Framework uses three example layers:

```text
user-approved project finals
        ↓
project-owned curated examples
        ↓
user-calibrated framework originals
        ↓
generic framework bootstrap
```

The current framework calibration profile is:

`examples/calibration/PROFILE.md`

Its curated originals are indexed at:

`examples/calibration/index.md`

The profile was distilled from three user-supplied samples. Raw source text is intentionally not persisted. Only high-level prose mechanics are retained.

## 10. User-sample calibration protocol

When a user supplies external prose samples for calibration:

1. read enough of every sample to identify repeated prose mechanics;
2. separate **mechanics to inherit** from translation/format/source-specific artifacts;
3. write a compact derived `PROFILE.md`;
4. create new original examples for useful prose functions;
5. do not copy sample wording, imagery, scene structure, plot beats, character/world identity or distinctive rhetorical frames;
6. do not commit raw external samples unless the user explicitly owns them and asks for storage;
7. Writer normally sees selected original calibrated examples, not the raw sample corpus and not the whole calibration profile.

## 11. Current calibration mechanics

The current user calibration emphasizes:

- event-first causal movement;
- `action/fact → immediate effect → response → changed situation`;
- decision-bound reasoning rather than thought logging;
- technical exposition attached to live objects/problems;
- discovery that changes benefit/risk/choice;
- combat loop `attack → counter → collision → physical result → tactical consequence`;
- escalation by new capability, position, injury, resource or terrain;
- pragmatic status-aware dialogue;
- brief world-scale zoom-out followed by return to local action;
- simple direct emotional labeling when useful;
- natural Vietnamese rather than translated clause order.

Do not inherit convert syntax, punctuation errors, repeated connector tics, spectator spam, onomatopoeia spam or source-specific terminology.

## 12. Example Bank

Recommended story structure:

```text
examples/style/
├── index.md
├── quiet_narration_*.txt
├── dialogue_relationship_*.txt
├── combat_action_*.txt
├── cultivation_craft_*.txt
├── mystery_tension_*.txt
└── aftermath_emotion_*.txt
```

Each example should be project-owned, framework-original or explicitly approved for calibration.

## 13. Example metadata

`index.md` should describe each example by function rather than plot:

```text
ID
Function
POV distance
Tempo
Dialogue density
Description density
Reason to select
Source: project_final / project_original / user_calibration_derived_original / framework_original
```

## 14. Dynamic example selection

Normally load **one primary example**.

Add a second only if the scene genuinely combines two prose functions. Use three only for a long mixed-mode chapter.

Select by:

- scene function;
- tempo;
- POV distance;
- dialogue/action/exposition balance.

Do not select by matching character names, plot event or exact scene shape.

Preferred calibrated mapping:

- survival/tactical reasoning → `CAL-TACT-01`;
- artifact/cultivation discovery → `CAL-DISC-01`;
- high-intensity duel → `CAL-COMB-01`;
- pragmatic negotiation → `CAL-DIAL-01`;
- local event causing wider consequence → `CAL-WORLD-01`.

## 15. Calibration takeover

As project finals improve:

```text
calibrated framework originals
        ↓
project-owned examples
        ↓
user-approved/high-quality project finals
```

Once project-owned examples cover a prose function well, stop loading the framework calibration example for that function.

## 16. Originality boundary

Examples may inform high-level execution only.

Never copy or closely reproduce:

- wording;
- distinctive metaphor/image;
- rhetorical frame;
- paragraph sequence;
- scene structure;
- plot beat;
- character identity.

## 17. Writer contract

The Writer should receive a short instruction:

```text
Treat supplied state as reality, not an outline checklist.
Characters act from current desire, knowledge, emotion, relationship and limitation.
Let action, dialogue, perception and consequence carry the scene.
Use supplied examples only to calibrate project prose feel.
Do not copy them.
Write fiction, not analysis.
```

Everything else should come from state and examples.

## 18. Anti-report principle

If prose starts reading like analysis, the solution is usually not more rules.

Prefer:

- removing unnecessary explanatory state from Writer context;
- tightening local state;
- selecting a better prose example;
- loading only one primary example instead of a style bundle;
- light prose editing after continuity passes.
