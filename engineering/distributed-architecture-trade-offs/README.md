# Rules from *Software Architecture: The Hard Parts*, as a skill for architects whose systems include agents

Rules from *Software Architecture: The Hard Parts* by Neal Ford, Mark Richards, Pramod Sadalage and Zhamak Dehghani
(2021): the principles of its trade-off analysis that still hold, or hold harder, now that AI agents write much of
the code and run inside systems. Nothing in the book broke; the principles that bend are given in the form in which
they still hold.

Free. One folder in the open Agent Skills format: `distributed-architecture-trade-offs/SKILL.md` plus five reference
files. Copy the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/software-architecture-the-hard-parts-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/software-architecture-the-hard-parts-in-its-own-time/)

The skill is not affiliated with, sponsored by or endorsed by the book's authors or publisher, and quotes none of the
book. *Software Architecture: The Hard Parts* is a trademark of O'Reilly Media, Inc.

## Tested

On three tasks written by someone who had not seen the skill, answers made **4.4 of 5 expected moves with it and
3.1 without**. Three fresh runs per task and arm, answers filed under random ids, two blind graders who agreed on
112 of 120 scores, and six hidden control answers that scored 5 and 0 as they should.

What that means and what it does not:

- The bare model already makes some of these moves: it treats a model's trade-off table as a draft, knows that a
  strict schema fixes only the shape of a call, puts contract tests in the providers' builds, and disputes that
  agents keep copies of code identical for free.
- The gains are moves it leaves out: a record of each decision where the coding agents read it, the steps that
  cannot wait for the data to agree, tool descriptions tested like code, and a tracked record of every copy of shared
  code with a check that fails when one drifts.
- The skill also cost something. On the task about a model-drafted move to events, every answer without the skill
  said that the agents' cheap build leaves the design's running cost unchanged; with the skill, most answers did not.
- The test shows that answers make the moves. It does not show that the plans would work.
- Author, answering model and graders were the same model family. Three runs a cell, one skill version, one run of
  the test.

The skill was written against what the bare model leaves out on three tasks of my own: it already took the control
flow away from a model, made writes idempotent, gave each table one owner, asked for a driver behind every split and
turned rules into checks that fail the build, but it did not record who decided and what was traded away, set
communication, consistency and coordination as one choice, write a saga as a state table, hold irreversible steps for
a person whatever their amount, make the contracts agents call strict and narrow, give a characteristic a number,
map the coupling agents add at runtime, or confirm a delegated write. Those are the eight rules in `SKILL.md`.
