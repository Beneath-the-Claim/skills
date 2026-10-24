# Getting data from sources when agents write the ingestion

Read this when the user is connecting a new source, choosing between managed connectors and agent-written ones,
handling partner files, coping with upstream schema changes, or moving data between systems. The rules in
`SKILL.md` still apply; this file adds the detail.

## Before an agent builds a pipeline

- **Ask what the data is for, and whether it already exists, before an agent ingests it.** (Key engineering
  considerations for ingestion, chapter 7: *strengthens*; Ingestion, the biggest bottleneck, chapter 2: *holds*.)
  An agent told to ingest a source builds a new copy unless a catalog shows it the existing one. The use case and
  fitness for purpose stay with people; the agent can draft the technical answers.
- **Understand how the source behaves: retries, duplicates, late data, backfills and planned changes.** (Understand
  and evaluate source systems, chapter 2: *strengthens*; Schema and data types: study sources early, chapter 7:
  *bends*.) Let the agent read the schema, the ORM models and a sample; spend the conversation with the producing
  engineers on meaning and change plans.
- **Treat model output as a source: non-deterministic, shifting with each model or prompt version.** (Understand
  and evaluate source systems, chapter 2: *strengthens*; Raw JSON beside flattened fields, chapter 8:
  *strengthens*.) Keep the raw JSON and flatten what agents query.

## Connectors: buy for running, let agents write the long tail

- **Buy a managed connector for each source you need run, monitored and backfilled; let an agent write the
  long-tail ones, and give each an owner.** (Managed data connectors, chapter 7: *bends*; APIs: managed connectors
  over custom code, chapter 5: *bends*.) An agent writes a connector in minutes and patches it when an API changes,
  so the build half of the case for buying goes; the run half remains: syncs need monitoring, alerting, backfills
  and someone accountable when one silently drops rows. Build where a vendor's per-row price outweighs the cost of
  running your own.
- **Treat every agent-written connector as software: in the repository, reviewed, tested, orchestrated and
  monitored.** (Ingestion is plumbing, shifting to streaming, chapter 7: *bends*; Shell scripts for small sources,
  chapter 7: *bends*.) The threshold for orchestration drops to the first job anyone depends on; a script nobody
  wrote down is forgotten by people and agents alike.
- **Prefer an API to a browser agent fetching a report; where none exists, check what the agent fetched.** (Web
  interface: manual downloads fail, chapter 7: *bends*.)

## Files and malformed data

- **Configure each file's dialect, encoding and schema explicitly and record them; never let a model's guess stand
  in production.** (CSV, the nonstandard standard, chapter 7: *holds*; Files remain a universal exchange medium,
  chapter 5: *bends*.) Models now read spreadsheets, PDFs and scans too, and misread a cell as confidently as they
  read one right, so validate what they extract.
- **Quarantine what fails, then let an agent diagnose and replay it.** (Error handling and dead-letter queues,
  chapter 7: *strengthens*.)
- **Keep files moving through object storage, with signed URLs for access that expires.** (Moving data with object
  storage, chapter 7: *holds*.)

## Upstream change

- **Write a data contract with each upstream owner, in a machine-readable form their agents and CI check
  against.** (Data contracts with upstream owners, chapter 5: *strengthens*; SLAs and SLOs with upstream, chapter 5:
  *bends*.) An agent honours only the contract it can read; a verbal promise reaches no agent.
- **Detect every schema change, automate what you can absorb, and tell consumers, agents included, when one breaks
  their assumptions.** (Detecting and handling schema changes, chapter 7: *strengthens*; Schema registries for
  evolving message schemas, chapter 7: *strengthens*.) A registry rejects an agent's breaking change before any
  reviewer has to notice it.
- **Give each schema change, an agent's included, its own table branch before it reaches the main table.** (Schema
  change management: Git-like table versions, chapter 7: *strengthens*.)
- **Ask source teams to put tests, schema checks and contracts in their CI; agents make them cheap to add.**
  (Upstream support for the undercurrents, chapter 5: *strengthens*; Feedback loop with upstream stakeholders,
  chapter 1: *strengthens*.)

## Delivery and time

- **Design for out-of-order and repeated delivery, and make every write idempotent.** (Design for out-of-order and
  repeated delivery, chapter 5: *holds*; Delivery frequency and idempotency, chapter 5: *strengthens*.) Put it in
  the agent's instructions and in tests that shuffle and repeat the input.
- **Timestamp every phase: event, ingestion and processing time.** (Types of time, chapter 5: *strengthens*;
  Late-arriving data needs a cutoff, chapter 7: *holds*.) A person still decides when a window's numbers are final.
- **Feed fresh operational data to agents through CDC, not by querying the live tables.** (Change data capture from
  database logs, chapter 5: *holds*; Direct database connection, chapter 7: *holds*.)

## Moving between systems

- **Let agents rewrite a migration's pipelines, and spend the time saved proving the numbers still match.** (Data
  migration: sample, stage, move pipelines, chapter 7: *bends*.) Sample and stage as before, then compare outputs
  between old and new.
- **Know which data you own and which you borrow under a grant that can be withdrawn.** (Data sharing is not
  ingestion, chapter 7: *strengthens*; Data sharing under defined permissions, chapter 5: *strengthens*.) When the
  consumer of shared data is an agent, the grant names the agent, the person and the purpose.
