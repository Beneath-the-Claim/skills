# Where people, review and structure go, and how much to fix up front

**21. Write a one-page statement of what makes the core distinct, and start every agent from it.** (DOMAIN VISION
STATEMENT, chapter 15: *strengthens*.) It tells an agent which part needs care before it reads any code.

**22. Put the core in its own packages.** (SEGREGATED CORE, chapter 15: *strengthens*.) Agents make the move cheap,
and the result lets a review rule, a permission and a test target attach to one place.

**23. Wall off the generic parts; hand them to agents, libraries or standard components.** (GENERIC SUBDOMAINS,
chapter 15: *bends*; Four options for generic subdomains, chapter 15: *bends*.) Time zones, invoicing formats and
document storage are someone else's solved problem. Do not let agents build a bespoke one.

**24. Spend scarce review on core refactorings first.** (Choosing refactoring targets, chapter 15: *bends*.)
Agents can tidy the supporting parts under light review.

**25. Give a memoryless agent a map of the whole system, so it can place its one part.** (LARGE-SCALE STRUCTURE,
chapter 16: *strengthens*.) A short description of the layers or the responsibilities, in the agents' instructions.

**26. Let the structure change when understanding does; revise the map after each step.** (EVOLVING ORDER, chapter
16: *holds*; Imposing architecture up front, chapter 16: *bends*.) Understanding arrives late, and agents will not
resist a bad structure: they build around it faithfully. Decide the first cut, make it, then revise the boundary
map before committing to the rest. Agents make the move cheap; they do not bring the understanding sooner.

**27. Read the agents' workarounds as the complaint they will never make.** (Follow the structure once adopted,
chapter 16: *bends*.) A person pushes back on a structure that does not fit. An agent quietly works around it; the
workarounds are the signal.

**28. Someone hands-on keeps the whole structure in one head.** (Emergent structure with an informal leader, chapter
17: *bends*.) Structure does not emerge from agents that forget every session; name the person who keeps it whole.

**29. Assess first, and ask whether the map and the language are written where agents read them.** (Assess the
situation first, chapter 17: *bends*.)
