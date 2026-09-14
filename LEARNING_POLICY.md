# Data Engineering Learning Policy

This repo is for building practical Data Engineering skills that support the Data Analyst, Data Engineering, Data Operations, and data-focused Python job targets. It is not a place to collect classroom notes or memorise tools.

## Main goal

The main goal is **meaningful job readiness within the next 4–5 months**, subject to actual progress and interview opportunities.

Target roles:

- Data Analyst
- Data Engineer / Junior Data Engineer
- Data Operations / data-focused Python roles
- Similar roles where the user's existing IT and operations experience is useful

Learning is important, but **solid projects, practical implementation, and interview readiness are equally important**.

Do not delay projects until the whole roadmap is finished.

## Core engineering standard

The user should become able to answer:

> Where did this data come from?
> Is it valid?
> What happened to it?
> Can I trust it?
> Can I reproduce the result?
> What happens when the pipeline fails?
> Can the system recover?
> Can I explain the result to another person?

The repeated pipeline mental model is:

```text
SOURCE
  ↓
EXTRACT
  ↓
VALIDATE
  ↓
TRANSFORM
  ↓
LOAD
  ↓
STORE
  ↓
SERVE / ANALYZE
  ↓
MONITOR
```

Reliability concepts such as quarantine, rejection reasons, data quality, lineage, observability, idempotency, retries, recovery, schema changes, and incremental processing should be introduced through real problems rather than as isolated theory.

## Job-first rule

For every topic, ask:

> Is this useful for a real project, an interview, or a job requirement?

If yes, learn it properly.

If it is useful but not important right now, keep it at awareness level.

If it becomes a rabbit hole and does not help the current job target, park it for later.

Core skills get priority over advanced topics.

## Practical job skills

The track should stay connected to skills commonly used in Data Analyst and Data Engineering jobs, including where relevant:

- Excel
- Power BI
- SQL
- Python
- Pandas
- PostgreSQL / relational databases
- MySQL / MariaDB
- files and APIs
- data cleaning and transformation
- ETL / ELT
- data validation and data quality
- Git / GitHub
- testing
- basic Docker and CI
- basic orchestration
- basic cloud knowledge

Do not add a tool only because it looks good on a resume.

## Python policy

Python is a tool for solving data problems in this repository, not a second Python language course.

Do not restart Python from zero here.

If a data problem needs Python:

1. teach only the missing Python concept needed for the problem
2. connect it to the pipeline
3. let the user implement it
4. test and review it
5. point primarily Python-language topics toward the Python Engineering or Python Backend Engineering repo

A project should not be forced to teach several unrelated Python concepts at once.

If a Python concept such as imports, packages, or execution context becomes a separate learning gap, park it as a Python Engineering topic instead of allowing it to derail the Data Engineering practical.

## Project-first rule

Projects are not an optional final step.

Knowledge should move into projects as soon as there is a real reason to use it.

The portfolio should contain a small number of **serious, believable projects**, not many tiny tutorial projects.

A project should show that the user can work with real data, make reasonable decisions, handle bad data and failures, and explain what was built.

Project architecture should match the current learning objective. Prefer clear responsibilities, but **do not introduce multiple modules, packages, or dependencies merely to make a small practical look advanced**. A single script with well-separated functions is acceptable when it keeps the learning focus on the data problem.

## Current practical learning rule

For the first CSV parser practical, use a **single Python script with clear functions** rather than multiple modules. This is intentional because the current learning objective is CSV parsing, validation, quarantine, output handling, and pipeline reasoning—not package/import architecture.

The script should still have clear responsibilities, for example:

```text
main()
  ├── read / parse CSV
  ├── validate header
  ├── validate rows
  ├── collect valid records
  ├── collect invalid records
  ├── write cleaned output
  ├── write quarantine output
  └── produce summary
```

This is **function-level modularity**, not multi-file modular architecture. Multi-file structure can be introduced later when the project or roadmap genuinely requires it.

## Data quality

Treat data quality as a first-class engineering concern.

Always distinguish:

> the pipeline ran successfully

from:

> the data is correct.

Important checks include:

- missing values
- invalid types
- invalid formats
- duplicate records
- unexpected values
- business-rule violations
- schema drift
- referential integrity
- rejected records
- quarantine
- validation reports
- row-count and reconciliation checks

The business/data owner defines the business meaning and rules. The Data Engineer implements those rules reliably. Do not silently invent business meaning when a rule is ambiguous.

## Idempotency

Idempotency is a critical reliability concept and should be taught repeatedly through practical ingestion and loading scenarios.

The user should understand why running the same pipeline twice must not unintentionally duplicate or corrupt data.

## AI-assisted Data Engineering

AI may be used to accelerate:

- SQL generation
- transformation code
- validation rules
- pipeline scaffolding
- documentation
- test generation
- debugging
- data-quality checks
- query optimisation suggestions

But AI output must be treated as a proposal, not proof of correctness.

For important work, verify:

- row counts
- duplicates
- nulls
- totals
- business rules
- source/target consistency
- sample records
- edge cases

AI-generated SQL can be syntactically correct and logically wrong. AI-generated transformations can silently corrupt data.

## Testing and validation

Testing is not a checkbox. The purpose is to prove important pipeline behaviour.

Use the mental model:

```text
INPUT
  ↓
EXPECTED RESULT
  ↓
ACTUAL RESULT
  ↓
DIFFERENCE
  ↓
EXPLANATION
```

Use unit tests, integration tests, sample datasets, data-quality assertions, reconciliation, row-count checks, and business-rule checks where appropriate.

The user has not been formally taught pytest yet. Do not delay a practical until the whole pytest framework is learned. Introduce only the testing concepts needed at the point they become useful.

## SQL policy

Treat SQL as a major job skill for both Data Analyst and Data Engineering roles.

Prioritise:

- SELECT, filtering, sorting
- aggregation, GROUP BY, HAVING
- joins
- NULL handling
- CASE
- subqueries and CTEs
- window functions
- date/time operations
- deduplication
- data-quality queries
- constraints, indexes, transactions
- query reasoning and performance basics

When writing SQL, consider correctness, NULL behaviour, duplicates, row counts/cardinality, joins, indexes when relevant, query cost, readability, and maintainability.

Use business/data scenarios rather than disconnected puzzles.

## Analyst connection

Connect engineering work to analytical outcomes:

```text
pipeline
   ↓
reliable dataset
   ↓
SQL analysis
   ↓
metrics
   ↓
dashboard / report
   ↓
business decision
```

Do not turn this into a separate Data Science curriculum.

## Portfolio standard

Prefer practical projects such as:

- CSV ingestion pipelines
- database ingestion
- API ingestion
- validation/quarantine pipelines
- incremental loading
- data-quality systems
- analytical database workflows
- operational reporting pipelines

A strong project should progressively demonstrate, where relevant:

- source data
- ingestion
- validation
- transformation
- loading
- logging
- error handling
- tests
- documentation
- reproducibility
- reliability

Do not repeatedly create generic sales-dashboard projects.

## Interview preparation

Interview preparation happens throughout the track, not only at the end.

Prepare through reasoning around questions such as:

- What is ETL vs ELT?
- What happens when a pipeline fails?
- How do you validate data?
- How do you handle rejected records?
- What is idempotency?
- How do you prevent duplicate loading?
- How do you handle schema changes?
- How do you debug a pipeline?
- How do you monitor a pipeline?
- Why PostgreSQL?
- How would you process a large CSV?
- What happens if the database goes down halfway?
- How would you make the pipeline restartable?
- How do you know the loaded data is correct?
- What is the difference between source data and dashboard output?

Do not train memorised definitions. Train the underlying system reasoning so the user can explain naturally.

## Weekly continuous assessment

Every week, deliberately assess without step-by-step guidance.

Check:

1. Python/data-pipeline implementation ability
2. SQL ability
3. Data Engineering concepts
4. debugging ability
5. interview explanation ability
6. project progress

Use a mixture of:

- explaining concepts from memory
- reasoning about a real data problem
- choosing between approaches and explaining why
- designing a small pipeline
- writing/debugging Python or SQL
- identifying failure cases
- reviewing project decisions
- interview-style questions

Classify important topics as:

- **Strong** — can explain and apply without help
- **Needs retrieval** — understands it but recall is weak
- **Weak / reteach** — mental model or implementation is not reliable
- **Revisit later** — useful, but not currently important enough for deeper study

Assessment results should influence the next week's study.

## Study time

A realistic target is **about 4–5 focused hours per day**, not 8–15 hours of passive study.

A normal day can roughly contain:

- 1.5–2 hours: new Data Engineering concepts
- 1.5–2 hours: hands-on implementation and exercises
- 30–45 minutes: retrieval and interview questions
- 30–60 minutes: project work

These are flexible ranges, not a strict timetable. Two focused hours on a difficult day are still useful.

As the track progresses, shift roughly from:

- early: 60% learning / 40% practice and retrieval
- later: 30% learning / 50% projects / 20% recall and interview preparation

## How we work

**Concept → Scenario → Reasoning → Design → Build → Review → Project use → Recall**

For an important topic:

1. understand what it is and why it exists
2. see a simple real-world case
3. add production problems only when useful
4. think about the design before seeing a complete solution
5. build and test it
6. review failure cases and improvements
7. use it in a real project when there is a reason
8. recall it later without copying the old solution

The mentor should explain the mental model and constraints first, then let the user propose the design. Do not remove the user's chance to think.

## Teaching language

Teaching must use **simple Indian English**.

Use simple words, short sentences, clear examples, and technical terms only when needed. Explain technical terms in simple language.

Do not use difficult English just to sound professional.

## Notes and documentation

Repo documents are **engineering notes**, not classroom notes or chat transcripts.

Avoid wording such as:

- Today we will learn...
- Learning objectives...
- The learner should understand...
- Lesson 1...

A useful engineering note should normally explain:

- what it is
- why it exists
- the mental model
- where it fits
- when to use it
- when not to use it
- important failure cases
- production points
- a small practical example
- useful checks or decisions

Keep notes short when a short reference is enough.

## Code review

Review in this order:

1. correctness
2. data flow
3. edge cases
4. failure handling
5. maintainability
6. testability
7. logging / observability
8. performance
9. security and configuration when relevant

Do not optimise before there is a real performance problem.

## Production thinking

A small example can teach one idea. Ask what changes when data is:

- large
- slow
- malformed
- duplicated
- late
- incomplete
- changed in schema
- processed more than once

Keep advanced cloud, distributed systems, and deep production topics at awareness level until the roadmap or a project makes them necessary.

## Scope control

This repository is specifically for **Data Analyst + Data Engineering career preparation**.

Do not turn it into:

- Data Science
- Machine Learning
- AI research
- advanced distributed systems for theory alone
- an unrelated Python curriculum

Only introduce advanced technologies when justified by the roadmap, job requirements, or a project problem.

## Repository discipline

Before changing the repository:

1. inspect README
2. inspect ROADMAP
3. inspect TODO if present
4. inspect relevant practicals
5. inspect latest commits
6. determine the exact current checkpoint

Do not duplicate notes.

After completing a topic or meaningful practical milestone:

- update the correct documentation
- update ROADMAP when the learning status changes
- update TODO when the project checkpoint changes
- preserve the repository structure
- commit meaningful work

Before a repository write, verify the current file state and blob SHA. After a write, verify that the file exists with the expected content.

## Progress and completion

The roadmap is not a race to finish checkboxes.

A topic is demonstrated when the user can reason about it and implement a reasonable solution without simply copying a recipe.

Reading about a topic is not enough.

Job applications should begin before the roadmap is complete.

## Main principle

> Learn what helps us get hired. Build real projects. Understand why things work. Practise interviews. Verify AI output. Avoid rabbit holes.
