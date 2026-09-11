# Data Engineering: Basic System Model

## What Data Engineering does

Data Engineering builds the path that takes data from a real source to a useful and trustworthy destination.

It is more than moving files or writing SQL. The system also needs to deal with validation, transformation, storage, failures, repeated runs, and data quality.

## Basic data lifecycle

```text
Source
  ↓
Ingest
  ↓
Store
  ↓
Transform
  ↓
Serve
  ↓
Consume
```

### Source

Where the data starts.

Examples:
- CSV file
- REST API
- application database
- event stream
- external vendor

### Ingest

Get the source data into a place where the pipeline can work with it reliably.

Questions:
- Can we connect to the source?
- When does data arrive?
- What if the source is unavailable?
- Can the same input arrive twice?

### Store

Keep data so it can be processed or used later.

Examples:
- object storage
- PostgreSQL
- data warehouse

### Transform

Change data into the form needed by the next stage.

Examples:
- convert data types
- clean or reject invalid records
- join datasets
- calculate values
- standardise fields

### Serve

Make prepared data available to the people or systems that need it.

Examples:
- analytical tables
- warehouse views
- API endpoints
- exported datasets

### Consume

The people or systems that use the prepared data.

Examples:
- dashboard
- analyst
- ML system
- business report
- application

## Pipeline mental model

Do not think only:

> Read CSV → write database

Think:

> Where does the data come from? What state of the data should we keep? What must be checked or changed? What happens if a step fails or runs again?

## Basic pipeline boundaries

```text
[ SOURCE ] → [ INGEST ] → [ PROCESS ] → [ DESTINATION ]
```

Each part should have a clear job. This makes failures easier to find and fix.

## Batch vs streaming

### Batch

Process data in groups at scheduled or triggered times.

Examples:
- process yesterday's sales every morning
- load a CSV every hour

### Streaming

Process events continuously or in very small groups as they arrive.

Examples:
- transaction events
- application activity
- sensor events

The choice depends on required speed, complexity, cost, and the type of data.

## Basic reliability checks

A useful pipeline should be judged on at least these four points:

- **Correctness:** Is the result right?
- **Completeness:** Did the required data arrive?
- **Freshness:** Is the data recent enough?
- **Availability:** Can users or systems get the data when needed?

## Practical scenario: nightly sales file

A shop receives a CSV every night and wants a dashboard showing daily revenue.

Example fields:

```text
order_id, customer_id, product_id, quantity, price, sale_date
```

Think through:

1. source
2. ingestion
3. where the data is stored
4. validation and transformation
5. destination/serving layer
6. consumer
7. one possible failure at each major boundary

### Production version

Now assume:

- 500,000 rows arrive each day
- duplicate files can arrive
- some rows are malformed
- files can arrive late
- the job can crash and restart
- daily totals must be trustworthy

A good first set of decisions is:

- keep the original input unchanged
- validate data before sending valid records forward
- keep malformed records separately with a reason
- do not confuse duplicate records with processing the same input twice
- if the database load fails, the next run must be able to continue safely without creating bad duplicates
- log important steps, counts, failures, and completion
- a run is successful only when the expected work and required checks pass

## Failure and restart example

Suppose the pipeline has 500,000 rows and has already inserted 300,000 valid, transformed rows into PostgreSQL when it crashes.

The important question is not only:

> “Start from row 300,001.”

First ask:

> “How do we know which data was successfully committed?”

The system needs a reliable way to know what has already been processed. Otherwise a restart can insert the same data again or skip data.

This problem leads to concepts such as transactions, checkpoints, restartability, and **idempotency**. Those concepts are covered later in the roadmap.

## Checks

Be able to explain these without copying the note:

1. What problem does Data Engineering solve?
2. What is the difference between ingesting and transforming data?
3. Why should pipeline stages have clear responsibilities?
4. When is batch processing a reasonable choice?
5. What are correctness, completeness, freshness, and availability?
6. Why should raw input normally be preserved?
7. What should happen to malformed records?
8. Why is “remove duplicates” not always enough when a pipeline runs twice?
9. What problem appears when a database load fails halfway through?
