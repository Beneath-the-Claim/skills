# Domain-Driven Design, as a skill for coding agents

Thirty-eight rules from Eric Evans's *Domain-Driven Design* (2003): the principles that still hold, or hold
harder, now that AI agents write much of the code. One principle broke, and it is listed so it is not applied by
habit; the principles that bend are given in the form in which they still hold.

Free. One folder in the open Agent Skills format: `domain-driven-design/SKILL.md` plus four reference files. Copy
the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/domain-driven-design-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/domain-driven-design-in-its-own-time/)

## Tested

On three tasks written by someone who had not seen the skill, answers made **4.2 of 5 expected moves with it and
2.3 without**. Three fresh runs per task and arm, answers filed under random ids, two blind graders who agreed on
117 of 120 scores, and six hidden control answers that scored 5 and 0 as they should.

What that means and what it does not:

- The bare model already makes some of these moves: it checks a rule on the merged code, asks for enforced
  controls once something has broken, routes the core to the seniors and keeps credit decisions apart from fees.
- The gains are domain moves it leaves out: a marked core, one object that guards a rule every change passes
  through, the rules in one layer, and one vocabulary across the people, the screens and the code.
- The skill also cost something. On the task about parallel agents overselling stock, two of three answers with
  the skill relied on the guarding object and never kept two agents off the same part of the model, a move every
  answer without the skill made.
- The test shows that answers make the moves. It does not show that the plans would work.
- Author, answering model and graders were the same model family. Three runs a cell, one skill version, one run of
  the test.

The skill was written against what the bare model leaves out on three tasks of my own: it already wrote a glossary, cut services along the business, dropped shared libraries
and pinned behaviour with tests, but it did not guard a consistency rule with one root, mark the core, revise the
model before agents copied it, use the glossary in prompts as well as code, write the context map where agents
read it, or fence agents with permissions the tools enforce. Those are the six rules in `SKILL.md`.
