# Style Example Bank Template — v4.0

> Story file: `examples/style/index.md`
> Examples calibrate prose function; they never define plot.

# Framework Calibration

- Profile: `examples/calibration/PROFILE.md`
- Calibrated originals: `examples/calibration/index.md`
- Raw external reference samples are not loaded into Writer.

# Selection Rules

- Select **one primary example** by default.
- Add a second only when the scene genuinely combines two prose functions.
- Use three only for a long mixed-mode chapter.
- Priority: user-approved project final > project-owned curated > user-calibration-derived original > generic framework original.
- Select by function, tempo, POV distance and dialogue/action/exposition balance.
- Do not select because plot/character/event resembles the target scene.
- Never copy wording, distinctive imagery, rhetorical frames, paragraph sequence or scene shape.

# Calibrated Function Registry

| ID | Framework file | Function | POV distance | Tempo | Dialogue | Exposition | Source | Select when |
|---|---|---|---|---|---|---|---|---|
| CAL-TACT-01 | `examples/calibration/tactical_reasoning_01.txt` | survival/tactical reasoning | close | medium-fast | low | low-medium | user_calibration_derived_original | character must read danger and choose under pressure |
| CAL-DISC-01 | `examples/calibration/cultivation_discovery_01.txt` | cultivation/artifact discovery | close | medium | none | high-consequential | user_calibration_derived_original | information about object/rule changes benefit, risk or plan |
| CAL-COMB-01 | `examples/calibration/combat_escalation_01.txt` | duel/combat escalation | close | fast | low | low | user_calibration_derived_original | attack-counter-result loops and momentum shifts |
| CAL-DIAL-01 | `examples/calibration/dialogue_pressure_01.txt` | pragmatic dialogue/negotiation | close | medium | high | low | user_calibration_derived_original | bargaining, alliance, suspicion, status-aware talk |
| CAL-WORLD-01 | `examples/calibration/world_consequence_01.txt` | world consequence / scale transition | close → brief zoom-out → close | medium | none | medium | user_calibration_derived_original | local event propagates into factions, economy or geography |

# Generic Bootstrap Registry

| ID | File | Function | Source |
|---|---|---|---|
| EX001 | `examples/default/quiet_narration_01.txt` | quiet narration | framework_original |
| EX002 | `examples/default/dialogue_relationship_01.txt` | dialogue/relationship | framework_original |
| EX003 | `examples/default/combat_action_01.txt` | short combat/action | framework_original |
| EX004 | `examples/default/cultivation_craft_01.txt` | cultivation/craft | framework_original |

# Project Registry

Add project-specific examples here as they become authoritative.

| ID | File | Function | POV distance | Tempo | Dialogue density | Description density | Source | Select when |
|---|---|---|---|---|---|---|---|---|

# Project Takeover

When a strong project final covers a function, promote it into this registry and stop loading the framework calibration example for that function unless the user specifically wants it retained.

# Notes

- Examples should be short enough to calibrate without dominating context.
- One example should not become the universal template for every scene type.
- Calibration profile guides curation; Writer should normally see the selected example, not the full profile.
- Example curation can improve over time without rewriting historical chapters.
