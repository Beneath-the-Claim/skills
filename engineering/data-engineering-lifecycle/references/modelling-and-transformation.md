# Modelling and transforming data when agents write the models and query them

Read this when the user is designing a data model or a semantic layer, letting agents write transformations or
dbt models, reviewing agent-written SQL, or cleaning malformed data. The rules in `SKILL.md` still apply; this file
adds the detail.

## The model carries the meaning

- **Write the business's definitions into the model before an agent answers from it.** (A data model encodes
  business logic, chapter 8: *strengthens*; Data modeling makes data useful, chapter 2: *strengthens*.) An agent
  asked for active customers picks a definition and answers confidently; an inferred definition is a guess nobody
  signed off. Find the terms that mean different things to different people first.
- **Spend the modelling effort on the conversation with the business.** (Data modeling is a full-contact sport,
  chapter 8: *strengthens*.) When the schema drafts itself, that conversation is most of the modelling, and its
  outcome must be written down.
- **Draw the conceptual model with people; let agents derive the logical and physical models, and review them.**
  (Conceptual, logical and physical models, chapter 8: *bends*.)
- **Define each metric once, in one governed place, with its departmental variants documented.** (Business logic
  and derived data, chapter 8: *strengthens*; Data definitions and logic, chapter 9: *strengthens*; Transformation
  and its business logic, chapter 2: *strengthens*.) An agent remembering nothing between sessions re-derives revenue
  or churn from scratch unless one definition is written where it reads.
- **Conform the dimensions from the first mart, and name the integrated core agents must trust.** (The star schema
  and conformed dimensions, chapter 8: *strengthens*; Kimball's bottom-up approach, chapter 8: *bends*; Inmon's 3NF
  warehouse feeding data marts, chapter 8: *strengthens*.) An agent cannot reconcile two versions of a dimension it
  finds.

## Shapes agents query correctly

- **Declare each fact table's grain and test it.** (Fact tables at the lowest grain, chapter 8: *holds*; Row
  explosion in joins, chapter 8: *strengthens*.) An agent that does not know a key repeats will multiply rows and
  report the inflated total.
- **Put a current-state view in front of every soft-delete, insert-only or slowly changing table.** (Delete: hard,
  soft or insert, chapter 8: *bends*; The insert-only pattern, chapter 5: *bends*; Slowly changing dimensions,
  chapter 8: *bends*.) Record in the catalog what the raw table holds.
- **Pre-join and persist what everyone joins, and point agents there.** (Optimize your JOIN strategy and schema,
  chapter 8: *strengthens*; Transformations differ from queries, chapter 8: *strengthens*.) It saves compute and
  spares every agent a join it might get wrong; give the persisted layer owners or it sprawls.
- **Serve wide tables to agents only over a modelled core, with every column described.** (Wide denormalized
  tables, chapter 8: *bends*; Model at the lowest grain, chapter 8: *holds*.)
- **Keep a date dimension with the fiscal calendar, so agents do not compute calendar logic.** (Dimension tables
  give the context, chapter 8: *holds*.)

## Reviewing what agents write

- **Prefer SQL where it fits: it is the cheapest code to review.** (SQL is declarative but builds workflows, chapter
  8: *strengthens*; When to avoid SQL in Spark, chapter 8: *bends*.) Pick SQL or Spark by what a reviewer can check
  and a library can reuse.
- **Read what actually runs: the plan, the bytes scanned, the shuffles.** (Know what your tools execute, chapter 8:
  *strengthens*; Use the explain plan and monitor performance, chapter 8: *strengthens*; Optimizing Spark and other
  processing frameworks, chapter 8: *bends*.) Agent-written SQL is generated code; the team's expertise moves from
  writing optimized code to reading the plans and costs of what agents wrote.
- **Prune by default, and cap agent sessions' scans.** (Avoid full table scans, chapter 8: *strengthens*.) An agent
  peeking at a table can pay to scan all of it.
- **Reuse through views and shared metrics, not result caches.** (Leverage cached query results, chapter 8:
  *bends*; Materialized views precompute expensive joins, chapter 8: *strengthens*.) Result caches match exact text,
  and agents rephrase.
- **Write down why a pipeline is ETL or ELT, so the next agent knows.** (ETL, ELT and data pipelines, chapter 8:
  *holds*.)
- **Merge at the frequency the target engine affords; an agent porting code copies the old system's habit unless
  told.** (Near real-time merges from CDC, chapter 8: *holds*.)

## Streams

- **Decide the window and how late is too late as business definitions, then let agents write the code.** (Windows,
  triggers and late-arriving data, chapter 8: *holds*; Streaming code is harder, chapter 2: *bends*.) Reasoning
  about late, out-of-order events is still the hard part.
- **Have agents build both a micro-batch and a streaming prototype and test them on your workload.** (Micro-batch
  versus true streaming, chapter 8: *strengthens*.) Neither a vendor benchmark nor an agent's opinion settles it.
- **Tag model-generated enrichment as generated, with the model version, and check its quality.** (Enrich a stream
  with other data, chapter 8: *bends*.)

## What broke here

- **Do not buy a separate data wrangling tool: have an agent profile a sample and write the parsing and cleaning
  code, tested and versioned; a person judges whether the cleaned data is right.** (Data wrangling tools as IDEs,
  chapter 8: *breaks*.)
- **Chain transformations with your platform's dynamic tables or declarative pipelines; the old limit that
  materialized views cannot read from one another is out of date.** (Composable materialized views, chapter 8:
  *breaks*.) Better tools made this change, not agents.
