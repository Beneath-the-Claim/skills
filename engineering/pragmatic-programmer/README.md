# The Pragmatic Programmer, as a skill for coding agents

Nineteen rules from Hunt and Thomas's *The Pragmatic Programmer* (1999, rewritten by the authors in
2019): the principles that still hold, or hold harder, now that AI agents write much of the code. The
ones that broke are listed so that an agent does not apply them by habit.

Free. One folder in the open Agent Skills format: `pragmatic-programmer/SKILL.md` plus six reference
files. Copy the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-its-own-time/)

## Tested

On three tasks written by someone who had not seen the skill, answers made **4.6 of 5 expected moves with
it and 4.0 without**. Three fresh runs per task and arm, answers filed under random ids, two blind graders
who agreed on every one of 120 scores, and six hidden control answers that scored 5 and 0 as they should.

What that means and what it does not:

- The bare model already makes most of these moves. Twelve of the fifteen criteria scored full marks in
  both arms. The skill adds the ones it does not make unprompted: counting the ability to replace a part
  outright when judging a design, sizing a component to one agent session, reading agent-written tests as
  a review of the design.
- The gain is 0.6 of a point and comes almost entirely from one of the three tasks. On another the bare
  answers already scored full marks, so that task measured nothing.
- The test shows that answers make the moves. It does not show that the plans would work.
- Author, answering model and graders were the same model family. Three runs a cell, one skill version,
  one run of the test.

The skill was written against what the bare model leaves out: on three development tasks it already
proposed thin slices, capped changes, a named owner and human-written acceptance examples, and did not
ask for contracts and assertions, the agent's list of design decisions, tests read as a design review,
property-based tests, or a fix to the bad pattern before the agent works near it. Those are the rules in
`SKILL.md`.
