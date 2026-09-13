# Data Engineering Roadmap

**Goal:** build the ability to design and build reliable data systems, while strengthening Python and SQL through real data problems.

**Priority:** become employable within the next 4–5 months. This roadmap shows the skills to build; it is not a rule that every advanced topic must be finished before applying for jobs.

## Phase 00 — Foundations & Mental Models 🔄

- [x] What Data Engineering is — introduced
- [x] Data Engineer vs Data Analyst vs Data Scientist vs Backend Engineer — demonstrated
- [x] Data lifecycle: source → ingest → store → transform → serve → consume
- [x] Data pipeline mental model
- [x] Batch vs streaming — introduced
- [x] Structured, semi-structured, unstructured data — demonstrated
- [ ] Data source, destination, pipeline, job, dataset, schema
- [x] Reliability basics: correctness, completeness, freshness, availability — introduced
- [ ] Source-of-truth and ownership
- [x] Production pipeline failure thinking: preserve raw data, separate validation/transformation, quarantine bad records, think about restart after failure

## Phase 01 — Data Formats & Schemas

- [ ] CSV
- [ ] JSON
- [ ] XML awareness
- [ ] Parquet
- [ ] Row-oriented vs columnar storage
- [ ] Schema and data types
- [ ] Schema evolution
- [ ] Encoding and delimiters
- [ ] Missing/null values
- [ ] Data contracts

## Phase 02 — Python for Data Engineering

Do not restart Python here. Pull required concepts from the Python Engineering / Python Backend Engineering tracks and apply them to data problems.

- [ ] pathlib and filesystem workflows
- [ ] file discovery and safe file handling
- [ ] iterators and generators for large data
- [ ] streaming/chunked processing
- [ ] JSON/CSV processing with the standard library
- [ ] validation and defensive parsing
- [ ] configuration and environment variables
- [ ] logging
- [ ] reusable data-processing modules
- [ ] error handling and recovery boundaries
- [ ] performance basics: memory vs CPU vs I/O

## Phase 03 — SQL Engineering

- [ ] SELECT/filter/order
- [ ] GROUP BY and aggregation
- [ ] JOINs
- [ ] NULL semantics
- [ ] CASE expressions
- [ ] subqueries
- [ ] CTEs
- [ ] window functions
- [ ] date/time operations
- [ ] deduplication
- [ ] data quality queries
- [ ] query plans and performance basics

## Phase 04 — Relational Databases

- [ ] relational model
- [ ] tables, keys, constraints
- [ ] normalization and denormalization
- [ ] PostgreSQL
- [ ] indexes
- [ ] transactions
- [ ] isolation awareness
- [ ] schema design
- [ ] database loading patterns
- [ ] connection management

## Phase 05 — ETL / ELT

- [ ] extraction patterns
- [ ] transformation patterns
- [ ] loading patterns
- [ ] ETL vs ELT
- [ ] full loads
- [ ] incremental loads
- [ ] upserts
- [ ] deduplication
- [ ] late-arriving data awareness
- [ ] raw/staging/processed layers
- [ ] pipeline boundaries

## Phase 06 — Data Quality & Validation

- [ ] completeness
- [ ] uniqueness
- [ ] validity
- [ ] consistency
- [ ] referential integrity
- [ ] schema validation
- [ ] business-rule validation
- [ ] quarantine/reject patterns
- [ ] data-quality reporting
- [ ] quality gates

## Phase 07 — Reliable Data Pipelines

- [ ] idempotency
- [ ] retries
- [ ] backoff
- [ ] checkpointing
- [ ] partial failure
- [ ] restartability
- [ ] dependency handling
- [ ] logging
- [ ] metrics
- [ ] freshness monitoring
- [ ] auditability

## Phase 08 — Data Warehousing & Dimensional Modeling

- [ ] OLTP vs OLAP
- [ ] analytical workloads
- [ ] fact tables
- [ ] dimension tables
- [ ] grain
- [ ] star schema
- [ ] surrogate keys
- [ ] slowly changing dimensions
- [ ] dimensional modeling trade-offs
- [ ] analytical marts

## Phase 09 — Orchestration

- [ ] workflow/DAG mental model
- [ ] scheduling
- [ ] dependencies
- [ ] retries and failure states
- [ ] backfills
- [ ] parameterisation
- [ ] Airflow or equivalent orchestration tool
- [ ] operational visibility

## Phase 10 — Cloud Data Engineering

Learn concepts before vendor-specific memorisation.

- [ ] object storage
- [ ] cloud databases/warehouses
- [ ] compute vs storage separation
- [ ] IAM basics
- [ ] secrets/configuration
- [ ] managed pipelines
- [ ] cost awareness
- [ ] one major cloud platform in practical depth

## Phase 11 — Big Data & Distributed Processing

- [ ] why distributed processing exists
- [ ] partitioning
- [ ] shuffling
- [ ] parallelism
- [ ] Spark mental model
- [ ] PySpark DataFrames
- [ ] joins and skew awareness
- [ ] distributed performance basics

Advanced distributed systems are awareness-first until job requirements justify deeper study.

## Phase 12 — Production Data Engineering

- [ ] environment separation
- [ ] secrets management awareness
- [ ] observability
- [ ] data lineage awareness
- [ ] incident/debugging workflow
- [ ] CI/CD for data code
- [ ] Docker
- [ ] reproducibility
- [ ] documentation/runbooks
- [ ] operational ownership

## Phase 13 — Showcase Projects

### Project 01 — Reliable Sales Data Pipeline

Build incrementally:

1. raw CSV/JSON sources
2. ingestion
3. validation
4. transformation
5. PostgreSQL storage
6. analytical schema
7. incremental processing
8. logging and quality checks
9. retries/idempotency
10. orchestration
11. Docker/CI where justified

### Project 02 — External API → Data Warehouse

- extract API data
- handle pagination/rate limits
- validate responses
- normalize nested data
- load to database
- incremental refresh
- quality and observability

### Project 03 — End-to-End Portfolio Pipeline

Combine the strongest concepts into one interview-defensible system.

## Phase 14 — Interview & Job Readiness

- [ ] explain pipeline architecture
- [ ] Python data-processing problems
- [ ] SQL interview problems
- [ ] ETL design scenarios
- [ ] data-quality scenarios
- [ ] incremental-load scenarios
- [ ] database/schema design questions
- [ ] debugging/failure scenarios
- [ ] project architecture explanation
- [ ] resume/GitHub/project presentation
- [ ] active job applications before roadmap completion

## Progress rules

- The current phase is the main learning focus.
- Mark a topic complete only after practical demonstration or retrieval.
- If a concept is already demonstrated in another repo, reuse it instead of relearning it from zero.
- Job applications do not wait for roadmap completion.
- Learn advanced tools after understanding the problem they solve.

## Status legend

- 🔄 In progress
- ⏳ Not started
- 🟡 Awareness / partial
- ✅ Demonstrated
- 🔁 Needs retrieval
