# Data Engineering

A practical, job-focused Data Engineering workspace.

This repo is for learning how to build data systems that work with real data. It is not a collection of beginner tutorials or tool notes.

## Goal

Build the ability to take data from a real source, move it safely, check it, transform it, store it, and make it useful for other systems or people.

This track works together with the Python Backend Engineering and Python Engineering repos. We do not restart Python from zero here.

## How we work

**Understand → Reason → Design → Build → Test → Debug → Improve → Apply → Recall → Reuse**

For an important topic, first understand the problem. Then work through a real situation, design a solution, write the code, test it, and improve it.

The main focus is not memorising tools. The focus is making good engineering decisions.

## Other learning tracks

- **Python Backend Engineering** — main job-focused engineering track.
- **Python Engineering** — deeper Python and software-engineering work.
- **Data Engineering** — data systems, pipelines, SQL, databases, ETL/ELT, data quality, and production work.
- **AI Automation** — kept separate until the Python/backend base is stronger.

If a Python concept is needed here, learn only what is needed for the current data problem and connect it back to the Python repos.

## Roadmap

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

The main project will grow step by step instead of using many unrelated toy projects.

```text
raw files
   ↓
ingestion
   ↓
validation
   ↓
transformation
   ↓
PostgreSQL
   ↓
analytical model
   ↓
reliable pipeline
   ↓
orchestration
   ↓
production controls
```

Add a new part only when there is a real reason to add it.

## Engineering rules

Code and pipelines should gradually include:

- clear responsibilities between parts
- useful type hints
- validation of input data
- clear assumptions
- proper error handling
- useful logs
- repeatable processing
- idempotency where needed
- tests for important behaviour
- config and environment variables
- clean Git history and useful documentation
- performance checks based on actual need

Do not add complexity just to make a project look advanced.

## Definition of done

A topic is not complete just because we have read about it.

It is complete when we can:

1. explain it in simple words
2. say why we need it
3. say when to use it
4. design a solution for a real case
5. write and test the code
6. handle important failure cases
7. use the idea again later without copying a recipe

## Progress

`ROADMAP.md` is the source of truth for progress.

Important topics should leave a useful engineering note, code, test, or project change.

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
├── practicals/
│   └── csv_parser/
│       └── qsn_csv_parser.md
└── interview-prep/
```

## Main rule

> Understand the data problem first. Choose the tool second. Build it. Test it. Then make it reliable.
