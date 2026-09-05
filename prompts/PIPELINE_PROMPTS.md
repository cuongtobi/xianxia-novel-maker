# Pipeline Prompts — v4.0 State + Example Driven

## P0 — Orchestrator

1. Resolve exact repo / branch / slug.
2. Read manifest and current persistent state.
3. Resolve requested range; `batch tiếp theo` defaults to 5 chapters.
4. Keep chapter intermediate work in session memory.
5. Do not expose retired creative-controller checklists to Writer.
6. Persist only after Chapter State + Scene State + Draft + Continuity PASS + Final + state/memory/manifest are ready.
7. Persist chapter using one Git tree/commit + one branch ref update.
8. Do not start next chapter until current commit verifies.

## P1 — Seed Validator

Validate user intent:

- premise/hook;
- protagonist;
- world/cultivation direction;
- target length;
- required/forbidden elements;
- romance/content boundaries;
- ending direction;
- any examples the user explicitly wants used for project calibration.

Seed is intent, not runtime state.

## P2 — Story Bible Architect

Build stable world/cultivation canon through causal logic:

`law → resource/limit → institution/behavior → conflict`

Lock only facts that need stability. Avoid turning Story Bible into chapter-writing instructions.

## P3 — Character Baseline Architect

Create stable baselines for important characters:

- identity/status;
- core desire/need/fear/blind spot;
- contradiction/value;
- voice anchors;
- relationship baselines;
- cultivation/combat identity;
- secrets;
- hard contradiction boundaries.

Do not create a giant deterministic `if situation → behavior` matrix for Writer.

## P4 — Minimal Style + Example Curator

Style Bible should stay compact and stable. Record only:

- POV/distance;
- broad tone;
- diction range;
- dialogue directness;
- prose density;
- content/style boundaries;
- originality policy;
- example-selection policy;
- active calibration profile path.

Default framework calibration profile:

`examples/calibration/PROFILE.md`

Default calibrated-original index:

`examples/calibration/index.md`

If the user supplies prose samples, distill only high-level mechanics and create original calibration examples. Do not store or feed the raw corpus to Writer by default. Filter translation/convert artifacts separately from useful narrative mechanics.

Build `examples/style/index.md` for the story. As strong project finals appear, promote them into the story example bank and let them replace framework calibration examples by prose function.

Never use an example as a plot template.

## P5 — Master Outline Architect

Build long direction, not a 500-chapter script:

- story core;
- protagonist transformation direction;
- cultivation/power progression;
- antagonist/faction escalation;
- saga map;
- mystery/reveal spine;
- relationship spine;
- major set pieces;
- soft reader expectations;
- flex zones;
- hard foreshadowing obligations.

Reader expectations are planning signals, not per-chapter quotas.

## P6 — Initial State Builder

From Genesis artifacts create:

- `memory/story_state.md`;
- `memory/arc_state.md`;
- `memory/character_states.md`;
- continuity ledgers;
- initial summaries if needed.

Run Genesis Consistency Audit across world, cultivation, character baselines, master direction and initial state.

Only then mark `READY_TO_WRITE`.

## P7 — Chapter State Deriver

Input: current Story/Arc/Character State + relevant continuity ledgers + recent summaries/final + long direction when relevant.

Output destined for `chapters/NNNN/chapter_state.md`.

Capture:

- entry reality;
- active pressures;
- relevant cast;
- knowledge asymmetry;
- body/resource/relationship conditions;
- tensions/opportunities currently ripe;
- plausible meaningful state changes;
- hard continuity anchors.

Do not prescribe beat order unless canon requires it.

## P8 — Scene State Deriver

Output destined for `chapters/NNNN/scene_state.md`.

For each scene capture:

- POV/time/place/cast;
- what just happened;
- immediate desires;
- emotional/body/relationship state;
- knowledge/suspicion/wrong belief;
- pressure/resources/limitations;
- possible directions if useful;
- exit expectation as state change type.

Scene State is reality, not a literary checklist.

## P9 — Style Example Selector

Read `examples/calibration/PROFILE.md` as curator guidance, **not** as Writer checklist.

Normally select **one primary example**. Add a second only if the scene genuinely mixes two functions. Use three only for a long mixed-mode chapter.

Selection priority:

1. user-approved project final matching the current prose function;
2. strong project-owned curated example;
3. calibrated original from `examples/calibration/`;
4. generic framework bootstrap example.

Current calibrated mapping:

- survival/tactical reasoning → `CAL-TACT-01`;
- cultivation/artifact/formation discovery → `CAL-DISC-01`;
- high-intensity duel/combat escalation → `CAL-COMB-01`;
- pragmatic negotiation/status dialogue → `CAL-DIAL-01`;
- local event → wider world consequence → `CAL-WORLD-01`.

Select by function/tempo/POV distance/dialogue-action-exposition balance, not plot resemblance.

Do not load every sample because the chapter contains multiple minor functions. Choose the dominant prose task.

## P10 — Vietnamese Xianxia Writer

Use this short contract:

> Write the next fiction from the supplied state. Treat state as reality, not an outline checklist. Characters act from their current desire, knowledge, emotion, relationship, body and limitations. Let action, dialogue, perception and consequence carry the scene. Explain reasoning only when the POV would naturally think it and when that reasoning changes a decision. Use the supplied example only to calibrate project prose feel: causal movement, rhythm, narrative distance, dialogue texture, action/exposition balance and density. Do not copy wording, imagery, rhetorical frames, paragraph sequence or scene structure. Write fiction, not analysis or report.

Writer input should be limited to:

- Chapter/Scene State;
- relevant Character State;
- minimal canon anchors;
- selected Style Example(s), normally one.

Do not attach:

- old Combined QC;
- Story Promise status matrix;
- anti-AI checklist;
- full calibration profile;
- raw user reference corpus.

For the current calibration, let prose naturally favor:

`fact/action → effect → response → changed situation`

but do not expose that as a mandatory per-paragraph formula.

Output destined for `chapters/NNNN/draft.txt`, not yet persisted.

## P11 — Continuity Checker

Read canon/state + draft.

Check only factual contradiction:

- canon/facts;
- timeline/geography;
- cultivation/power;
- item/resource/injury;
- knowledge boundary;
- relationship/faction state;
- POV identity;
- hard Character Baseline contradiction.

Decision:

- `PASS`;
- `FIX_REQUIRED`.

If FIX_REQUIRED, identify the smallest factual fix. Do not make prose-style recommendations.

Output destined for `chapters/NNNN/continuity_check.md`.

## P12 — Factual Fix

Run only if P11 = `FIX_REQUIRED`.

Patch contradictions with the smallest change that preserves scene intent. Recheck failed facts only.

No full literary rewrite.

## P13 — Prose Editor

Input: continuity-safe draft + the same selected example(s) used by Writer.

Edit only where prose materially benefits.

Preserve:

- events;
- character decisions;
- dialogue intent;
- scene shape;
- state consequences;
- useful irregularity in sentence/paragraph rhythm.

Legitimate edits:

- remove explanation the scene already demonstrates;
- compress reasoning that has become a report instead of a decision process;
- repair unnatural Vietnamese/convert-like clauses;
- trim obvious repetition;
- improve local spatial/causal clarity;
- restore concrete consequence when a sentence becomes abstract.

Prefer leaving good prose untouched.

Do not:

- standardize paragraph length;
- manufacture punchy fragments;
- add aphorisms;
- make every character equally articulate;
- add plot/state;
- copy examples;
- imitate translation errors, connector tics, spectator spam or onomatopoeia spam from source samples.

No prose-edit report required. Candidate becomes Final.

## P14 — State Extractor

Read Final as truth and prepare:

- canon updates if stable facts were created;
- Story State;
- Arc State;
- affected Character States;
- affected continuity ledgers;
- compact Chapter Summary;
- batch/arc/saga summary at boundaries;
- manifest pointers.

Do not import events removed during edit.

## P15 — Atomic Git Committer

1. use chapter-start HEAD/tree as parent/base;
2. create blobs for all new/changed chapter/state/final/manifest files;
3. include batch audit when closing requested batch;
4. create one tree;
5. create one commit;
6. update exact story branch ref once;
7. verify HEAD + manifest/state.

## P16 — Batch Auditor

After fifth requested chapter, verify:

- all five atomic chapter commits/finals;
- all Continuity Checks PASS;
- Story/Arc/Character State current;
- knowledge/resource/relationship handoff coherent;
- unresolved obligations preserved;
- example usage has not collapsed into repeated copied scene patterns;
- project-owned finals are being promoted when they outperform framework calibration;
- next-batch handoff is clear.

No style score, payoff quota or rolling checkpoint.
