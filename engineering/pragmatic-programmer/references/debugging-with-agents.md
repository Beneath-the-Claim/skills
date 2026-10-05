# Chasing a bug, alone or with an agent

**No failing test, no delegated fix.** (Failing test before fixing code, Topic 20: *strengthens*.) The
agent needs a target and you need proof. Reproduce the bug as a test that fails for the right reason
BEFORE asking for a fix, and keep the test (rule 14).

**Ask for the root cause, in words, before any code.** (A debugging mindset, Topic 20: *strengthens*.)
An agent will happily silence the symptom: catch the exception, special-case the input, loosen the
assertion. Ask it to explain why the bug happens and where else the same cause bites. If the
explanation does not account for every symptom, it is not the cause.

**Its confidence is not evidence; make it prove the code with this data.** (Don't assume it, prove it,
Topic 20: *strengthens*; "select" isn't broken: *strengthens*.) Suspect the code written ten minutes
ago before the compiler, the library or the platform. Time and test on the real data; a benchmark on
toy data counts for nothing (Topic 39: *holds*).

**Finish your own explanation before you listen to the agent's.** (Rubber ducking, Topic 20: *bends*.)
The duck talks back now. Explaining the problem step by step still finds the gap, but only if you
complete the explanation yourself; an agent's fluent answer arriving halfway ends the exercise.

**The agent wrote the bug, you merged it, and it is still yours to fix.** (Fix the problem, not the
blame, Topic 20: *holds*.)

When failures look random, ask what is shared, including between your agents: two sessions in one
checkout, one database, one port (Topic 34: *strengthens*).

Why these rulings: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
