# Securing, governing and operating data when agents build and read it

Read this when the user is giving agents access to data, deciding who owns or answers for data, setting up
monitoring, testing or incident response for pipelines agents write, or handling sensitive data. The rules in
`SKILL.md` still apply; this file adds the detail.

## Access: the grant is the control

- **Treat an agent as an insider that never tires.** (Hardened perimeter versus zero trust, chapter 3:
  *strengthens*; People are the weakest link, chapter 10: *bends*.) An agent runs inside with real credentials and
  can be steered by instructions hidden in the documents, tickets and web pages it reads. Authenticate every action
  it takes, and assume that text it reads may try to talk it into something.
- **Give agents scoped, short-lived credentials held in a secrets manager, never in code or in their context.**
  (Protect your credentials, chapter 10: *strengthens*; Credential handling in data science code, chapter 9:
  *strengthens*.) Coding agents read notebooks and repositories into their context and may echo a key into a
  transcript or a commit, or write one into code to make it run. Delete keys an agent no longer needs.
- **Break the glass for an agent as for a person.** (Broken-glass process for live data, chapter 7: *bends*.)
  When an agent needs live sensitive data to debug, a person approves the access, which is scoped to the issue,
  expires and is logged. The unit moves from a person's ticket to an agent session.
- **Develop on synthetic or cleansed data and deploy through automation, with agents' hands off production
  too.** (Touchless production for sensitive data, chapter 7: *bends*.) Models now make realistic synthetic data
  cheap, so developing away from production data is a reachable default.
- **Run code an agent wrote, or a model produced, in a sandbox stronger than a shared container.** (Containers and
  container escape, chapter 4: *strengthens*.) Share a cluster only among mutually trusted code, and agent-written
  code nobody has read is not that.
- **Let agents change infrastructure only through code a person can review.** (Infrastructure as code, chapter 2:
  *strengthens*.) An agent clicking through a console leaves no diff to check.

## Sensitive data: what an agent never sees cannot leak

- **Drop or hash sensitive fields at ingestion unless a named downstream use needs them.** (Privacy: question
  sensitive data first, chapter 7: *strengthens*; The power of negative thinking, chapter 10: *holds*.) Agents copy
  what they read into prompts, transcripts, logs and embeddings, each a new access path that storage encryption does
  nothing for. Encryption stays the baseline and does nothing against an agent holding valid keys (Encryption:
  baseline, not magic bullet, chapter 10: *holds*).
- **Make a deletion request reach every copy, embeddings and prompt logs included.** (Data lifecycle management:
  archive and destroy, chapter 2: *strengthens*; Update patterns for persisted data, chapter 8: *strengthens*.)
  Catalogue the vector stores, caches, agent memories and evaluation sets that hold personal data, or a deletion
  cannot find them.
- **Serve obfuscated data as one layer only.** (Serve obfuscated data where traceable, chapter 9: *bends*.) Models
  make synthetic data cheaper and re-identification easier, so access control carries more of the protection.

## Ownership, meaning and the record

- **Name one accountable person for each table, stream or field that matters.** (Data accountability per portion of
  data, chapter 2: *strengthens*.) Agents add tables and fields faster than a team names owners by default, and an
  agent cannot answer for a number.
- **Govern meaning on purpose: origin, relationships and meaning written where agents read them.** (Intentional
  data governance and discoverability, chapter 2: *strengthens*; Data catalogs and metadata management, chapter 6:
  *strengthens*.) The catalog is the map an agent works from; keep it current.
- **Let models draft the metadata; keep people owning what each definition means.** (Metadata, automated with
  humans involved, chapter 2: *bends*; Master data management, chapter 2: *bends*.) A model matches
  records and drafts descriptions; only the business agrees what a customer is.
- **Keep lineage as the record of how each number was made.** (Data lineage as audit trail, chapter 2:
  *strengthens*.) When agents write the transformations, lineage is the only account of a derivation, and an agent
  debugging a number or honouring a deletion request needs it written down.
- **Log every agent action against the agent session and the person it acted for.** (Logging, monitoring, and
  alerting, chapter 10: *strengthens*; Logs: content, encoding, resolution, latency, chapter 5: *strengthens*.)
  Billing alerts now catch runaway agents as well as intruders.

## Operating what agents build

- **Write down what good data means as tests, because an agent consumer never notices an odd number.** (Data
  quality: accuracy, completeness, timeliness, chapter 2: *bends*; Data-quality tests against silent regressions,
  chapter 7: *strengthens*.) Test the statistics, not only the nulls: the most dangerous regressions are silent
  distortions, and a model fed one answers confidently.
- **Check what each change does to the data, not only whether the code runs.** (Data Observability Driven
  Development, chapter 2: *bends*; Observability and monitoring, chapter 2: *strengthens*.) Agents land many
  more changes per person; a data diff on each one is now table stakes.
- **Keep dependencies explicit in the orchestrator, and start near the top of the automation ladder.**
  (Orchestration by dependency DAG, chapter 2: *holds*; Automation matures in steps, chapter 2: *bends*.) Agents
  write tested, monitored DAG deployment cheaply; the operating burden stays.
- **Keep incident response blameless so the people directing agents report what went wrong.** (Blameless, fast
  incident response, chapter 2: *holds*.)
- **Make DataOps a habit of the organisation, not a tool purchase.** (DataOps: culture first, three pillars,
  chapter 1: *holds*; Security theater versus security habit, chapter 10: *strengthens*.) Models make policies and
  audit evidence cheap; only habit separates the letter of compliance from real security.
- **Research the attacks agents brought: prompt injection, exfiltration through tool calls, over-privileged agent
  credentials, packages that do not exist.** (Active security, not fixed routines, chapter 10: *strengthens*;
  Security for low-level data engineering, chapter 10: *strengthens*.) No 2022 checklist covers them.
- **Ask every vendor where its models run, what they keep and what its agents can read.** (Ask vendors about data
  management, chapter 4: *strengthens*.)
- **Keep the security policy short, and add what agents may touch, which secrets may enter a prompt and who approves
  an agent's actions.** (An example security policy, chapter 10: *bends*.)
