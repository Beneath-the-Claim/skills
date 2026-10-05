# Designing or restructuring code that agents will keep changing

**15. Size a component to one agent session, and make every dependency visible in the code.**
(Orthogonality, Topic 10: *strengthens*; avoid global data, Topic 28: *strengthens*.) A context window
is a smaller head than a long-serving engineer's. Ask of any change how many units it touches; the
right answer is still one. An agent cannot respect a dependency it cannot see, so no hidden globals,
no state reached through the back door. Wrap a shared resource in one interface, which is also where
you stop an agent touching production (Topic 28: *holds*).
*Pitfall:* counting on a bigger context window to make coupling cheap. Vendors' own documentation says
performance degrades as the window fills.

**16. Reverse code decisions freely; treat data and contracts as the expensive ones.** (There are no
final decisions, Topic 11: *bends*; avoid fortune-telling, Topic 27: *holds*.) Nobody sees further
ahead than before. Do not design for a guessed future; make the part cheap to replace and let an agent
replace it. What did not get cheaper to reverse: a stored data format, a published interface, a
contract another team builds on. Write an interface down once, as a schema both sides and their agents
read (Topic 9: *bends*).

**17. Most configuration options are deferred decisions.** (Don't overdo configuration, Topic 32:
*strengthens*; policy is metadata, Topic 45: *bends*.) When changing code takes minutes, make something
configurable because a non-programmer must change it or because it differs per environment, never
because a code change used to be expensive.

Also here, unchanged by agents (*holds*): prefer interfaces and delegation to inheritance (Topic 31);
pass data through functions and do not hoard state (Topic 30); a clear input and output makes a step
an agent can finish. For several agents at once: parallel agents in one checkout are shared state, and
shared state is incorrect state (Topic 34: *strengthens*). Give each its own worktree and a written
board to coordinate from (Topic 36: *strengthens*).

Why these rulings: [the verdict](https://beneaththeclaim.com/writing/the-pragmatic-programmer-in-the-age-of-ai/)
