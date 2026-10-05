# Dividing work among engineers or parallel agents

**6. Put one named mind over the design before anyone starts.** (The architect, chapter 4: *holds*;
the surgical team, chapter 3: *strengthens*.) One engineer directs; agents take the support roles
Brooks gave to the copilot, the toolsmith, the tester and the editor. An agent rarely argues back, so
book a design review with another ENGINEER for anything that matters.

**7. Write the interfaces first, and keep them small.** (Separate architecture from implementation,
chapter 4: *strengthens*.) What the system does is decided and written down before how. A small,
precise interface is what lets work be divided, and it is what fits in a context window. Workers, human
or agent, should not need to read each other's code.

**8. Partition by independence, and say what cannot run in parallel.** (The man-month, chapter 2;
organisation cuts the communication needed, chapter 7: *holds*.) Ten workers who must coordinate are
slower than three who need not. Name the subtasks with no shared state, give each its own check, and
name the sequential spine (shared schema, integration, migration) that stays with one owner.
*Pitfall:* giving several agents one undivided task. They fix the same bug and overwrite each other.

**9. Integrate one change at a time into a system that always runs.** (Chapter 13: *bends*; let a
machine keep the gate.) Add components singly, with a regression run each time. Do not collect five
branches for one merge at the end of the week.

**10. Never let the worker that wrote the code be the only one that tests it.** (Independent product
test, chapter 6: *strengthens*.) An agent that writes both code and tests checks its own reading of the
task against itself. Have the work checked against the SPECIFICATION by a separate agent that never saw
the implementation, or by a person acting for the user.

Why these rulings: [the verdict, the surgical team and the architect](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
