# Reviewing, testing or merging what an agent produced

**11. A human who agreed to own it signs it.** (Take responsibility, Topic 2: *strengthens*; sign your
work, the Postface: *strengthens*.) An agent cannot be held to anything and will not remember the failure.
Before merge there is one named person who accepted the outcome and can explain every decision in the
change (rule 4). "The agent wrote it" is the old excuse in a new form.

**12. Green tests from an agent loop are a coincidence until someone can say why.** (Don't program by
coincidence, Topic 38: *strengthens*; test-driven development and its traps, Topic 41: *strengthens*.)
An agent will make every test pass, including by weakening the test. Check that a test can fail: break
the rule on purpose and watch it go red. Check that the tests were not edited in the same change that
made them pass.

**13. Add properties where one author wrote both the code and the tests.** (Property-based testing,
Topic 42: *strengthens*.) One author makes one mistake twice; random inputs do not share it. For
anything with an invariant (a total never goes negative, parsing then formatting returns the input,
an order is preserved) ask for a property-based test that states the invariant, as well as the
examples.

**14. Done is decided by the build running every test.** (The pragmatic starter kit, Topic 51:
*strengthens*; find bugs once: *strengthens*.) Version control, regression tests and full automation
are the guardrails that make agent speed safe. Every bug found becomes a test, because the agent
forgets it at the end of the session. Coverage an agent reached by lunchtime says nothing about the
states that were never tested (test state coverage: *holds*).
*Pitfall:* asking an agent to repeat a manual procedure each time is still a manual procedure (Topic
51: *bends*). Put it in a script.

Why these rulings: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
