# A late project, an estimate, or "should we add people or agents?"

**1. Treat adding people and adding agents as two different decisions.** (Brooks's Law, chapter 2:
*bends*.) Added people cost the incumbents training time, force the work to be divided again and
lengthen system test. Brooks himself called the law an oversimplification and limited it to LATE
projects. Added agents take little of the incumbents' time, but they need written context, the work
still has to be divided, and everything they produce joins the same review queue.
*Pitfall:* stating the law as absolute, or treating added agents as free. Both are wrong.

**2. Find the review and integration capacity before adding any hands.** (The man-month is a deceptive
unit, chapter 2: *bends*.) Cost scales with workers times time; progress does not. Progress is set by
how many independent subtasks exist and by the sequential work: integration, system test, human review.
List who reviews and how many hours they have this week. Add agents only to subtasks that can be split
off with their own check.

**3. Take no small slips: reschedule once, with room, or cut scope by name.** (Chapter 2: *holds*.)
When a date is lost, name ONE new date far enough out that it will not move again, or name the
functions that are cut. If nobody trims the task on purpose, the team or the agent trims it silently,
in testing and in design.

**4. Defend the estimate; a wished-for date is not an estimate.** (Gutless estimating, chapter 2:
*holds*.) Urgency can set the promised date and cannot set the real one. Say so, and give the basis for
your number.
*Pitfall:* a fast first draft from an agent is not evidence that the rest of the chain will go well
(programmer optimism, chapter 2: *strengthens*). Schedule the verification: when code is cheap,
verification is the schedule.

**5. Use milestones too sharp to fool yourself, and react to a one-day slip.** (Chapter 14:
*strengthens* and *holds*.) A milestone is a concrete, checkable, 100-per-cent event: "all test cases
pass on the integrated build", never "coding 90 per cent done". An agent reports "done" with full
confidence, so only a check decides. Projects become a year late one day at a time.

Why these rulings: [the verdict, Brooks's Law](https://beneaththeclaim.com/writing/the-mythical-man-month-in-the-age-of-ai/)
