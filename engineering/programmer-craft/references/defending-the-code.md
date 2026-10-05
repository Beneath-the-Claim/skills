# How much checking code needs at run time, and securing it

Rule 3 in `SKILL.md` is the core: contracts, assertions left on, crash early. The detail:

**Write the invariants that must never break where every session will read them.** (Semantic
invariants, Topic 23: *strengthens*.) "A payment is never applied twice." "A published price always has
an approver." An agent remembers nothing between sessions, so an unwritten invariant does not exist for
it. State each one once (rule 2), in the code as a check and in the brief as a sentence.

**A dead program does less damage than a crippled one.** (Crash early, Topic 24: *holds*.) Agent-written
code leans towards swallowing errors and returning a default. Ask for the opposite at every boundary
that matters: stop, say what was expected and what arrived, and leave the data untouched.

**Whoever opens a resource closes it, in the same place.** (Finish what you start, act locally, Topic
26: *holds*.) Let the language guarantee the release. One reading of the code should show both ends.

**Keeping the system small is now the security work.** (Minimise attack surface area, Topic 43:
*strengthens*.) When code costs nothing to add, every endpoint, option and dependency an agent adds is
surface. Ask what can be removed. Code that works is not code that is safe, and agents produce a great
deal of code that works.

**Give the agent less than you have.** (Least privilege, encrypt sensitive data, Topic 43:
*strengthens*.) An agent with your credentials can do whatever you can, and it reads every file it can
reach. Scoped credentials, no secrets in plain text in the repository, no production access from a
session that does not need it. Apply security patches quickly; agents shorten both the time to exploit
a flaw and your excuse for not patching it.

The authors reversed themselves here. The 1999 edition said programmers need not be "as paranoid as
spies or dissidents"; the 2019 edition says "We were wrong."

Why these rulings: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
