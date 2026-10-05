# Rules from *Modern Software Engineering*, as a skill for coding agents

Twenty-five rules from David Farley's *Modern Software Engineering* (2021): the principles that still hold,
or hold harder, now that AI agents write much of the code. Nothing in the book broke; the principles that
bend are given in the form in which they still hold.

Free. One folder in the open Agent Skills format: `modern-software-engineering/SKILL.md` plus four reference
files. Copy the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/modern-software-engineering-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/modern-software-engineering-in-its-own-time/)

The skill is not affiliated with, sponsored by or endorsed by the book's author or publisher, and quotes none of the book.

## Tested

On three tasks written by someone who had not seen the skill, answers made **4.6 of 5 expected moves with it and
4.4 without**. Three fresh runs per task and arm, answers filed under random ids, two blind graders who agreed on
113 of 120 scores, and six hidden control answers that scored 5 and 0 as they should.

What that means and what it does not:

- The bare model already makes nearly all of these moves. Seven of the fifteen criteria scored full marks in both
  arms, and a first task that scored 5 of 5 without the skill was replaced before the test ran.
- The clearest gain is one move: writing a settled decision into the instructions every agent reads at the start
  of a session. No answer without the skill did it; every answer with the skill did.
- The skill also cost something. On one task it scored lower (4.2 against 4.5): one answer kept a manual sign-off
  for costly changes and framed the change as a trial, but never proposed measuring the sign-off it kept, a move
  every answer without the skill made.
- The gain is 0.2 of a point. The test shows that answers make the moves. It does not show that the plans would
  work.
- Author, answering model and graders were the same model family. Three runs a cell, one skill version, one run of
  the test.

The skill was written against what the bare model leaves out: on three tasks it already protected the main
branch, used a merge queue, kept feedback under ten minutes, quarantined flaky tests, shrank batches, paired
speed with stability and had people write worked examples before the agent started. It did not read the
agent's tests as feedback on the design, make every new test fail first for a stated reason, write down the
interfaces between parallel agents' areas, refuse proxy targets and check that no test was loosened, write
the learning down for the next session, spend design care where change is still expensive, or run a change
to how the work runs as an experiment with a written prediction. Those are the six rules in `SKILL.md` and
rule 19 in `references/measuring-agent-work.md`.
