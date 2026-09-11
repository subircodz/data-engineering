# Data Engineering

A practical, job-oriented Data Engineering learning and engineering workspace.

This repository is not a collection of beginner tutorials. The goal is to learn how real data systems are designed, built, tested, operated, and improved.

## Mission

Build the ability to take data from real sources, validate and transform it, store it correctly, move it through reliable pipelines, and produce useful data products.

The learning path is designed to reinforce the user's existing Python, SQL, analytics, and software-engineering work rather than restart Python from zero.

## Learning model

**Understand → Reason → Design → Implement → Test → Debug → Harden → Apply → Retrieve → Reapply**

For each major topic:

1. Learn the mental model and why the concept exists.
2. Work through a focused production-style scenario.
3. Design the solution before coding.
4. Explain the reasoning, assumptions, trade-offs, and failure cases.
5. Implement the solution.
6. Review correctness and production quality.
7. Apply the concept to the showcase project.
8. Revisit it later through retrieval and a new scenario.

## Relationship with other learning tracks

- **Python Backend Engineering** — primary engineering/employability track.
- **Python Engineering** — deeper Python fundamentals and software-engineering reasoning.
- **Data Engineering** — parallel data-system track that applies Python and SQL to real data problems.
- **AI Automation** — intentionally parked until the Python/backend foundation is stronger.

This repository must not become a duplicate Python course. When Python is needed, learn only the Python concept required to solve the data-engineering problem, then connect it back to the dedicated Python repositories.

## Roadmap at a glance

| Phase | Area | Status |
|---|---|---|
| 00 | Foundations & mental models | 🔄 Current |
| 01 | Data formats & schemas | ⏳ |
| 02 | Python for Data Engineering | ⏳ |
| 03 | SQL engineering | ⏳ |
| 04 | Relational databases | ⏳ |
| 05 | ETL / ELT | ⏳ |
| 06 | Data quality & validation | ⏳ |
| 07 | Reliable data pipelines | ⏳ |
| 08 | Data warehousing & dimensional modeling | ⏳ |
| 09 | Orchestration | ⏳ |
| 10 | Cloud data engineering | ⏳ |
| 11 | Big data & distributed processing | ⏳ |
| 12 | Production data engineering | ⏳ |
| 13 | Showcase projects | ⏳ |
| 14 | Interview & job readiness | ⏳ |

## Showcase project

The repository will gradually build one realistic data platform instead of isolated toy exercises.

Initial evolution:

**raw files → ingestion → validation → transformation → PostgreSQL → analytical model → reliable pipeline → orchestration → production controls**

The project will grow only as the required concepts are learned.

## Engineering standards

Projects should progressively include:

- clear boundaries and maintainable structure
- type hints where useful
- validation and explicit assumptions
- meaningful exceptions and failure handling
- logging and observability
- deterministic/reproducible processing
- idempotency where required
- tests for important behavior
- configuration through environment/config files
- Git discipline and documentation
- performance awareness based on evidence, not premature optimisation

## Definition of done

A topic is not complete because a lesson was read.

A topic is complete when the learner can explain the mental model, choose an appropriate approach, design it for a realistic scenario, implement it, handle important failure cases, and reapply the idea later without following a recipe.

## Progress tracking

`ROADMAP.md` is the source of truth for learning progress.

Each completed topic should leave behind a durable engineering note, practical code, or project change when appropriate.

## Learning policy

See [`LEARNING_POLICY.md`](LEARNING_POLICY.md).

## Repository structure

```text
data-engineering/
├── README.md
├── ROADMAP.md
├── LEARNING_POLICY.md
├── 00-foundations/
├── 01-data-formats/
├── 02-python-for-data-engineering/
├── 03-sql/
├── 04-databases/
├── 05-etl/
├── 06-data-quality/
├── 07-pipelines/
├── 08-data-warehousing/
├── 09-orchestration/
├── 10-cloud/
├── 11-big-data/
├── 12-production/
├── 13-projects/
└── interview-prep/
```

## Guiding principle

> Do not learn data engineering as a list of tools. Learn how to build reliable systems that move and transform data for a reason.
