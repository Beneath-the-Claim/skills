# Running several agents at once, or scaling the number of agents

**7. Coupling, not headcount, sets how many agents can work at once.** (Manage coupling, chapter 13:
*strengthens*; coupling limits how teams scale, chapter 9: *strengthens*.) Parallel agents hit the coupling wall
sooner than teams did, because none of them holds the whole system and none of them talks to the others. Before
adding agents, find where their changes collide and decouple those parts. More agents on coupled code means more
collisions, not more output.

**8. Merge to the main line more often as agents multiply, never less.** (Continuous integration, chapter 5:
*strengthens*; feature branching defeats CI, chapter 5: *bends*.) Each agent may work on its own branch, but that
branch lands within hours. Text merges cleanly long after behaviour has drifted apart; only frequent integration
finds the conflict in behaviour.

**9. The scope of the pipeline is the unit you can deploy on its own.** (Deployability defines the scope of
evaluation, chapter 9: *holds*.) A pipeline gives a clear answer only for something that can be released alone.
If an agent's part must be tested with its neighbours before release, it is not independent, and the agents
working on it are not either. When the pipeline says a change is releasable, no further sign-off follows; add
the check to the pipeline instead.

**10. Keep one copy of a rule inside a deployable unit, and accept copies across units.** (DRY is too
simplistic, chapter 13: *strengthens*.) Inside one unit, duplicated knowledge will be updated where the agent
looks and missed elsewhere. Across independently deployable units, a shared library couples them again; a copy
with its own tests is cheaper than the coordination.

**11. Count the agents each person directs, and give each area one person.** (Organisational incrementalism,
chapter 6: *bends*; organizations are information systems, chapter 15: *holds*.) Agents are new actors in the
organisation's information system, sharing only what is written down. A person can direct only as many agents as
they can check. Each area of the code has one person who owns what its agents produce.
