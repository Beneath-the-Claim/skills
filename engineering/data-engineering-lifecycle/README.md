# Rules from *Fundamentals of Data Engineering*, as a skill for data engineers whose pipelines agents write and whose data agents read

Rules from *Fundamentals of Data Engineering* by Joe Reis and Matt Housley (2022): the principles of the data
engineering lifecycle and its undercurrents that still hold, or hold harder, now that AI agents write much of the
pipeline code and read the data. One piece of advice broke because of agents, and one more because of better tools;
the principles that bend are given in the form in which they still hold.

Free. One folder in the open Agent Skills format: `data-engineering-lifecycle/SKILL.md` plus five reference files.
Copy the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/fundamentals-of-data-engineering-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/fundamentals-of-data-engineering-in-its-own-time/)

The skill is not affiliated with, sponsored by or endorsed by the book's authors or publisher, and quotes none of the
book. *Fundamentals of Data Engineering* is a trademark of O'Reilly Media, Inc.

## Tested

Tested three times, one version at a time, each on three tasks the skill had never seen, written by someone who had
read only the verdict, each task answered three times with the skill and three times without, and scored blind against
criteria fixed in advance. The first version raised the share of expected moves from 1.9 to 2.3 of 5, the second from
2.5 to 2.9, and the third, this one, made no difference: 1.9 with it and 1.9 without.

Without it, the model already makes most of what the verdict asks: it keeps the checks that judge an agent's run out of
the agent's reach, locks a definition once its owner approves it, and keeps record-level data inside the platform.
Each version added moves it names, among them people-time for running the connectors agents write, and each cost a few
the model makes on its own, for example an analyst reproducing a pattern an agent reports before anyone acts on it.

The skill was written against what the bare model leaves out on three tasks of my own: it already capped what an
agent can spend, defined each metric once with its owner, ran an assistant's queries under the asking user's
identity, gated an assistant on an evaluation set, streamed only what an action needed, kept managed connectors for
running them and replaced a wrangling tool with tested parsing code, but it did not name the stage a pipeline serves
or walk its six undercurrents, ask what each table is for and retire the unused ones, bound an agent's access in
time, tie each agent action to a person, plan to undo an agent's bad write, trace a number by lineage, or keep the
data in an open base under a replaceable AI layer. Those are the seven rules in `SKILL.md`. A first test on unseen
tasks found moves the verdict names that the rules left out, and one sentence that pushed out the model's own advice
to keep its SQL portable; a second version added those moves and dropped that sentence, and its test showed the new
moves crowding out four the model makes on its own. This version names those four among the model's own moves; its
own test, on three fresh tasks, is the third result above.
