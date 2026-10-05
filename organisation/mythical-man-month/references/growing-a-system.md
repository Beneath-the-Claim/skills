# Starting a build, or a rewrite against growing what exists

**18. Build an end-to-end skeleton first and keep it running at every step.** (Grow, don't build,
chapters 16 and 19: *strengthens*.) Start with a path through the whole system made of stubs. Add
function in small pieces, each with a check the agent can run. A running system is the only thing a
fallible worker can be checked against. **The check has to be one you trust**: the agent's work is
judged against it, so a weak check gets the wrong problem solved with full confidence. Prove the check
on output you know is right (the old system's real results, a hand-worked case) before agents work to
it, and keep it where the agent cannot edit it. Discard failed attempts freely; never discard the running
system.
*Do not* "plan to throw one away" (chapter 11): Brooks withdrew that advice in 1995 because it assumes
one pass from specification to delivery.

**Also apply**

- Build plenty of scaffolding, and integrate only debugged components (chapter 13: *strengthens*).
  Agents made scaffolding cheap, so the old excuse for skipping it is gone.
- Design for change with precise, documented interfaces between modules (chapter 11: *strengthens*).
  The interfaces and documents are the agent's memory between sessions.
- Expect each fix to risk a new defect (chapter 11: *strengthens*). Every fix ships with its regression
  check.

Why these rulings: [the verdict, grow, don't build](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
