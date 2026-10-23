# Designing a workflow or transaction across services, an agent's included

**54. Avoid a distributed transaction where you can.** (Avoid distributed transactions where possible, chapter 12:
*strengthens*; Distributed transactions are not ACID, chapter 9: *strengthens*.) Every agent task that writes to
several services is a distributed transaction without the guarantees of one database: each call commits, a failure
midway leaves systems out of step, and partial results show early.

**55. Ask whether the business needs all or nothing at all, and never put an agent step inside an atomic span.**
(Defaulting to the familiar Epic Saga, chapter 12: *strengthens*; Transactionality is the worst coupling, chapter
12: *strengthens*.) Models reach for the familiar transaction too. An atomic span that includes a model step holds
its locks for seconds or minutes and fails whenever the model does.

**56. Choose the coordination by the workflow's error conditions.** (Choose coordination by workflow complexity,
chapter 11: *strengthens*; Model error conditions, not only happy paths, chapter 11: *strengthens*.) Agent steps add
timeouts, refusals, confidently wrong output and waits for a person. A model drafts the happy path in seconds; the
error paths are where the design work now lives.

**57. Give each workflow its own orchestrator.** (An orchestrator per workflow, chapter 11: *strengthens*.) One
agent coordinating every workflow is a central service bus again.

**58. For an agent workflow, start from one orchestrator that owns the errors, with each step committing its own
work.** (chapter 12: *strengthens*.) The book calls that combination, synchronous, eventually consistent and
orchestrated, the Fairy Tale Saga.

**59. Going asynchronous is a quick diff and a hard change.** (Asynchronicity is not a simple change, chapter 12:
*strengthens*; Synchronous versus asynchronous communication, chapter 1: *holds*.) The lost ordering and the races
are as hard as ever, and tests that pass on one interleaving miss them. Agents wait on their tools and run too long
to be waited on.

**60. In choreography, every new failure becomes new wiring.** (Choreographed errors add communication links,
chapter 11: *strengthens*; Choreography communication style, chapter 11: *holds*.) Choreography still trades a
visible workflow for speed and independence; each agent failure mode adds links between services that cheap code
hides.

**61. Keep a workflow in one domain-shaped place.** (Model workflow semantics in the implementation, chapter 11:
*strengthens*; Semantic versus implementation coupling, chapter 11: *holds*.) An agent can then load all of it at
once. No agent can make a workflow simpler than the business needs it to be.

**62. Every step an agent workflow adds is one more chance to fail.** (More coupling, worse scale and availability,
chapter 15: *strengthens*.)

**63. Decide the coordination scenario by scenario, and record it.** (Decide coordination scenario by scenario,
chapter 11: *strengthens*.) A model may draft the scenario table; the business picks the scenarios and a person signs
the record.

**64. When a compensation fails, an agent may draft the repair; a person answers for it.** (Orchestrated
request-based pattern, chapter 9: *bends*; Event-based eventual consistency pattern, chapter 9: *bends*.) An agent
can clear more of a dead-letter queue than people could; people review its fixes.

**65. Eventual consistency is still the price of distribution, and agents now act inside the window.** (Eventual
consistency patterns, chapter 9: *holds*; BASE for distributed transactions, chapter 9: *holds*.) Agent workflows
are eventually consistent by nature, and their soft state lasts longer; another agent may act on intermediate data
within seconds.

**66. A reconciler that writes everyone's tables couples everything.** (Background synchronization pattern,
chapter 9: *holds*.) That holds whether a batch job or an agent runs it.

**67. Saga machinery can be bought; which services join which saga must still be written down.** (Techniques for
managing sagas, chapter 12: *bends*.)
