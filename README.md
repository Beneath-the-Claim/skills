# Skills from Beneath the Claim

Free skills for AI coding agents, each built from a book reviewed on
[Beneath the Claim](https://beneaththeclaim.com/writing/series/books/). Every book gets a review in the world it
was written for and a verdict on which of its ideas still hold now that agents write much of the code. A skill
carries the principles that held into the agent's own context, and lists the ones that broke so an agent does
not apply them by habit.

Each skill is one folder in the open [Agent Skills](https://agentskills.io/specification) format: a `SKILL.md`
plus reference files. Each was tested once, on three tasks written by someone who had not seen it; the result,
with what it does and does not show, is in the skill's README.

## Skills

Expected moves made out of 5, with the skill and without it.

### Engineering

| Skill | Book | With | Without |
|---|---|---|---|
| [`domain-driven-design`](engineering/domain-driven-design/) | Eric Evans, *Domain-Driven Design* (2003) | 4.2 | 2.3 |
| [`modern-software-engineering`](engineering/modern-software-engineering/) | David Farley, *Modern Software Engineering* (2021) | 4.6 | 4.4 |
| [`programmer-craft`](engineering/programmer-craft/) | Andrew Hunt and David Thomas, *The Pragmatic Programmer* (1999, 2019) | 4.6 | 4.0 |

### Organisation

| Skill | Book | With | Without |
|---|---|---|---|
| [`mythical-man-month`](organisation/mythical-man-month/) | Frederick P. Brooks Jr., *The Mythical Man-Month* (1975, 1995) | 4.4 | 3.1 |

## Install

**Claude Code**, as a plugin from this repository:

```
/plugin marketplace add Beneath-the-Claim/skills
/plugin install domain-driven-design@beneaththeclaim
```

**Any agent that reads Agent Skills** (Claude Code, GitHub Copilot, Cursor, Codex, Gemini CLI and others): copy
the skill's folder, for example `engineering/domain-driven-design/`, into your agent's skills directory.

**Claude apps**: upload the skill's folder as a zip in Claude's skill settings.

## Not affiliated

The skills are not affiliated with, sponsored by or endorsed by the books' authors or publishers. Each is a set
of rules written after reviewing the book it names; none quotes the book or carries its text. A title is named
only to say which book a skill comes from. *The Pragmatic Programmer* is a trademark of The Pragmatic
Programmers, LLC; the other titles belong to their owners.

## Licence

MIT. See [LICENSE](LICENSE).
