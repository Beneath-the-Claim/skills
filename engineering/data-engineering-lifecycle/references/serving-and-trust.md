# Serving data to people, dashboards, models and agents

Read this when the user is serving data to analysts, dashboards, ML, an AI assistant (text-to-SQL, retrieval, an
assistant inside a product) or an agent that writes back into business systems. The rules in `SKILL.md` still
apply; this file adds the detail.

## Trust is the product

- **Build trust with checks, and treat one visible wrong number as the loss it is.** (Trust as the root of
  serving, chapter 9: *strengthens*.) An agent states a wrong figure as fluently as a right one, with the query and
  the stale table hidden from the user, so bad data now fails confidently and travels further before anyone
  checks. Validation, observability, SLOs, reconciliation against the system of record and an evaluation set of real
  questions with agreed answers are how a team earns it.
- **Test a text-to-SQL or retrieval product on your own schema and your own questions, never on a vendor's
  benchmark.** (Benchmark wars: buyer beware, chapter 4: *strengthens*.) Accuracy claims are often measured on
  small, clean schemas unlike a real company's.
- **Trace an agent's wrong answer back to its source.** (Build, learn, improve: serving loops back, chapter 9:
  *bends*.) An agent rarely complains about bad data, so listening to complaints is not enough: log each question,
  the query or documents behind the answer, and the lineage to the source, so a complaint becomes an upstream fix.
  Review the logged queries and failed questions as the feedback analysts used to give (Business analytics:
  dashboards, reports, ad hoc, chapter 9: *bends*).

## Agents are a new kind of consumer

- **Design serving for agents as a consumer of their own, through a semantic layer with scoped access.** (Three
  kinds of analytics, chapter 2: *bends*; Self-service needs the right audience, chapter 9: *bends*.) Agents ask
  unpredictable questions in plain language, fire generated queries at volume and need every definition written
  down. Chat lowered the skill barrier to self-service; definitions and guardrails now decide whether it works.
- **Point agents at views, marts and the metrics layer, never at raw tables.** (Views for access and convenience,
  chapter 8: *strengthens*; Semantic and metrics layers, chapter 8: *strengthens*; Data marts: refined warehouse
  subsets, chapter 3: *bends*.) A view limits what an agent sees and carries what it cannot know, such as the
  deduplication of an insert-only table. A mart now scopes an agent's context and access more than it speeds
  queries.
- **Give agents their own compute and budget, as you would any major workload.** (Serving from OLAP databases,
  chapter 9: *holds*.) Separate clusters by use case, and the engineer's check on generated SQL extends from BI
  tools to agents.
- **Keep agents off the production database the application runs on.** (Analytics on OLTP does not scale, chapter
  5: *strengthens*; Single tier: prototyping, not production, chapter 3: *strengthens*.) For fresh operational
  state, give them a fast follower fed by CDC (The fast-follower approach, chapter 8: *strengthens*), and if they
  must query a source in place, give them federation's rules: read-only, tightly scoped, production protected (Query
  federation for exploration and control, chapter 8: *strengthens*; Data virtualization, used with care, chapter 8:
  *strengthens*).
- **Enforce tenant isolation in the data layer, never in the agent's query.** (Embedded analytics: isolate each
  tenant, chapter 2: *strengthens*; User access: single versus multitenant, chapter 3: *strengthens*.) An
  in-product assistant can drop the tenant filter, follow an injected instruction or retrieve from a mixed index,
  so use row-level policies, per-tenant credentials the agent cannot widen, and separate indexes.
- **Serve in-product assistants through governed metric endpoints, with per-query limits and cost caps.**
  (Embedded analytics: latency, speed, concurrency, chapter 9: *bends*.)
- **Give retrieval for agents its own serving path, with its own freshness and access checks.** (Serving ML
  alongside analytics, chapter 9: *bends*; ML basics a data engineer should know, chapter 9: *bends*.) Documents
  parsed, chunked and embedded into vector indexes carry permissions that must follow each document. Embeddings,
  retrieval, evaluation sets and logging of prompts and outputs now lead the ML a data engineer must know.
- **Serve one file in one place.** (File exchange, from email to lake, chapter 9: *strengthens*.) Assistants index
  mailboxes and shared drives, so every stale copy is a candidate answer an agent may quote.

## Freshness: stream where an action needs it

- **Ask what action the data drives, and who takes it, before choosing real time.** (Streaming-first serving, tied
  to action, chapter 9: *holds*; Operational analytics: data for immediate action, chapter 2: *holds*; What's the
  use case, who's the user, chapter 9: *holds*.) An agent can be the actor that responds at once, which adds cases
  where streaming pays; a decision made on trends gains nothing from second-by-second numbers, whoever reads them.
- **Do not plan a streaming platform to feed agents; feed them from batch-fresh tables, retrieval indexes and, for
  live state, a call to the source.** (The live data stack, chapter 11: *bends*; Streaming pipelines and
  real-time analytical databases, chapter 11: *bends*.) The successor to the modern data stack came through
  language models and retrieval more than streaming, and most of what agents read arrives fine in batches.
- **Stamp every phase with its time, so an agent can tell stale data from fresh.** (Types of time, chapter 5:
  *strengthens*.) Show the as-of time with every answer.

## Agents that act on data

- **Guard every loop in which an agent writes back to a live system before it compounds.** (Reverse ETL feedback
  loops need guardrails, chapter 9: *strengthens*; Automate repetitive actions behind dashboards, chapter 11:
  *strengthens*.) Monitoring, spend caps and a person's approval for costly actions; automate the routine action
  and keep a person approving the expensive one.
- **Build or buy the write-back by its running cost, not its build cost.** (Reverse ETL: serve where users work,
  chapter 2: *bends*.) An agent writes a custom sync in hours; API changes, rate limits and silent failures keep the
  case for a managed tool where those costs are high.
- **Make every action an agent can call idempotent.** (Delivery frequency and idempotency, chapter 5:
  *strengthens*.) Agents retry what they are unsure of.
- **Capture what an agent read, decided and wrote.** (The fusion of data with applications, chapter 11:
  *strengthens*; CRUD and extracting its history, chapter 5: *strengthens*.) CDC history is how you see and undo what
  an agent changed in a business system.
