# Pulling data apart, assigning who owns it, and giving services and agents access

**40. Split the data and you owe three answers: who owns it, how writes commit, who reads it.** (Splitting data
creates three problems, chapter 9: *strengthens*.)

**41. Settle the tables with one writer first; an agent can list them, people confirm.** (Single ownership
scenario, chapter 9: *holds*; Primary domain priority, chapter 9: *holds*.) Writes through an ORM, a stored
procedure or another team's repository may sit outside what an agent sees. Give a shared table to the service whose
domain does most of its writing, not to the busiest caller.

**42. When every agent action must be audited, give the audit table one owner and a durable queue.** (Common
ownership scenario, chapter 9: *strengthens*.)

**43. Two services writing one table is a dependency problem; agents can code any fix, not dissolve it.** (Joint
ownership scenario, chapter 9: *holds*; Table split technique, chapter 9: *holds*; Data domain technique, chapter 9:
*bends*.) Splitting the table still needs a consistency choice, and sharing it still needs joint deployments,
however cheap agents make the edits.

**44. Weigh the forces for splitting a database with your own metrics.** (Data decomposition drivers, chapter 6:
*holds*; Data relationships as a data integrator, chapter 6: *strengthens*; Database transactions as a data
integrator, chapter 6: *strengthens*.) A model lists the forces; only someone with the connection counts, failure
tolerances and priorities can weigh them. A foreign key is a check no agent forgets to write, and a write that must
be all or nothing stays in one database.

**45. Live data moves at the speed of business risk.** (Data is harder to break apart, chapter 6: *strengthens*;
Five-step process for decomposing monolithic data, chapter 6: *holds*.) Agents write the migration scripts and take
each step faster; the order of the steps stays.

**46. Data sovereignty is cheaper to build and riskier to run.** (Data sovereignty per service, chapter 6: *bends*.)
Integrity that moves out of the database into agent-written code needs checks of its own.

**47. Choose a read pattern on purpose for every agent that needs another domain's data.** (Four distributed data
access patterns, chapter 10: *strengthens*; Interservice Communication pattern, chapter 10: *bends*; Column Schema
Replication pattern, chapter 10: *holds*; Replicated Cache pattern, chapter 10: *holds*.) A tool call is
interservice communication, and for an agent its contract matters more than its latency. A copy of another service's
columns buys fast reads and a copy someone must keep in step.

**48. Replicate data that changes slowly, and synchronise it asynchronously.** (Replicated caching suits relatively
static data, chapter 10: *holds*; Synchronize replicated data asynchronously, chapter 10: *holds*.) Replicate
product descriptions, not stock counts; check every agent reader that claims it needs the copy in the same
transaction.

**49. A shared table is a contract nobody wrote; give agents a service contract, and grant only the columns they
need.** (The shared table schema is the contract, chapter 10: *strengthens*; Data Domain pattern, chapter 10:
*bends*.)

**50. Write down the schema a schema-less store still has, and why the data looks as it does.** (Entirely
schema-less is misleading, chapter 6: *strengthens*; Collaborate closely with the database team, chapter 6:
*bends*.) An agent reads the schema; it cannot read what the data team knows about it.

**51. Choose a database's trade-offs yourself.** (Selecting a database type, chapter 6: *bends*; Relational
databases: SQL and ACID, chapter 6: *strengthens*.) Agents shrink the learning curve of a new database without
choosing its trade-offs; an ACID transaction contains the half-finished work of a fallible agent.

**52. Watch connections, failures and load on a shared database.** (Connection management as a data disintegrator,
chapter 6: *holds*; Fault tolerance as a data disintegrator, chapter 6: *holds*; Scalability as a data
disintegrator, chapter 6: *strengthens*.) Agents add callers, not capacity, and agent workflows lean on the data
tier, the part that still scales worst.

**53. A bounded context tells an agent what it may change without breaking anyone else.** (Bounded contexts isolate
breaking data changes, chapter 6: *strengthens*.)
