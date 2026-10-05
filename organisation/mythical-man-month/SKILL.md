---
name: mythical-man-month
description: Use when planning or rescuing a late software project, deciding whether to add people or AI coding agents to a schedule, estimating, splitting work across engineers or parallel agents, reviewing a design or a feature list for coherence, deciding what to build when building is cheap, writing a specification or context for coding agents, growing a system incrementally, or judging a productivity claim for a tool. Applies the principles of Frederick P. Brooks Jr.'s The Mythical Man-Month that still hold now that AI agents write much of the code, and leaves out the ones that broke.
---

# The Mythical Man-Month, for teams that work with coding agents

Eighteen rules from Brooks's book (1975, enlarged 1995). Only principles that were judged to
**strengthen**, **hold** or **bend** in the age of AI coding agents are here; what broke is listed at
the end so that you do not apply it by habit. Each rule names its chapter and its ruling.

Do not recite Brooks at the user. Make the move the rule calls for, in the user's own situation, and
say why in one sentence.

**These rules ADD to your own judgement; they never replace it.** If you already see a sound reason or
a sound move, keep it and give it, then add what the rule brings. An answer that drops its own best
argument to make room for a rule is a worse answer.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| behind schedule, estimating, or asking whether to add people or agents | `references/late-project.md` |
| dividing work among engineers or parallel agents, or integrating their output | `references/splitting-work.md` |
| designing, reviewing a design, or choosing which features to build | `references/design-and-features.md` |
| writing a specification, a context file or documentation that agents will work from | `references/written-word.md` |
| starting a build, or deciding between a rewrite and growing what exists | `references/growing-a-system.md` |
| weighing a tool, a productivity claim or a metric | `references/judging-tools.md` |

Read one file, or two when the task spans them. Do not load all six.

## Eight things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not repeat
these.

1. **An agent is a worker who needs onboarding, in writing, every session.** It takes little of a
   colleague's time and all of its context from what someone wrote down. Budget for writing and
   maintaining that context the way Brooks budgeted for training.
2. **Generation is cheap; review, integration and deciding what is wanted are not.** Before proposing
   more hands of any kind, find who reviews the work and how many hours they have.
3. **Whatever is left unwritten, the agent decides for you.** Whichever file you read, ask for a short
   written specification before agents start: what the user sees, what is left out on purpose, and
   where the builder is free to choose. It goes into every session. The rules are in
   `references/written-word.md`.
4. **Say what before how, in writing.** One page states what the system does for the user and the
   interfaces between its parts. One named person owns that page, and a
   senior colleague has standing to challenge it. Engineers and agents are free on the
   implementation side of it, and only there.
5. **An agent rarely argues back, so it is never the second opinion on a design.** Agents take the
   support roles: tooling, tests, drafts, mechanical checks. A design that matters is reviewed by
   another ENGINEER.
6. **Only a check decides "done".** An agent reports success with full confidence. Use milestones that
   are concrete, 100-per-cent events, prove the check on output you know is right, and never let the
   worker that wrote the code be the only one that tests it.
7. **Keep a running system, and change it one piece at a time.** Each fix ships with its regression
   check, because each fix risks a new defect.
8. **Measure the whole job.** Verified behaviour, reviewed changes, defects, stability. Never lines,
   agent hours or a demo extrapolated to a product.

## What broke: do not apply these

- Starting implementation before the specification is done, to keep implementers busy (chapter 4). An
  idle agent costs nothing, and early code anchors the design.
- Measuring output in statements or lines (chapter 8). Count verified behaviour.
- "Plan to throw one away" (chapter 11). Brooks withdrew it himself in 1995; grow the system instead.
- "Everyone sees everything" in place of precise interfaces (chapter 7). Brooks withdrew this too:
  information hiding is right, and it is what fits in a context window.

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/). The book in its own world:
[the review](https://beneaththeclaim.com/writing/the-mythical-man-month-in-its-own-time/).
