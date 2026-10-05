# Designing code, data or interfaces that agents will keep changing

**21. Build only what today's problem needs.** (YAGNI, not future-proofing, chapter 12: *strengthens*.) Agents
make later change cheaper, so the case for guessing the future is weaker than ever. Abstraction manages the
complexity in front of you; safety later comes from tests and code that is cheap to change.

**22. Hide what is likely to change behind a stable interface, and keep one level of abstraction in a place.**
(Abstraction and information hiding, chapter 12: *strengthens*; consistent level of abstraction, chapter 11:
*holds*.) Information hiding is how an agent changes one part without reading the whole. A low-level call among
business logic costs an agent context as it costs a person attention.

**23. Everything a service exposes is its interface.** (An API is all exposed information, chapter 11:
*strengthens*.) Formats, field names, error messages and timing that another program or agent reads are part of
the contract. Change them as you would change a public function: versioned, announced, with the old form kept
until its readers have moved.

**24. Do not rebuild the waterfall around agents.** (Production is not our problem, chapter 2: *strengthens*.)
With code nearly free to produce, the work is even more about finding out what to build. A long specification
handed to an agent to "produce" is the staged handover the book warns against: keep specifying, building and
learning in small loops, and let what users do change the plan.

**25. Where change still costs, design with care; where it does not, redo freely.** (Flatten the cost of change
curve, chapter 4: *bends*.) Rewriting code is cheap now. A schema change, a data migration, a public format or a
change to how users work is not: slow down there, and plan the move.
