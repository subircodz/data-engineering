# Day 1 — Data Engineering Mental Model

## What is Data Engineering?

Data Engineering is the engineering work required to make data reliably available in a useful form for people, applications, and analytical systems.

A Data Engineer is not simply “moving files” or “writing SQL”. The core problem is building a trustworthy path from a data source to a useful destination.

## Core data lifecycle

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

Where the data originates.

Examples:
- CSV files produced by a business system
- REST API
- application database
- event stream
- external vendor

### Ingest

Getting data from the source into a system where it can be processed reliably.

Questions:
- How do we connect?
- How often do we pull data?
- What happens if the source is unavailable?
- Can the same data arrive twice?

### Store

Persisting data so it can be processed or consumed later.

Examples:
- object storage
- PostgreSQL
- data warehouse

### Transform

Changing raw data into a form that is correct and useful.

Examples:
- type conversion
- cleaning invalid records
- joining datasets
- calculating metrics
- standardising fields

### Serve

Making prepared data available to consumers.

Examples:
- analytical tables
- warehouse views
- API endpoints
- exported datasets

### Consume

The people or systems using the data.

Examples:
- dashboard
- analyst
- ML system
- business report
- application

## Pipeline mental model

A pipeline is a controlled sequence of data-processing steps.

Do not think:

> “Read CSV → write database.”

Think:

> “Where does trustworthy data come from, what transformations are required, where should each state of the data live, and what happens when any step fails?”

## Four basic pipeline boundaries

```text
[ SOURCE ] → [ INGEST ] → [ PROCESS ] → [ DESTINATION ]
```

Each boundary should have a clear responsibility.

A failure in one boundary should be understandable rather than becoming one large block of code.

## Batch vs streaming

### Batch

Data is processed in groups at scheduled or triggered intervals.

Examples:
- process yesterday's sales every morning
- load a CSV once per hour

### Streaming

Data is processed continuously or in very small increments as events arrive.

Examples:
- transaction events
- application activity
- sensor events

The choice depends on requirements such as latency, complexity, cost, and data characteristics.

## Reliability dimensions introduced today

When judging a data pipeline, ask:

- **Correctness:** Is the output right?
- **Completeness:** Did required data arrive?
- **Freshness:** Is the data recent enough?
- **Availability:** Can consumers get the data when needed?

These dimensions will become more concrete in later phases.

## Day 1 focused scenario

A shop receives a CSV file every night containing that day's sales. The business wants a dashboard showing daily revenue.

Before coding, identify:

1. source
2. ingestion step
3. storage location
4. transformation required
5. destination/serving layer
6. consumer
7. one likely failure at each major boundary

## Day 1 production scenario

The same shop now has:

- 500,000 sales rows per day
- occasional duplicate files
- occasional malformed rows
- files sometimes arrive late
- the job may be restarted after a failure
- the dashboard must contain trustworthy daily totals

Design the pipeline boundaries and explain:

1. What should happen to raw data?
2. Where should validation happen?
3. What happens to malformed records?
4. How would you prevent duplicate processing?
5. What should happen if the database is unavailable halfway through the load?
6. What would you log?
7. What does “successful pipeline run” mean?

## Retrieval questions

Answer without looking at this note:

1. What problem does Data Engineering solve?
2. What is the difference between ingesting and transforming data?
3. Why should pipeline stages have clear boundaries?
4. When would batch processing be a reasonable choice?
5. Name four dimensions of data reliability introduced today.

## Definition of done

Day 1 is demonstrated when you can design both scenarios above and explain the reasoning behind your boundaries and failure handling without copying a template.
