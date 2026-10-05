# Specifications, context files and documentation for agents

**15. Start a small set of decision documents on day one, each short, each with an owner.** (The
documentary hypothesis, chapter 10: *strengthens*.) What, when, how much, where, who. They record
DECISIONS. A generic overview of the repository is the wrong document: keep bulk out, because
everything an agent reads spends its context window.

**16. Specify everything the user sees, and state where the builder is free to choose.** (The manual
as external specification, chapter 6: *strengthens*.) Whatever you leave unwritten, the agent will
decide for you. If both a prose specification and a test suite exist, say which one is law (chapter 6:
*strengthens*); unprompted, an agent will satisfy the tests.
*Pitfall:* letting the running prototype stand in for the specification. It shows what the system
does, and cannot show where you did not care.

**17. Document for a reader with no memory: overview first, then how to check that it works.**
(Documentation to use, believe and modify, chapter 15: *strengthens*.) Every agent session starts as a
new hire. Give the purpose and the structure before the detail, and ship small runnable cases that
prove the program works, including the edge and the just-illegal inputs.

Why these rulings: [the verdict, the written word](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
