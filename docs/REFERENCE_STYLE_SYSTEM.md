# Reference Style System — v4.0 Compatibility Note

## 1. Status

Reference Style is no longer the primary active style mechanism.

v4.0 uses **dynamic project prose examples** as the main calibration signal.

Historical high-level reference profiles may remain in the repository for compatibility, but they should not be loaded into Writer by default.

## 2. Active hierarchy

```text
Minimal Story Style Bible
        ↓
Project Style Example Bank
        ↓
Dynamic 1–3 Example Selection
        ↓
Writer / Prose Editor
```

Project-owned/user-approved examples outrank framework bootstrap examples.

## 3. What examples may calibrate

- rhythm;
- narrative distance;
- dialogue texture;
- descriptive density;
- paragraph movement;
- action/exposition balance;
- level of explicitness;
- Vietnamese prose feel.

## 4. What examples may not transfer

- wording;
- distinctive images/metaphors;
- rhetorical frames;
- paragraph sequence;
- scene structure;
- plot beats;
- character/world identity.

## 5. Historical reference profile

`docs/reference_profiles/TIEN_NGHICH_HIGH_LEVEL_STYLE.md` is historical/optional calibration material only.

Do not use it as:

- Writer prompt;
- plot model;
- character model;
- story-DNA model;
- mandatory prose checklist.

If a migrated story already has a good project-owned style bank, do not load the historical profile at all.

## 6. Bootstrap behavior

A new v4 story may begin with original framework examples under `examples/default/`.

As soon as strong project finals/user-approved passages cover the required prose functions, promote those into `examples/style/` and retire matching bootstrap examples from active selection.

## 7. Prose Editor

Prose Editor should use examples only as calibration and should prefer leaving strong draft prose unchanged.

The editor is not a rule-enforcement pass.

## 8. Principle

Examples answer:

> What does good prose in this project feel like in practice?

They do not answer:

> What plot should happen, or what exact sentence pattern must be reproduced?
