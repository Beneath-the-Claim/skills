# Making, recording and enforcing architecture decisions

**9. Find what is entangled, analyse how it couples, then assess the trade-offs, in that order.** (Trade-off
analysis in three steps, chapter 2: *strengthens*; Assess trade-offs, chapter 15: *holds*.) Agents change more code
with less view of the system. Map the coupling before judging any change, and settle first the dimension that
constrains the rest; agents make iterating cheaper, not the order optional.

**10. Write down the constraints the code does not show, and the reason behind each.** (Finding entangled
dimensions, chapter 15: *bends*; Why is more important than how, chapter 1: *strengthens*.) An agent finds the
coupling the code shows. The reasons, the limits and the promises made to other teams reach it only in writing.

**11. Let a model list and rate the options; check the ratings against your context.** (Analyze coupling points,
chapter 15: *bends*; The out-of-context trap, chapter 15: *strengthens*; MECE lists, chapter 15: *holds*.) A table
written without your context is generic advice produced in seconds. Check that the options compare like with like
and that none is missing.

**12. Settle a dispute with a spike where you can.** (Answer evangelism with scenario analysis, chapter 15:
*bends*; Testing can make trade-offs quantitative, chapter 15: *strengthens*; Iterative design through what-if games,
chapter 15: *bends*.) Agents build two variants cheaply, so measure them in your own system. Keep judgement for
what a spike cannot show, and never stop at a model's first draft.

**13. Model the cases your business will face, and give the sponsor the bottom line.** (Model relevant domain
cases, chapter 15: *holds*; Prefer bottom line over overwhelming evidence, chapter 15: *holds*.) A model invents
scenarios and writes long reports with ease; the people who choose need the few outcomes they are choosing between.

**14. Ask every tool, and the model you consult, for its costs as well as its capabilities.** (Avoiding snake oil
and evangelism, chapter 15: *strengthens*; First law of software architecture, chapter 10: *holds*.) If a choice
looks free, its trade-off has not been found yet.

**15. Check characteristics alone and together, and tell agents which checks they may change.** (Atomic and
holistic fitness functions, chapter 1: *holds*; Fitness functions versus unit tests, chapter 1: *holds*.) A check
that needs domain knowledge belongs to the team; a check that guards the architecture belongs to whoever owns it.

**16. Put a cycle check, layer rules and a security check in every pipeline.** (Cyclic dependencies between
components, chapter 1: *strengthens*; Governing layers with fitness functions, chapter 1: *strengthens*; A security
slot in every pipeline, chapter 1: *strengthens*.) Agents add imports and dependencies faster than anyone reviews
them, and rarely see the architecture diagram; the build is what they run into.

**17. Let automation govern, and a model route.** (Automating architecture governance, chapter 1: *strengthens*.)
No review board reads at the speed agents ship. A model can review a change against written principles, but it is
fallible: let it route changes to people, never approve them alone.

**18. Ask which reasons for today's style still hold.** (Judge a style by its constraints, chapter 1: *holds*;
Software architecture cannot stay stable, chapter 3: *strengthens*.) Agents change the costs that made today's
styles win, and join systems as callers, so the architecture has to be revisited more often than before.

**19. Treat data, contracts and agreements as the parts that are hard to change.** (The stuff that's hard to change
later, chapter 1: *bends*; Data outlives systems and architecture, chapter 1: *strengthens*.) Agents make code
structure easier to change. Data cannot be regenerated, and contracts and agreements between teams move only as
fast as the people behind them.

**20. A tool's knowledge goes stale; the method lasts.** (An ecosystem that replaces itself, chapter 1:
*strengthens*.) Models know the tools of their training. Weigh any recommended tool by the trade-off method, not by
how familiar the model is with it.
