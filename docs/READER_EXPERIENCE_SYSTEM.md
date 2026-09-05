# Reader Experience System — v4.0 Compatibility Note

## 1. Status

The old **Story Promise Controller** is retired as an active controller in v4.0.

Reader expectations are still useful, but they now live as **soft planning state** rather than a per-chapter scoring/enforcement system.

## 2. New role

Reader expectation answers:

> What did the reader come to this story to experience over time?

Examples:

- cultivation ascent;
- alchemy competence;
- rivalry/payback;
- mystery/reveal;
- romance/relationship growth.

These signals help Story/Arc State notice what has been neglected or what is naturally ripe. They do not command Writer to produce a specific payoff.

## 3. Suggested state fields

In Master Outline or Story/Arc State:

```text
ID
Expectation
Reader value
What meaningful delivery looks like
Last meaningful delivery
Current pressure
Natural opportunity ahead
Notes
```

No required `UNTOUCHED / ADVANCE / PAY_*` status in active v4 production.

## 4. No drought-clearing behavior

Do not force a fake payoff because a numeric drought threshold was reached.

If an expectation has been neglected, the Arc State may record that pressure and expose a future opportunity. The next chapter should still follow current character/world state naturally.

## 5. Writer boundary

Writer should not receive a reader-expectation matrix unless one short expectation is directly relevant to local state.

Even then it should be represented as story reality/pressure, not as a metric target.

## 6. Migration from v3.x

Historical Story Promise data may remain.

Useful conversion:

- `Promise` → `Reader Expectation`;
- `last_pay_chapter` → `last meaningful delivery`;
- `next planned payoff window` → `natural opportunity ahead`;
- `pay_drought` → optionally a qualitative note such as `neglected / active / recently delivered`.

Do not continue status enforcement after migration.

## 7. Principle

Reader experience informs **where the story may want to move**.

It does not dictate **how the Writer must manufacture a chapter**.
