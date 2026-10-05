# Designing, reviewing a design, choosing features

**11. Protect conceptual integrity: one set of design ideas, and good ideas left out on purpose.**
(Chapter 4: *strengthens*.) A product that reflects one set of ideas beats one that collects every
contributor's best idea. Agents will build any good idea you have, including the ones that do not fit,
so write the design ideas down, INCLUDING what is excluded, and check new work against that page.

**12. Judge a feature by fit and by what it costs after it ships, never by what it costs to build.**
(Featuritis, chapter 19: *strengthens*.) Build cost used
to be the brake on marginal features, and it is gone. The costs that remain arrive late: ease of use,
performance, support, documentation, users who now depend on it. Reject "build them all". Cut or defer
by name, for reasons of fit.
*Pitfall:* "we can always remove it later". Removing code is cheap; removing a shipped feature is not.

**12a. Treat the follow-up to a success as the dangerous release.** (The second-system effect,
chapter 5: *holds*.) The first version was lean because its designer was unsure; the second is where
every idea held back arrives at once, and cheap building removes the last brake. Say so plainly. The
remedy is a check ON the designer: give a senior person other than the designer the authority to
challenge the list and cut from it. One owner of the design does not mean an owner nobody may question.

**13. Write down who the users are and how often they will use each function.** (Define the user set,
chapter 19: *strengthens*.) Guess the frequencies explicitly: a wrong explicit guess can be corrected
and a vague one cannot. For an agent, a user who is not written down does not exist.

**14. When requests overlap or contradict, one owner resolves them in one written specification.**
(The architect as the user's agent, chapter 4: *holds*.) Do not build both sides of a contradiction and
do not settle it by vote. The test of the result is function per unit of conceptual complexity
(chapter 4: *holds*): cheap features do not make a product easier to learn.

Why these rulings: [the verdict, conceptual integrity](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
