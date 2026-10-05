# Duplicate or drifting concepts, the glossary, and what agents are told

**7. Let agents draft candidate models; let experts and developers choose.** (Knowledge crunching with domain
experts, chapter 1: *bends*.) An agent can list the concepts in a specification, past tickets or a contract in
minutes. Which of them matter, and how they relate, is decided with the people who do the work, on real cases.

**8. Give each business rule a name and one home.** (SPECIFICATION, chapter 9: *holds*.) A rule with no name is
rewritten by every agent that needs it. Name it in the glossary's terms, put it in one place, and point the agents'
instructions at that place.

**9. Name every operation for what it does, never for how.** (INTENTION-REVEALING INTERFACES, chapter 10:
*strengthens*.) Agents find their way by names. A method called after its mechanism invites a second method that
does the same thing under the business's name.

**10. Divide the code by domain meaning.** (MODULES, chapter 5: *strengthens*; MODULES must coevolve with the model,
chapter 5: *bends*.) An agent then loads one part of the story, not the whole system. Agents make moving modules
cheap, so move them when the model changes, not once at the start.

**11. Write the design in words, in the repository.** (Text documents with small diagrams, chapter 2: *bends*;
Discipline for undeclarable model distinctions, chapter 5: *bends*.) A distinction that lives only in discussion is
invisible to an agent. Put it in a short text next to the code, where people and agents both read it.

**12. Translating between two jargons hides drift; it does not remove it.** (Translation between separate jargons,
chapter 2: *bends*.) An agent translates instantly between the experts' words and the code's, so nobody notices the
two drifting apart. Close the gap: one vocabulary, used by both.

When a concept already exists under four names, settle the meaning first with the people who own the outcome, keep
one class per meaning in each context, make the others delegate to it, move the callers, then delete them. Rules 1
and 3 in `SKILL.md` keep it from coming back.
