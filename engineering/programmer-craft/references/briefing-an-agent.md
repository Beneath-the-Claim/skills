# Handing a change to an agent: the brief and the context

**8. Walk the ground before the agent does, and mark what it must not copy.** (Software entropy is
cultural, Topic 3: *bends*; refactor early, refactor often, Topic 40: *strengthens*.) An agent's only
culture is the code it reads and the rules you wrote down. Before the task, find the hacks, the
duplicates and the misleading names in the area it will touch. Fix what takes minutes; renaming is
cheap now, and an agent navigates by names (Topic 44: *strengthens*). Board up the rest in the brief.
*Pitfall:* "don't touch the old code" without saying which code is the example to follow. Name the
good pattern as well as the bad one.

**9. Say what is wanted in the user's terms, with the standard it must meet.** (Make quality a
requirements issue, Topic 5: *strengthens*; no one knows exactly what they want, Topic 45:
*strengthens*.) An agent builds exactly what was first said, to the standard that was stated. Put in
the brief: the behaviour in the domain's own words, the examples that define "right", how good is
good enough here, and what is out of scope on purpose.

**10. Keep the why where the agent will find it tomorrow.** (Build documentation in, Topic 7:
*strengthens*; keep knowledge in plain text, Topic 16: *strengthens*.) The agent forgets everything
overnight. The reason behind a decision goes in the code or in a plain-text file in the repository,
once (rule 2), and the brief points to it. A daybook is still worth keeping; keep it where the agents
can read it.

Why these rulings: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
