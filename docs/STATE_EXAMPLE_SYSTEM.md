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

## 9. Example Bank

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

Each example should be project-owned or explicitly approved for calibration.

Framework bootstrap examples are original samples and may be copied into a new story only until project-owned examples take over.

## 10. Example metadata

`index.md` should describe each example by function rather than plot:

```text
ID
Function
POV distance
Tempo
Dialogue density
Description density
Reason to select
Source: framework_original / project_final / user_approved
```

## 11. Dynamic example selection

Normally select 1–3 examples.

Select by:

- scene function;
- tempo;
- POV distance;
- dialogue/action/exposition balance.

Do not select by matching character names, plot event or exact scene shape.

## 12. Calibration takeover

As project finals improve:

```text
framework bootstrap examples
        ↓
project-owned examples
        ↓
user-approved/high-quality project finals
```

Older bootstrap examples should stop being loaded once project examples cover the needed prose functions.

## 13. Originality boundary

Examples may inform high-level execution only.

Never copy or closely reproduce:

- wording;
- distinctive metaphor/image;
- rhetorical frame;
- paragraph sequence;
- scene structure;
- plot beat;
- character identity.

## 14. Writer contract

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

## 15. Anti-report principle

If prose starts reading like analysis, the solution is usually not more rules.

Prefer:

- removing unnecessary explanatory state from Writer context;
- tightening local state;
- selecting a better prose example;
- light prose editing after continuity passes.
