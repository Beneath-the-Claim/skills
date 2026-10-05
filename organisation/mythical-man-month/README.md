# Rules from *The Mythical Man-Month*, as a skill for coding agents

Eighteen rules from Frederick P. Brooks Jr.'s *The Mythical Man-Month* (1975, enlarged 1995): the
principles that still hold, or hold harder, now that AI agents write much of the code. The ones that
broke are listed so that an agent does not apply them by habit.

Free. One folder in the open Agent Skills format: `mythical-man-month/SKILL.md` plus six reference
files. Copy the folder into your agent's skills directory.

- Why each rule got its ruling: [the verdict](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
- The book in its own world: [the review](https://beneaththeclaim.com/writing/the-mythical-man-month-in-its-own-time/)

The skill is not affiliated with, sponsored by or endorsed by the book's author or publisher, and quotes none of the book.

## Tested

On three tasks written by someone who had not seen the skill, answers made **4.4 of 5 expected moves
with it and 3.1 without**. Three fresh runs per task and arm, answers filed under random ids, two blind
graders who agreed on every score, and six hidden control answers that scored 5 and 0 as they should.

What that means and what it does not:

- The bare model already makes about three moves in five. The skill adds the ones it does not make
  unprompted: saying where an agent is free to choose, naming one owner for the decision record,
  writing down intended behaviour for every session, taking agent hours out of a progress report.
- The test shows that answers make the moves. It does not show that the plans would work.
- Author, answering agents and graders were the same model family. Three runs a cell.

This is version four. Versions one to three, each tested on a single unseen task, scored 3.0 with the
skill against 1.8, 2.0 and 3.3 without; on the last of those the skill did not help, which is what
version four fixed.
