---
name: data-engineering-lifecycle
description: Use when a data engineer or data lead designs, builds, reviews or runs data pipelines and platforms that AI agents help write, or that agents and AI assistants read from, and is connecting sources or choosing connectors, modelling and transforming data, choosing storage, tools or an AI platform, controlling cost, serving data to dashboards, ML, text-to-SQL or retrieval, letting agents write back into business systems, or securing and governing data and the agents' access to it. Applies the lifecycle and undercurrents of Joe Reis and Matt Housley's Fundamentals of Data Engineering (2022), in the form in which they hold now that agents write much of the pipeline code and read the data.
---

# Rules from Fundamentals of Data Engineering, for data engineers whose pipelines agents write and whose data agents read

Rules from the book by Joe Reis and Matt Housley (2022). The book holds that data engineering is defined by its
lifecycle (generation, storage, ingestion, transformation and serving) and by the undercurrents that run under every
stage (security, data management, DataOps, data architecture, orchestration and software engineering), and that the
lifecycle outlasts the tools. Every principle in it was ruled on for the age of AI agents. Agents now write much of
the pipeline code and read the data, so a pipeline is cheap to write, and what binds harder is the undercurrents and
trust in the numbers. One piece of advice broke because of agents, and one more because of better tools. Each rule
names its chapter and its ruling.

Do not recite the book at the user. Make the move the rule calls for, in the user's own situation, and say why in
one sentence.

**These rules ADD to your own judgement; they never replace it.** You already set a spend limit before an agent gets
access (its own role, a warehouse it cannot resize, a quota and a timeout), test a backfill on a small slice first,
declare each model's grain and test it, reconcile key numbers with the system of record, show a change's data diff
before merge, define each business term once with its owner where agents read it and keep agents off the raw tables,
run an assistant's queries under the asking user's identity with row- and column-level policies, check trust before
anything is served with an evaluation set of real questions, stream only what an action needs, keep managed
connectors for the sources you need run, replace a wrangling tool with tested parsing code, pilot a new platform
beside the old one, measure a team's actual workload before committing to a headcount, hand a person any fix that
would change what a field or a metric means, have an assistant say it cannot answer rather than improvise beyond its
vetted queries, and show the reader how each number was worked out. Keep doing that and give those answers first. Then add what the rules below bring, because they
are the moves usually left out.

## Pick the file for the task in front of you

| The user is... | Read |
|---|---|
| connecting sources, choosing connectors, handling partner files or upstream schema changes, migrating data | `references/sources-and-ingestion.md` |
| designing a data model or semantic layer, letting agents write transformations, reviewing agent SQL, cleaning malformed data | `references/modelling-and-transformation.md` |
| choosing storage, tools or a platform (an AI platform included), deciding build or buy, controlling cost, changing the architecture | `references/storage-architecture-and-cost.md` |
| serving data to dashboards, ML, text-to-SQL, retrieval or an assistant in a product, or letting agents write back into business systems | `references/serving-and-trust.md` |
| giving agents access, assigning ownership, setting up tests, monitoring and incident response, handling sensitive data | `references/security-governance-and-operations.md` |

Read one file, or two when the task spans them. Do not load all five.

## Seven things that hold everywhere

Apply these to EVERY task, whichever file you read. The reference files add detail; they do not repeat these.

1. **Name the stage a pipeline serves and what it must deliver, then walk all six undercurrents, before an agent
   builds it.** (The lifecycle isn't going away, the Preface: *strengthens*; The undercurrents of the lifecycle,
   chapter 2: *strengthens*; The data engineering lifecycle, chapter 1: *holds*.) Say which stage the work serves
   (generation, storage, ingestion, transformation or serving), and have a person write what it must deliver: its
   tables, their grain and freshness, and the checks they must pass. The agent carries the tools; knowing what each
   stage must deliver, and catching the pipeline that does not deliver it, is the person's part. Then say what the
   pipeline needs from each undercurrent: security (who and what may read it), data management (the definitions it
   carries, its owner, its lineage, its retention), DataOps (its tests, monitors and on-call), data architecture
   (where it sits and what it couples to), orchestration (its dependencies) and software engineering (its
   repository, review and versioning). An incident shows only the undercurrent that failed; the others fail next.
   Write the result where the agent that builds the pipeline reads it, and have the agent build one stage at a time,
   each stage's output checked before the next starts. An AI pipeline is no exception: a retrieval index ingests
   documents, cuts them into chunks and embeddings, stores and serves them, so build it on the ingestion,
   orchestration and storage you already run, with no sixth stage and no separate AI stack.
2. **Ask what each table is for and who uses it, retire what nobody uses, and make what stays legible to agents.**
   (Serving data: value only when used, chapter 2: *strengthens*; Key engineering considerations for ingestion,
   chapter 7: *strengthens*; Security as an enabler, chapter 6: *strengthens*; Principles of good data architecture,
   chapter 3: *holds*.) Agents remove the build cost that once stopped pipelines with no purpose, and to an agent
   searching the catalog an unused table is not inert: it is a decoy it can pick by mistake, and one more surface to
   secure. Describe each table that stays, its columns and its metrics, where agents load them as context, so other
   teams' agents reuse it instead of rebuilding it from raw exports: a 2026 list of architecture principles would add
   a tenth, make the data legible to agents.
3. **Grant each agent the data and privileges of today's task, through short-lived credentials, and revoke them when
   the task ends.** (The principle of least privilege, chapter 2: *strengthens*; Protect your credentials, chapter 10:
   *strengthens*; Hardened perimeter versus zero trust, chapter 3: *strengthens*.) An agent is fast, fallible,
   confident when wrong and can be steered by text it reads, so what it can reach sets the size of every error. A
   standing role for an agent is a start; a grant that expires with the task is the control.
4. **Log every agent action against its session and the person who directed it.** (Logging, monitoring, and
   alerting, chapter 10: *strengthens*; Data accountability per portion of data, chapter 2: *strengthens*.) Tag each
   query and change with the person as well as the agent and the ticket, or nobody can reconstruct what happened or
   answer for it.
5. **Plan for the agent's bad write: give it a clone to build against, and keep the history to undo it.** (Principle
   2: Plan for failure, chapter 3: *strengthens*; Zero copy cloning, chapter 6: *strengthens*; Always back up your
   data, chapter 10: *strengthens*; The data lakehouse, chapter 3: *strengthens*.) A dropped table or a bad backfill
   is now an everyday failure beside the dead disk. Agents build and test against a zero-copy clone or a development
   copy, never the production tables; table history, time travel and point-in-time recovery cover the logical
   damage; and a restore you have tested, from a copy the agents cannot delete, is the last line.
6. **Trace every number agents build or serve back to its sources.** (Data lineage as audit trail, chapter 2:
   *strengthens*; Build, learn, improve: serving loops back, chapter 9: *bends*; Trust as the root of serving, chapter
   9: *strengthens*.) When agents write the transformations, lineage is the only record of how a number was made: use
   it to find everything a wrong number reached, and link each answer an assistant gives to the tables behind it, so
   a complaint becomes an upstream fix. A wrong number now arrives fluently, so trust is the product.
7. **Keep the long-lived base under a replaceable AI layer, and rent compute until a steady load shows.** (Immutable
   versus transitory technologies, chapter 4: *strengthens*; Data gravity: egress costs, chapter 4: *strengthens*;
   Total opportunity cost of ownership, chapter 4: *bends*; Separation of compute from storage, chapter 6: *holds*;
   Capex versus opex, opex first, chapter 4: *holds*.) Keep the data in your own object storage, in open table
   formats, reached through SQL and the shell, the interfaces agents know best, and keep the code portable too:
   standard SQL wherever it will do, with an engine's own extensions in a few named places. Treat agent frameworks,
   vector databases and AI-native platforms as the newest transitory layer: choose one you can leave without moving
   the data, keep a retrieval index's chunks and embeddings in your own storage so the vector database is an index
   you can rebuild, and re-evaluate the layer every two years. Rent compute for agents' bursts, and commit to reserved
   or annual capacity only once a measured base load is steady. Then leaving costs proving the numbers, not moving
   the data or rewriting the code.

## What bends: apply the changed form, not the original

- **Buy connectors for running them, not for writing them.** (Managed data connectors, chapter 7: *bends*.) Buy a
  managed connector for each source you need run, monitored and backfilled; let an agent write the long-tail ones,
  each with an owner.
- **Stream only where an action needs the freshness.** (The live data stack, chapter 11: *bends*.) What reached
  applications came through language models and retrieval more than streaming: feed agents from batch-fresh tables
  and retrieval indexes.
- **Price build or buy by its upkeep.** (Build versus buy, chapter 4: *bends*.) Agents make the first version cheap;
  someone must run, patch and answer for every generated tool.
- **Let models draft the metadata; keep people owning the definitions.** (Metadata, automated with humans involved,
  chapter 2: *bends*.)
- **Write down what good data means, as tests.** (Data quality: accuracy, completeness, timeliness, chapter 2:
  *bends*.) Agent consumers give no human feedback, so the expectations must be codified.
- **Draw the conceptual model with people; let agents derive the rest, and review it.** (Conceptual, logical and
  physical models, chapter 8: *bends*.)
- **Size the stack to what your people can review and run.** (Team size and capabilities, chapter 4: *bends*.)
- **Orchestrate the first job anyone depends on.** (Shell scripts for small sources, chapter 7: *bends*.)

## What broke

- **A separate data wrangling tool.** (Data wrangling tools as IDEs, chapter 8: *breaks*.) An agent profiles a sample
  and writes the parsing and cleaning code, tested and versioned in the repository; buying a no-code tool and
  training specialists for it adds a tool and a role. Judging whether the cleaned data is right stays with a person.
- **The limit that materialized views cannot read from one another.** (Composable materialized views, chapter 8:
  *breaks*.) Better tools did this, not agents: chain transformations with your platform's dynamic tables or
  declarative pipelines.

Do not read "cheap to write" as "free to run": every pipeline an agent writes still has to be secured, governed,
monitored and trusted, and the undercurrents now carry most of that work.

The reasoning behind every ruling: [the verdict](https://beneaththeclaim.com/writing/fundamentals-of-data-engineering-in-the-age-of-ai/). The book in its own world: [the review](https://beneaththeclaim.com/writing/fundamentals-of-data-engineering-in-its-own-time/).
