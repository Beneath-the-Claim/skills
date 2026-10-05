---
name: domain-driven-design
description: Use when an engineering leader or engineer works with AI coding agents on business software and is naming or untangling domain concepts, stopping agents from duplicating a concept, splitting a monolith or drawing service and team boundaries, integrating with another system or model, deciding where the best people and review should go, setting up a new domain module for agents to build, or deciding how much structure to fix up front. Applies the principles of Eric Evans's Domain-Driven Design (2003) that still hold now that AI agents write much of the code, in the form in which they hold.
---

# Domain-Driven Design, for teams that work with coding agents

Rules from Eric Evans's book (2003). The book holds that the hard part of business software is the domain, not the
technology, and every principle in it was ruled on for the age of AI coding agents. Agents make code cheap and leave
the domain as hard as it was. Each rule names its chapter and its ruling.

Do not recite the book at the user. Make the move the rule calls for, in the user's own situation, and say why in
one sentence.

**These rules ADD to your own judgement; they never replace it.** You already write a glossary from the experts' own
words and give it to the agents, cut services along business capability and never along tables, drop shared
libraries of common objects for versioned contracts, give each table one owner, translate at the edge of an old
system, pin today's behaviour before changing it, turn the experts' real cases into tests the agents cannot edit,
prefer a failing build to a paragraph of guidance, and slice thin. Keep doing that and give those answers first.
Then add what the rules below bring, because they are the moves usually left out.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| fighting duplicate or drifting concepts, or setting up a glossary and agent instructions | `references/language-and-model.md` |
| splitting a system, drawing service or team boundaries, or integrating with another model | `references/boundaries.md` |
| deciding where people, review and structure go, or how much to fix up front | `references/core-and-structure.md` |
| designing the objects, rules and layers inside one module | `references/building-blocks.md` |

Read one file, or two when the task spans them. Do not load all four.

## Six things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not repeat these.

1. **Say it the same way in talk, tickets, prompts and code; when a word changes, rename the code in the same
   change.** (UBIQUITOUS LANGUAGE, chapter 2: *strengthens*; MODEL-DRIVEN DESIGN, chapter 3: *strengthens*.) An agent
   takes its words from the prompt, the documents and the code. A synonym in a ticket becomes a second class. So the
   people who brief agents use the glossary's terms, and a term that changes in a meeting changes in the code and
   the glossary in one commit.
2. **Put each cluster of objects that must stay consistent behind one root that checks its rules on every change,
   and let other code reach the cluster only through that root.** (AGGREGATES, chapter 6: *strengthens*; ASSERTIONS,
   chapter 10: *strengthens*.) A rule in one shared function is a home, not a guard: an agent working on another
   slice can still change the data around it. Several agents may edit one model at once, each seeing a part; the root
   is where a broken rule is caught, and its invariants are written as tests.
3. **Revise the model as soon as the team learns it is wrong, before agents copy it further.** (Refactoring toward a
   deeper model, Part III: *strengthens*; Listen to the domain experts' language, chapter 9: *bends*.) Agents extend
   whatever model exists at the pace they write, so a naive model left in place spreads faster than it did. Have the
   agents flag expert terms the code lacks; people decide which ones change the model, and the change goes in early.
4. **Mark the core in the repository, and send its changes to the best reviewers and the domain experts.** (CORE
   DOMAIN, chapter 15: *holds*; HIGHLIGHTED CORE, chapter 15: *strengthens*; Put top talent on the core, chapter 15:
   *bends*.) Name the small part that makes the business distinct, in a file every agent reads and in its own
   packages. Generic parts go to agents, libraries or standard components under light review; the core gets the
   scarce judgement, which agents do not supply.
5. **Write the context map where every agent session reads it.** (CONTEXT MAP, chapter 14: *strengthens*; BOUNDED
   CONTEXT, chapter 14: *strengthens*.) Each context, its owner, and how each pair relates: one conforms, one
   translates, they share a small kernel, or they go separate ways. An agent remembers nothing between sessions, and
   an edge it cannot see is an edge it will cross.
6. **Fence the agents with permissions and checks the tools enforce, and let the people who direct them step past.**
   (Frameworks that coddle developers, chapter 17: *breaks*.) A written instruction shapes what an agent tries; it
   does not enforce a boundary. Put the fence in permission rules and failing checks, around what agents may change.
   The people directing them must be able to design: someone who cannot should not be steering agents on the model
   (HANDS-ON MODELERS, chapter 3: *bends*).

## What bends: apply the changed form, not the original

- **SMART UI** (chapter 4): still fine for a trivial application, but agents now write the layered version nearly as
  fast, so the saving that justified it is small.
- **Declarative design** (chapter 10): agents turn a precise description into code in almost any aspect, but only an
  executable check makes the description binding. Pair every specification with one.
- **KNOWLEDGE LEVEL** (chapter 16): when an agent can change a rule in code today, with tests, fewer rules need to be
  data a superuser edits. Keep it where non-developers must reconfigure at run time.
- **OPEN HOST SERVICE** (chapter 14): a translator per consumer is cheap now; open a shared protocol when consumers are
  many, not merely several.
- **SYSTEM METAPHOR** (chapter 16): an agent carries an analogy further than the model fits. Give agents the precise
  terms instead.

## What broke: do not apply it by habit

- **The rejection of frameworks that fence developers in** (chapter 17). Evans rejected frameworks that prepackage
  design for weaker developers, because they fence in the capable. Agents are fallible designers, and a fence around
  what they may change costs capable people nothing if those people can step past it. Rule 6 is its new form.

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/domain-driven-design-in-the-age-of-ai/). The book in its own world: [the review](https://beneaththeclaim.com/writing/domain-driven-design-in-its-own-time/).
