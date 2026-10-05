# Setting up tests, test-first work or a pipeline for agent-written code

**12. Keep the essential logic free of databases, files, networks and clocks.** (Separate essential from
accidental complexity, chapter 11: *strengthens*.) Agents work by running tests in a loop. Logic that can be
tested in memory, fast, is a quick and trustworthy loop; logic tangled with input and output is a slow, flaky one
that the agent learns to work around. Put a thin adapter at each edge and test through the port.

**13. A flaky test is worse with agents than without.** (Tests must be deterministic, chapter 9: *strengthens*;
control the variables, chapter 8: *strengthens*.) An agent reads a random failure at machine frequency and learns
to retry, or to "fix" the test. Every test gives the same answer for the same code: time, randomness and order
are inputs the test controls.

**14. Agents work at the speed of the slowest test they must wait for.** (Architect for testability and
deployability, chapter 5: *strengthens*; design for testability, chapter 14: *strengthens*.) Design so that the
tests an agent runs after each change finish in seconds, and the slower suites run after merge. Code an agent
cannot test is code it cannot check: every part needs a point where its behaviour can be measured.

**15. The person writes what "right" means; the agent may add tests, never define correctness.** (Test-driven
development as talent amplifier, chapter 9: *bends*.) Worked examples written by people are the specification.
An agent writing both the code and the tests makes one mistake twice. When the agent adds tests, read them for
what they say about the design (rule 1), and check they were not changed in the same step that made them pass
(rule 3).

**16. Measure at stable seams, not through the whole system.** (Measure at stable points of measurement,
chapter 9: *holds*.) A test that drives the whole system is slow and vague about what failed. Test each part
at its interface, and keep a few whole-system tests for the paths that matter most.
