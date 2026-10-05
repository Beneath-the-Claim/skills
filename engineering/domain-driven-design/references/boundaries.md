# Splitting a system, drawing boundaries, integrating with another model

**13. Keep foreign models behind a layer that translates them.** (ANTICORRUPTION LAYER, chapter 14: *strengthens*.)
Agents copy what they see. A legacy or vendor model visible in your code spreads into every change an agent makes;
behind a translating layer it stays where it is.

**14. Publish the language two contexts exchange, separate from either model.** (PUBLISHED LANGUAGE, chapter 14:
*strengthens*.) Agents integrate against what is documented. A written, versioned exchange format beats an agent
reading the other side's code and guessing.

**15. Keep a shared kernel only where two models truly overlap, and let tests guard it.** (SHARED KERNEL, chapter 14:
*bends*.) Goodwill between teams kept a kernel consistent; agents have none. Every change to the kernel runs both
sides' tests.

**16. When two parts share nothing essential, let them go separate ways.** (SEPARATE WAYS, chapter 14:
*strengthens*.) Integration is the expensive part; agents build two separate things cheaply.

**17. Integrate and test inside a context often, because parallel agents split a model faster.** (CONTINUOUS
INTEGRATION, chapter 14: *strengthens*.) Several agents on one context each drift a little; merge and run the whole
context's tests many times a day.

**18. Count parallel streams of change, not people, when deciding how many contexts.** (Choosing a strategy within
the system, chapter 14: *bends*; Forces on context size, chapter 14: *bends*.) The agent's context window pulls
toward smaller contexts, and each stream of agents needs a boundary of its own. But a boundary is where translation
and drift begin.

**19. Distil before you split.** (Splitting a context to tame complexity, chapter 14: *bends*.) A context too big
for an agent tempts you to cut it. First separate the core from the generic parts and the mechanisms; split only
if that is not enough.

**20. Models drift wherever communication is thin, and between agent sessions it is thinnest of all.** (Model
boundaries follow team organization, chapter 14: *bends*.) Draw the boundary where one owner, one set of tests and
one written model can hold it.
