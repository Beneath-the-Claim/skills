# Splitting a system, sizing services, and asking whether to split at all

**21. Weigh the reasons to keep services together every time a split is proposed.** (Granularity disintegrators
and integrators, chapter 7: *strengthens*; Four granularity integrators, chapter 7: *strengthens*.) Agents remove
the labour that once made a split expensive enough to deter it. The integrators, shared transactions, workflow,
shared code and data relationships, are the brake left, and each prices what a cut costs at runtime.

**22. Split only for a business driver, however cheap the split.** (Break apart only for business drivers, chapter
3: *strengthens*; The five modularity drivers, chapter 3: *bends*.) A model drafts a persuasive business case in
seconds, so check that the driver is real and name who is accountable for it. With agents writing the code,
testability and deployability carry most of the speed to market.

**23. Ask whether you built many services or one.** (Architecture quantum, chapter 2: *strengthens*; A common
coupling point makes one quantum, chapter 2: *strengthens*; Big ball of distributed mud, chapter 3: *strengthens*.)
A shared database, or a shared model gateway, still makes one quantum, and services that deploy together belong
together. Cheap splitting makes distributed mud cheap too.

**24. Prefer modularity without distribution until a driver demands distribution.** (Modularity does not require
distribution, chapter 3: *strengthens*; Architectural modularity, chapter 3: *holds*.) In a modular monolith an
agent changes caller and callee in one tested commit, inside firm module walls, with no distributed transaction.

**25. Size modules for agents and services for runtime.** (Modularity versus granularity, chapter 7: *holds*;
Splitting on single responsibility alone, chapter 7: *strengthens*.) Small modules suit an agent's context; the
trouble of distribution still comes from the size of the deployed parts. Single responsibility alone, or an agent's
context window, is no reason to split a service.

**26. Keep one unit of work in one service.** (Database transactions integrator, chapter 7: *strengthens*; Workflow
and choreography integrator, chapter 7: *strengthens*.) If the business needs a change to succeed or fail as a
whole, keep it in one service; agent tasks that cross fine-grained services multiply part-way failures.

**27. Split for load, failure and security as before, and give sensitive operations their own service when agents
call them.** (Six granularity disintegrators, chapter 7: *holds*; Security disintegrator, chapter 7: *strengthens*;
Scalability and throughput disintegrator, chapter 7: *holds*; Fault tolerance disintegrator, chapter 7: *holds*.)

**28. Read version control for business change, not agent churn.** (Code volatility disintegrator, chapter 7:
*bends*.) Volatile code can earn its own service, but agents inflate the commit count; count the changes the
business asked for.

**29. Split by variant once growth shows.** (Extensibility disintegrator, chapter 7: *bends*.) Agents make a later
split cheaper, so waiting costs less than it did.

**30. After a split, check what is left.** (Check the remaining service's cohesion, chapter 7: *bends*.) A fluent
name from a model proves nothing about cohesion.

**31. Write a whole-system plan before the first extraction.** (Elephant Migration anti-pattern, chapter 4:
*strengthens*; Service-based architecture as a stepping-stone, chapter 4: *holds*.) When each extraction is cheap,
the plan is what prevents distributed mud; coarse domain services first still teach you where to split.

**32. Give a mess structure before you split it.** (Shore up structure before restructuring, chapter 4: *bends*;
Architectural decomposition decision tree, chapter 4: *bends*; Component-based decomposition, chapter 4: *holds*.)
Agents make fixing the foundation cheaper, so it pays off more often; whether the codebase is worth saving stays a
judgement.

**33. Count who depends on shared code before an agent moves it.** (Afferent and efferent coupling, chapter 4:
*holds*; Distance from the main sequence, chapter 4: *holds*.) An agent's context will not show every dependant,
and a structural number can be checked where a model's review is an opinion.

**34. Gather duplicated domain logic, and enforce the dependency rules.** (Gather Common Domain Components pattern,
chapter 5: *strengthens*; Determine Component Dependencies pattern, chapter 5: *strengthens*.) Agents copy business
logic freely and add the dependency they need; only a written, enforced rule says a dependency is forbidden.

**35. Have the business confirm the domains.** (Identify component domains with business stakeholders, chapter 5:
*strengthens*; Create Component Domains pattern, chapter 5: *holds*.) A model can group the components; only the
business can say the grouping is right. Name each domain in the namespace, where agents see it.

**36. Size components against each other, and against what an agent can hold.** (Identify and Size Components
pattern, chapter 5: *bends*.)

**37. Deploy small units often, with small, fast test suites.** (Deployability: ease, frequency and risk, chapter 3:
*strengthens*; Testability: a smaller testing scope, chapter 3: *strengthens*.) Tests are how agents check their
own work, and agents multiply changes: a big release carries a bigger, riskier batch.

**38. An agent front end over every service is one quantum, unless each tool is optional.** (A coupled user
interface makes one quantum, chapter 2: *bends*; Dynamic coupling: how quanta communicate, chapter 2:
*strengthens*.) Every synchronous call ties two parts' limits together, and an agent caller and the services it
calls are far less evenly matched.

**39. Version an agent service's prompt and model like code.** (Service: independently deployed functionality,
chapter 1: *bends*; Static coupling: how services are wired, chapter 2: *holds*.) An agent service changes when its
prompt or model changes, and what it needs to start includes a model version.
