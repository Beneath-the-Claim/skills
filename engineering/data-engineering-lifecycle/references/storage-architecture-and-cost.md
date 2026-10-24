# Storage, architecture, technology choices and cost when agents build and query

Read this when the user is choosing where data lives, designing or changing a data architecture, choosing or
replacing tools and platforms (an AI platform included), deciding build or buy, or controlling what agents cost. The
rules in `SKILL.md` still apply; this file adds the detail.

## Storage

- **Keep data in object storage and rent compute for the bursts.** (Separation of compute from storage, chapter 6:
  *holds*; Object storage for data engineering, chapter 6: *holds*.) Agent traffic is bursty and arrives at all
  hours, the varied load that favours ephemeral compute. Object storage still loves big batches and hates small
  updates: send agents' traces, events and memory entries to a transactional store.
- **Pick each store for its workload, and count retrieval and agent queries as workloads.** (Storage: choose by
  use case, chapter 2: *holds*; Data engineering storage abstractions, chapter 6: *holds*.) Choose a warehouse, a
  lake or a vector index by purpose and update pattern, as before.
- **Set data temperature from measured access, machine readers included.** (Hot, warm, and cold data, chapter 2:
  *bends*.) Agents running retrieval, backfills and broad historical queries read archives far more often than a
  monthly report did.
- **Use table snapshots and object versions to see and undo what an agent changed.** (The data lakehouse, chapter 3:
  *strengthens*; Object consistency and versioning, chapter 6: *bends*; Hybrid serialization: Hudi and Iceberg,
  Appendix A: *strengthens*.) Version every object you might need back and cap the versions with lifecycle rules.
- **Keep at least one copy where your own agents cannot delete it.** (Data durability and availability, chapter 6:
  *bends*; Always back up your data, chapter 10: *strengthens*.) Separate credentials, object lock or immutable
  backups; an agent with the team's credentials can reach every region a replica sits in.
- **Make clone and raw-file dependencies visible before an agent tidies storage.** (Zero copy cloning, chapter 6:
  *strengthens*.) A clone's dependence on raw files is invisible to an agent unless lineage records it.
- **Write the store's consistency model where an agent will look.** (Eventual versus strong consistency, chapter 6:
  *strengthens*.) An agent cannot sense a stale read; it acts on it at once.
- **Decide retention for every copy agents create: embeddings, caches, agent memory, prompt and output logs.** (Data
  retention: value, time, compliance, cost, chapter 6: *strengthens*.) Much of it can be re-created, which the
  value test counts toward deleting.
- **Decide who may deploy and change storage, and decide it for their agents too.** (Domains of responsibility for
  storage, chapter 6: *strengthens*; Single-tenant versus multitenant storage, chapter 6: *strengthens*.)

## Architecture

- **Write the architecture down before agents choose tools.** (Architecture first, then tools, chapter 4:
  *strengthens*; Ivory tower architecture is gone, chapter 1: *bends*.) An agent left to choose picks habit over the
  business and carries no design between sessions; the written architecture is the brief it works from, just ahead
  of the build.
- **Keep the nine principles as the checklist; security, cost and coupling weigh more.** (Principles of good data
  architecture, chapter 3: *holds*; Principle 6: Build loosely coupled systems, chapter 3: *strengthens*; Principle 1:
  Choose common components wisely, chapter 3: *strengthens*.) An agent changes a component safely only when its
  interface is explicit and its blast radius fits in its context; a few shared, documented components keep agents
  governable.
- **Treat code choices as two-way doors and deleting or exposing data as one-way.** (Principle 7: Make reversible
  decisions, chapter 3: *holds*.) Agents make porting code cheap; they do not make a dropped table or data sent to an
  outside model reversible.
- **Replace one piece at a time and check it against the old outputs.** (Brownfield projects and the strangler
  pattern, chapter 3: *strengthens*.) Agents make a rewrite cheap to try, not safe to cut over.
- **Ask what a new AI component returns before building it.** (Greenfield projects and shiny object syndrome,
  chapter 3: *strengthens*.) AI is today's shiny object, and agents make it cheap to build.
- **Before buying a platform, check that your catalog, lineage and definitions can leave with you.** (Data
  platforms around the storage layer, chapter 6: *bends*; Interoperability across the stack, chapter 4: *bends*.)

## Choosing technology and paying for it

- **Size the stack to what your people can review and run.** (Team size and capabilities, chapter 4: *bends*.)
  Agents can generate a big company's stack in days; they do not review, run or answer for it.
- **Choose tools by how fast you can verify and trust a change.** (Speed to market, chapter 4: *bends*.) Build
  speed no longer separates teams.
- **Price build or buy by who runs it afterwards.** (Build versus buy, chapter 4: *bends*; Adopt open source before
  building, chapter 2: *bends*.) Generate small glue; adopt maintained open source for anything that needs a
  community; count running, patching and answering for every generated tool as its real cost.
- **Price an exit by data movement and proving the numbers, not by rewriting code.** (Total opportunity cost of
  ownership, chapter 4: *bends*; Data gravity: egress costs, chapter 4: *strengthens*.) Agents port the code in days;
  the egress bill and the comparison of old and new outputs still hold you.
- **Tie each metered dollar to what it earns, with a named person accountable.** (FinOps is about making money,
  chapter 4: *strengthens*; Control costs, deliver outsized value, chapter 1: *strengthens*.) Count the token bill
  and the review hours in total cost of ownership (Total cost of ownership, chapter 4: *holds*).
- **Model cost per event before agents run unattended.** (Serverless versus servers, chapter 4: *strengthens*.)
  Your own agents in a loop are the bot swarm the pricing model punishes.
- **Make every temporary cluster an agent starts stop on its own.** (Cloud ≠ on premises, chapter 4: *holds*.) An
  agent that starts one remembers nothing after its session.
- **Pay as you go for agent workloads until a measured steady base shows.** (Capex versus opex, opex first, chapter
  4: *holds*; Principle 3: Architect for scalability, chapter 3: *bends*.) Agent load scales with loops, not
  headcount: measure it separately and cap it.
- **Test a vendor's claims on your own data and query sizes, and price the high-usage case at agent query
  rates.** (Proprietary offerings: independent and cloud, chapter 4: *holds*.)
