---
name: modern-software-engineering
description: Use when an engineering leader or engineer works with AI coding agents and is scaling the number of agents on a codebase, splitting work between parallel agents, setting up tests or a pipeline for agent-written code, measuring whether an AI rollout is working, deciding what to optimise for, or designing code, data and interfaces that agents will keep changing. Applies the principles of David Farley's Modern Software Engineering (2021) that still hold now that AI agents write much of the code, in the form in which they hold.
---

# Modern Software Engineering, for teams that work with coding agents

Rules from David Farley's book (2021). The book asks engineers to be experts at two things, learning and
managing complexity, and every principle in it was ruled on for the age of AI coding agents. None broke; many
strengthen, and some bend, so they are given here in the form that still holds. Each rule names its chapter
and its ruling.

Do not recite the book at the user. Make the move the rule calls for, in the user's own situation, and say why
in one sentence.

**These rules ADD to your own judgement; they never replace it.** You already know to protect the main branch,
put changes through a merge queue, get feedback under ten minutes, quarantine flaky tests, shrink batches, pair
speed with stability, treat lines of code as a cost, pull business rules into a pure core, pin today's behaviour
before changing it, and have people write worked examples as tests before the agent starts. Keep doing that and
give those answers first. Then add what the rules below bring, because they are the moves usually left out.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| running several agents at once, or scaling the number of agents | `references/parallel-agents.md` |
| setting up tests, test-first work or a pipeline for agent-written code | `references/tests-and-design.md` |
| judging whether agents are helping, or choosing what to measure | `references/measuring-agent-work.md` |
| designing code, data or interfaces that agents will keep changing | `references/designing-for-change.md` |

Read one file, or two when the task spans them. Do not load all four.

## Six things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not repeat these.

1. **Read the agent's tests as the design talking.** (Test-driven development as talent amplifier, chapter 9:
   *bends*; design for testability, chapter 14: *strengthens*.) A test that is hard to write means the design is
   poor, but the agent never feels that: it writes the mocks and the set-up without complaint. So a person reads
   the tests for that signal. Heavy set-up, many mocks, or a test that must reach through several objects means
   the unit is too coupled: fix the design, not the test.
2. **Make every new test fail first, for the reason stated before the run.** (TDD as a series of experiments,
   chapter 8: *strengthens*; watch the test fail, chapter 8: *bends*.) Before the agent writes code, it states
   what the new test should fail with, runs it, and shows that failure. A test that passes at once, or fails for
   another reason, checks nothing. People keep the predictions for the acceptance tests.
3. **Never hand an agent or a team a proxy target; say what you expect before a change, and check it after.**
   (Design it into the experiment, chapter 8: *strengthens*; control the variables, chapter 8: *strengthens*;
   speed of feedback as fitness function, chapter 14: *bends*.) An agent given a coverage figure, a deploy count
   or a test that must pass will hit that number, if need be by weakening the test. Name the real outcome, write
   down what a change to the work should do to it before you make it, and after it check that no test was
   loosened, skipped or deleted to buy the speed.
4. **Write the learning down where the next session will read it.** (Iteration drives learning, chapter 4:
   *bends*; inspect and adapt, chapter 5: *bends*; experts at learning and managing complexity, chapter 15:
   *strengthens*.) An agent forgets everything between sessions, so iteration teaches no one unless the lesson is
   written into the repository's instructions for agents, in the same change that taught it: the decision, the
   trap, the "do not do X here, do Y".
5. **Before parallel agents split the work, write down the interfaces between their areas, and choose coordinate
   or distribute.** (Modularity with agreed interfaces, chapter 6: *strengthens*; coordinate or distribute,
   chapter 13: *holds*; coupling limits how teams scale, chapter 9: *strengthens*.) Parallel agents can work
   independently only where the contract between their parts is agreed and written. Then pick one of two: keep
   one codebase and make checking the whole of it fast enough for every change, or split it into parts each
   deployable on its own behind a fixed, written contract. The middle ground, separate parts that must still be
   tested together, is slower than either.
6. **Spend design care where change is still expensive.** (Flatten the cost of change curve, chapter 4: *bends*;
   an API is all exposed information, chapter 11: *strengthens*.) Agents make rewriting code cheap. Stored data,
   public interfaces, and users' habits cost what they did, and an interface is everything another program or
   agent reads, including formats and error text. Design those with care; let the rest stay cheap to redo.

## What bends: apply the changed form, not the original

Nothing in this book broke. These bend, and the rules above and in the reference files carry their new form:

- **Stability and throughput** (chapter 3) are still the right pair, but agents can raise throughput on volume
  alone: read it beside rework and the people reviewing the work.
- **Feature branches defeat continuous integration** (chapter 5): give each agent its own branch, but merge it
  within hours; text merges easily, behaviour does not.
- **The coordinated approach** (chapter 13): one repository with every change checked together, scoped to what
  the change can affect, so the check stays fast as agents multiply.
- **Organisational incrementalism** (chapter 6): small autonomous teams still, but count the agents each person
  directs, and write down the steps the agents follow.

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/modern-software-engineering-in-the-age-of-ai/). The book in its own world: [the review](https://beneaththeclaim.com/writing/modern-software-engineering-in-its-own-time/).
