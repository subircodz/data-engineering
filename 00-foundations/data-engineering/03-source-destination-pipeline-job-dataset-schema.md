# Data Source, Destination, Pipeline, Job, Dataset, and Schema

## Core mental model

```text
DATASET = WHAT data
SCHEMA = SHAPE / RULES of that data
SOURCE = WHERE data comes from
DESTINATION = WHERE data goes
PIPELINE = HOW data moves / processes
JOB = ONE EXECUTION of the pipeline
```

These terms describe different parts of a data system. They should not be treated as interchangeable.

## Data source

A **data source** is where data comes from.

Examples:

- CSV file
- JSON file
- REST API
- application database
- PostgreSQL database
- Excel file
- logs or events

Example:

```text
sales_2026_09_13.csv
```

This file is the source for the pipeline.

## Destination

A **destination** is where the pipeline sends its processed data.

Examples:

- PostgreSQL
- data warehouse
- object storage
- analytical database
- another application or service

Example:

```text
PostgreSQL → sales table
```

The destination is not always a database. The correct destination depends on how the data will be used.

## Pipeline

A **pipeline** is the defined flow of work that moves and/or processes data from source to destination.

Example:

```text
CSV
 ↓
Read
 ↓
Validate
 ↓
Transform
 ↓
Load
 ↓
PostgreSQL
```

A pipeline is the process or design. It is not one particular execution of that process.

## Job

A **job** is one execution (run) of a pipeline.

For example, a pipeline may be designed to process the daily sales file every night at 2 AM.

```text
Pipeline = daily sales processing flow
Job      = the actual execution of that flow on 2026-09-13
```

`2 AM` is the scheduled time, not the job itself.

One pipeline can produce many jobs:

```text
Pipeline
  ├── Job: 2026-09-11
  ├── Job: 2026-09-12
  └── Job: 2026-09-13
```

## Dataset

A **dataset** is a collection of related data treated as one logical set.

For example, the rows in a daily sales file can form a sales dataset.

```text
sales_2026_09_13.csv

order_id | product_id | quantity | price | sale_date
------------------------------------------------------
1001     | P10        | 2        | 50.00 | 2026-09-13
1002     | P11        | 1        | 80.00 | 2026-09-13
```

The dataset describes the logical data. The CSV is one physical representation of that data.

## Schema

A **schema** describes the structure and rules of a dataset.

It can define things such as:

- field/column names
- data types
- whether a value can be NULL
- primary keys
- relationships
- allowed values
- other constraints

Example:

```text
order_id  → INTEGER
price     → NUMERIC
sale_date → DATE
```

A real schema may also say that `order_id` is required and unique, depending on the business rules.

For money such as price, `NUMERIC` is usually more suitable than `INTEGER` because prices can contain decimal values.

## How the concepts connect

```text
                  DATA SYSTEM

       ┌─────────────────────────┐
       │       Data Source       │
       │                         │
       │ sales_2026_09_13.csv    │
       └────────────┬────────────┘
                    │
                    ▼
       ┌─────────────────────────┐
       │        Pipeline         │
       │                         │
       │ read → validate        │
       │       → transform      │
       │       → load           │
       └────────────┬────────────┘
                    │
                    ▼
       ┌─────────────────────────┐
       │       Destination       │
       │                         │
       │ PostgreSQL / warehouse  │
       └─────────────────────────┘

Dataset = logical collection of related data
Schema  = structure and rules describing the dataset
Job     = one execution of the pipeline
```

## Why the distinction matters

These terms help engineers describe failures precisely.

Example:

- The **source** file arrived successfully.
- The **dataset** contains 500,000 rows.
- The **schema** expects `quantity` to be a positive integer.
- The **pipeline** validates and transforms the data.
- A **job** runs the pipeline at 2 AM.
- The **destination** is PostgreSQL.

If the PostgreSQL load fails, the source and pipeline are not automatically the problem. Check the boundaries and identify where the first unexpected change occurred.

## Engineering checks

Be able to answer these without copying the note:

1. What is the difference between a pipeline and a job?
2. Is `2 AM` a job or a scheduled time?
3. What is the difference between a dataset and a schema?
4. Can the same dataset exist in more than one physical format or location?
5. In a CSV → PostgreSQL system, identify the source, destination, pipeline, dataset, schema, and one job.
6. Why is `NUMERIC` often better than `INTEGER` for a price column?
