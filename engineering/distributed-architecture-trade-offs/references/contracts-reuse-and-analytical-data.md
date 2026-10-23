# Contracts, shared code and analytical data

## Contracts

**68. Treat every join as a contract, the wiring nobody wrote down included.** (Hard parts contract: all the wiring,
chapter 13: *strengthens*; Contract: wherever two pieces join, chapter 1: *holds*.) An agent breaks the wiring
nobody wrote down: a cache, a start-up order, a shared file. Every place an agent touches a system is a join.

**69. Let agents pick the wire format; people decide what is shared and how tightly.** (Three decisions in contract
design, chapter 13: *holds*.)

**70. Set strictness per collaborator, and make it strict wherever an agent reads the contract.** (Contract
strictness per collaborator, chapter 13: *bends*; Strict contracts: fidelity for coupling, chapter 13: *bends*.) An
agent acts with confidence on a field it misread, even where the data changes slowly. Inside one codebase strict
contracts now cost less.

**71. A slow channel still justifies a loose contract.** (ADR: loose contract for the mobile app, chapter 13:
*holds*.) Agents write the update faster; an app store's review queue does not move.

**72. A state object passed between agents is stamp coupling.** (Stamp coupling, chapter 13: *holds*; Stamp
coupling for workflow management, chapter 13: *holds*; Stamp coupling wastes bandwidth, chapter 13: *bends*.) It
has the same uses and the same risks, and an oversized payload costs an agent context on every call.

## Shared code

**73. Couple only to what changes slowly, and put model SDKs and agent toolkits behind an interface you own.**
(Abstraction and rate of change, chapter 8: *strengthens*.) Agents make your own code change faster, not slower;
they write well against stable frameworks and guess at internal or fast-moving APIs.

**74. Decide how each kind of shared code is reused, and write it down.** (Code reuse is a fact of life, chapter 8:
*strengthens*; Duplication or coupling depends on style, chapter 8: *holds*.) Agents duplicate by default; whether
a copy or a dependency is right still depends on the style.

**75. One shared model of a concept for every domain is still a mistake.** (Reuse, the most abused abstraction,
chapter 8: *holds*.) However fast an agent drafts it.

**76. Pin every shared library, and version a shared service's endpoints.** (Always version shared libraries,
chapter 8: *strengthens*; Shared service change risk, chapter 8: *strengthens*.) An agent on the latest version
builds on ground that moves while it works, and an agent caller often adapts silently to changed behaviour instead
of failing loudly.

**77. Choose a shared service for volatile code and for agent callers; a library for the rest.** (Shared service,
called at runtime, chapter 8: *bends*; Shared library, bound at compile time, chapter 8: *bends*; Shared library
granularity, chapter 8: *bends*.) With agents porting and upgrading, libraries fit code in several languages if one
test suite binds the ports, and can be finer if agents can find what each holds.

**78. Keep authentication, limits and logging outside agent-written code.** (Sidecar pattern, chapter 8:
*strengthens*; Service mesh as operational interface, chapter 8: *strengthens*; Orthogonal reuse pattern, chapter 8:
*holds*.) Where no prompt can switch them off; agent tracing and guardrails cut across domains like monitoring and
get their own layer.

**79. Keep platform interfaces stable.** (Reuse via platforms, chapter 8: *strengthens*.) Agents rewrite behind
them and call through them.

## Analytical data

**80. Keep analytical data tied to its domain, and let each data product say what its columns mean.** (Analytical
data needs domain partitioning, chapter 14: *strengthens*; Domain ownership of data, chapter 14: *strengthens*; Data
as a product, chapter 14: *strengthens*.) An agent acting alone cannot ask what a column means, and cannot rebuild
domain context from bare tables.

**81. Run data governance as code on every access.** (Computational federated governance, chapter 14:
*strengthens*.) No reviewer can follow agents reading data.

**82. Declare a pipeline's needs as a contract.** (Integration brittleness from transforming on ingestion, chapter
14: *strengthens*; Data Warehouse pattern, chapter 14: *bends*.) Agents change operational schemas faster than
pipelines can follow, and cut a warehouse's build effort without removing its coupling to every schema.

**83. A raw lake's privacy risk has grown.** (Data lake privacy exposure risk, chapter 14: *strengthens*; Data Lake
pattern: load, then transform, chapter 14: *bends*.) Models combine and infer faster than any analyst, and without
domain context they transform raw data wrongly with confidence.

**84. Give agents a domain's data through its data product, apart from the operational database.** (Data product
quantum, chapter 14: *holds*; DPQ as a cooperative quantum, chapter 14: *bends*; DPQ belongs to static coupling,
chapter 14: *strengthens*.) Agents pick data products at run time, so every product's contract must hold for
consumers nobody planned, and a product that reads another service's internals breaks with each refactor.

**85. Keep operations and analytics apart, and asynchronous.** (Data sidecar: asynchronous, eventually consistent,
chapter 14: *holds*; Operational versus analytical data, chapter 1: *bends*.) Agents want fresher data, but a
transactional sync couples analytics to operations; analytical data that agents act on within seconds is a third
kind, between the two.
