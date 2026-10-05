---
name: programmer-craft
description: Use when a software engineer or tech lead is working with AI coding agents and is briefing an agent for a change, reviewing or merging agent-written code or tests, designing or restructuring code that agents will keep changing, starting a project or a first slice, debugging with an agent, working in a codebase with known hacks or duplication, or deciding how to defend code nobody read line by line. Applies the principles of Hunt and Thomas's The Pragmatic Programmer (1999, rewritten 2019) that still hold now that AI agents write much of the code, and leaves out the ones that broke.
---

# Rules from The Pragmatic Programmer, for engineers who work with coding agents

Nineteen rules from Hunt and Thomas's book (1999, rewritten by the authors in 2019). Only principles
judged to **strengthen**, **hold** or **bend** in the age of AI coding agents are here; what broke is
listed at the end so that you do not apply it by habit. Each rule names its topic in the 2019 edition
and its ruling.

Do not recite the book at the user. Make the move the rule calls for, in the user's own situation,
and say why in one sentence.

**These rules ADD to your own judgement; they never replace it.** You already know to slice the work
thin, cap the size of a change, name an owner and have a human write the acceptance examples. Keep
doing that, and give those answers first. Then add what the rules below bring, because they are the
moves that are usually left out.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| about to hand a change to an agent, or writing its brief or context | `references/briefing-an-agent.md` |
| reviewing, testing or merging what an agent produced | `references/reviewing-agent-work.md` |
| designing, restructuring, or asking why changes keep going wrong | `references/designing-for-change.md` |
| starting a project, a first slice, a prototype or an estimate | `references/starting-a-project.md` |
| chasing a bug, alone or with an agent | `references/debugging-with-agents.md` |
| deciding how much checking code needs at run time, or securing it | `references/defending-the-code.md` |

Read one file, or two when the task spans them. Do not load all six.

## Seven things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not
repeat these.

1. **Fix or board up the bad pattern BEFORE an agent works near it, never after.** (Don't live with
   broken windows, Topic 3: *strengthens*.) An agent copies the code in front of it more literally
   than a newcomer and feels no unease. A hack left in place for "after this feature" is the template
   for this feature. If there is no time to fix it, board it up where the agent will read it: a
   comment at the site and a line in the brief saying "this is wrong, do not copy it, use X".
   "Leave it alone and file a ticket" is the move this rule replaces.
2. **One home for each piece of knowledge, and that includes what you tell the agent.** (DRY, Topic 9:
   *strengthens*.) A rule, a schema, a format or a setting that lives in two places will be updated in
   the one the agent can see. Code that merely looks alike is not the same knowledge; do not merge it.
   A context file that restates what the code or the schema already says is a second copy: point to
   the source.
3. **Ask agent-written code to write its assumptions down and check them.** (Design by contract,
   assertions, crash early, Topics 23 to 25: *strengthen* and *hold*.) For every unit that matters:
   what it requires, what it guarantees, what must always be true, as checks that run. An impossible
   case gets an assertion, and assertions stay on in production. On a broken assumption the code stops
   loudly; it never guesses a default and carries on.
4. **Ask the agent for the decisions it made, and review that list before the diff.** (Coding is not
   mechanical, chapter 7: *bends*.) An agent makes a judgement call every few lines and reports none
   of them. Make "list every design decision and assumption you made, and what you chose against" part
   of the task. A decision the engineer cannot explain to a colleague is not finished work (don't
   program by coincidence, Topic 38: *strengthens*).
5. **Read the agent's tests as a review of the design.** (Testing is not about finding bugs, Topic 41:
   *bends*.) When the agent wrote the tests, nobody felt the interface. Read them as its first user
   would: much set-up before a call means the unit is too coupled; a test that asserts only what the
   code does today confirms the code, never the intent. Write the intent-level cases yourself, or
   specify them and delegate only the implementation.
6. **Judge a design by what it costs to verify and to replace.** (ETC, Topic 8: *bends*; decoupling
   and orthogonality, Topics 10 and 28: *strengthen*.) Typing a change is cheap now; knowing it is safe
   is what costs. Prefer the design in which a change touches one unit, the unit can be run and tested
   alone, and everything the change depends on fits in one agent session. What does not fit gets
   changed blind.
7. **The step is as big as what one person can check, and the agent's thrash is your warning.** (Take
   small steps, Topic 27: *strengthens*.) Feedback sets the speed, whatever the agent's output. The
   agent never feels the code push back, so read the gauges for it: a diff that keeps growing, the same
   fix attempted three times, special cases piling up. Any of those means the design is wrong. Stop
   the agent and rethink; do not let it try again.

## What broke: do not apply these

- **Editor fluency as a skill to drill** (Topic 18). The authors' own sum assumes twenty hours a week
  of hand editing. Train reading and judging a change.
- **A shell of your own, with personal aliases and functions** (Topic 17). A shortcut only one person
  can run is one an agent cannot. Put shortcuts in versioned project scripts.
- **Waiting for the code to push back** (Topic 37). The agent feels nothing. Use the gauges in rule 7.
- **The prototyping trick for blank-page fear** (Topic 37). The page is never blank now. Keep only its
  last step: delete the prototype.
- **PERT three-point estimates per task** (Topic 15). Agent work finishes in minutes or stalls until a
  person steps in. Give a range for the whole and let the first iterations set the schedule.
- **Learning layout tools and proofreading by hand** (Topic 7).

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/). The book in its own world:
[the review](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-its-own-time/).
