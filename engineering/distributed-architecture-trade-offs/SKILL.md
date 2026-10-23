---
name: distributed-architecture-trade-offs
description: Use when a software architect or tech lead designs, changes or governs a distributed system that AI agents help build or run inside, and is splitting a monolith or sizing services, assigning who owns data, designing a workflow or transaction that crosses services (an agent's own workflow included), choosing between orchestration and choreography, setting the contracts that services and agents call, deciding how to share code, or keeping architecture decisions intact while agents write much of the code. Applies the trade-off analysis of Ford, Richards, Sadalage and Dehghani's Software Architecture: The Hard Parts (2021), in the form in which it holds now that agents write code and run inside systems.
---

# Rules from Software Architecture: The Hard Parts, for architects whose systems include agents

Rules from the book by Neal Ford, Mark Richards, Pramod Sadalage and Zhamak Dehghani (2021). The book holds that a
distributed architecture has no best practices, only the least worst combination of trade-offs for a context, and
every principle in it was ruled on for the age of AI agents. Agents make every split, every saga and every trade-off
table cheap to produce, so what binds harder is what a boundary costs at runtime and the record of who decided it.
Nothing in the book broke. Each rule names its chapter and its ruling.

Do not recite the book at the user. Make the move the rule calls for, in the user's own situation, and say why in
one sentence.

**These rules ADD to your own judgement; they never replace it.** You already take the control flow away from a
model and run the workflow in code with the agent proposing inside it, make writes idempotent, put the steps that
cannot be undone last, give each table one owner and end direct reads of another service's database, ask for a
business driver behind every split and check what changes and writes together, pin and version shared libraries
and run their consumers' tests, turn rules into checks that fail the build, and roll out in stages. Keep doing that
and give those answers first. Then add what the rules below bring, because they are the moves usually left out.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| making, recording or enforcing an architecture decision, or weighing options | `references/decisions-and-governance.md` |
| splitting a system, sizing services, or asking whether to split at all | `references/splitting-and-sizing.md` |
| pulling data apart, assigning who owns a table, or giving services and agents access to data | `references/data-ownership-and-access.md` |
| designing a workflow or transaction across services, an agent's included | `references/workflows-and-sagas.md` |
| designing contracts, sharing code, or building analytical data | `references/contracts-reuse-and-analytical-data.md` |

Read one file, or two when the task spans them. Do not load all five.

## Eight things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not repeat these.

1. **Write the decision record before an agent builds on the decision, and have a named person decide it.**
   (Architectural Decision Records, chapter 1: *strengthens*; Finding the right balance, chapter 7: *strengthens*;
   Least worst combination of trade-offs, chapter 1: *holds*.) An agent remembers nothing between sessions except
   what is written down, and a model drafts a record or a trade-off table in seconds, so records nobody decided
   multiply. Each record states the choice, the trade-off accepted, what was given up, who decided and what would
   reopen it, and sits where every agent session reads it. A model's analysis is a first draft until someone with
   the context and the accountability has chosen.
2. **Give every architecture characteristic a number, and every rule a check the agents cannot edit.** (Objective,
   measurable architecture characteristics, chapter 1: *strengthens*; Architecture fitness functions, chapter 1:
   *strengthens*; Fitness functions as an executable checklist, chapter 1: *strengthens*.) An agent cannot meet
   "fast" or "loosely coupled"; it can meet a threshold a check tests on every change. A check an agent may edit or
   disable is a suggestion, so changes to the checks go to a person.
3. **Give every table one writing service, give agents that service's tool, and have an agent confirm a write
   before it reports one.** (Assigning data ownership, chapter 9: *strengthens*; Ask the owning service, not its
   database, chapter 6: *strengthens*; Delegate technique, chapter 9: *strengthens*.) An agent takes the shortcut a
   database tool puts one call away. When it asks an owner to change data, the request can be lost, delayed or
   applied twice, so it reads the result back before it says the work is done.
4. **Set communication, consistency and coordination together, on purpose, for every workflow that crosses
   services, and have the business choose the consistency.** (Dynamic coupling's three forces and eight sagas,
   chapter 2: *strengthens*; Atomicity versus eventual consistency, chapter 1: *strengthens*; Data and
   transactionality as architecture concerns, chapter 1: *strengthens*.) Name the combination (synchronous or
   asynchronous, atomic or eventual, orchestrated or choreographed) and what the nearest alternative would cost. An
   agent's own workflow is one of these, and an agent framework's defaults choose all three if nobody does. Ask the
   owner of the business outcome how long the data may disagree and what undoing a step means.
5. **Make every contract an agent calls strict and narrow, and test its prose.** (Strict versus loose contracts,
   chapter 13: *holds*; Over-coupling via stamp coupling, chapter 13: *strengthens*; Consumer-driven contracts,
   chapter 13: *strengthens*.) A typed schema fixes the shape of a call and nothing more; the tool's description is
   prose the agent acts on, so test it as you test code. Give each agent step only the fields it needs. Put each
   consumer's tests in the provider's build, editable only by that consumer.
6. **Map the coupling agents add at runtime.** (Static and dynamic coupling, Part I: *holds*; Inter-service
   communication erodes modularity's gains, chapter 3: *strengthens*.) An agent that chooses its tools at runtime
   couples to every service it calls, and no build file shows it. Map calls from traces as well as from code, count
   the synchronous hops one agent task chains, and alert on a new link.
7. **Before agents implement a saga, write it as a state table.** (Saga state machines, chapter 12: *strengthens*;
   Workflow state management, chapter 11: *bends*.) List every state, trigger, action and error state, including
   waiting for a person; agents build and test one transition at a time from it. Keep the state where any session
   can query it, because an agent workflow outlives the session that started it.
8. **Keep the orchestrator deterministic with agents inside its steps, compensate what cannot be rolled back, and
   hold any step nothing can reverse for a person's approval.** (Orchestration communication style, chapter 11:
   *bends*; Compensating updates and their costs, chapter 12: *strengthens*; State management and eventual
   consistency, chapter 12: *strengthens*.) A model in the orchestrator's place gives up the predictable state,
   error handling and recovery the orchestrator was chosen for. Irreversibility, not the amount, decides which steps
   wait for a person: an email, a payment or a deletion cannot be compensated. Where an action cannot be undone,
   record where the saga stands and repair forward.

## What bends: apply the changed form, not the original

- **Fork, then refactor.** Agents make the clean-up of a forked monolith cheap, so forking suits more codebases;
  each fork still inherits the monolith's code, so plan the refactoring it needs. (Tactical forking, chapter 4:
  *bends*.)
- **Replicate only what you track.** Agents make fixing every copy cheap but not finding them, and they copy code
  unasked, so keep a record of every copy. (Code replication, chapter 8: *bends*.)
- **Shared code argues less for merging services.** Agents can update every consumer of a shared library at once; a
  change that cannot be versioned still argues for one service. (Shared code integrator, chapter 7: *bends*.)
- **A merged service is still one service.** Agents absorb the wider testing a merged service needs; it still
  fails, deploys and scales as one. (Service consolidation technique, chapter 9: *bends*.)
- **Every check on every change, a person only where it is sensitive.** Run every automated check on every change,
  and keep a person's sign-off for the changes that touch sensitive parts. (Run fitness functions continually,
  chapter 1: *bends*.)
- **Back a loose contract with tests.** A loose contract still decouples, but an agent reading one guesses.
  (Loose contracts: decoupling for fidelity, chapter 13: *bends*.)
- **Domains own the meaning; agents can do more of the building.** (Data mesh, chapter 14: *bends*.)

## Nothing broke

No principle in the book breaks, by agents or otherwise. The nearest is code replication, which bends (above). Do not
read "cheap to build" as "free to run": every split, saga and copy an agent makes cheaply still costs at runtime
what the book says it costs.

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/software-architecture-the-hard-parts-in-the-age-of-ai/). The book in its own world: [the review](https://beneaththeclaim.com/writing/software-architecture-the-hard-parts-in-its-own-time/).
