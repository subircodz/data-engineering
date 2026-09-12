# Data Roles and System Boundaries

## Main problem each role solves

Different roles can work on the same data system, but their main problems are different.

### Backend Engineer

Builds and operates application services and business logic.

Examples:
- build an order API
- validate an application request
- save an order to the application database
- return a response to the client

### Data Engineer

Builds reliable paths that make data available and trustworthy for downstream use.

Examples:
- ingest application data
- validate and transform records
- load data into analytical storage
- handle failures, retries, repeated runs, and data quality

### Data Analyst

Uses available data to answer business questions and explain what happened.

Examples:
- Which product sold the most?
- Why did revenue fall yesterday?
- Which region is performing badly?

### Data Scientist

Uses data for prediction, modelling, experimentation, and other statistical or machine-learning work.

Examples:
- Can we predict next month's sales?
- Which customers may stop buying?
- Can we detect unusual transactions?

## The roles overlap

The difference is mainly the problem being solved, not the tool being used.

A Data Engineer may write Python and SQL. A Backend Engineer may process data. A Data Analyst may write complex SQL. A Data Scientist may build production services.

A useful system view is:

```text
Backend Engineer
      ↓
Operational application data
      ↓
Data Engineer
      ↓
Reliable / usable data
     ↙       ↘
Data Analyst  Data Scientist
```

This is a mental model, not a strict company structure.

## Debugging a wrong business number

When a business number is wrong, do not assume the whole pipeline is broken. Compare the data at each boundary and find where it first becomes incorrect.

Example:

```text
Application DB       ₹8.5L  ✓
       ↓
Ingested             ₹8.5L  ✓
       ↓
Transformed          ₹8.5L  ✓
       ↓
Warehouse            ₹10L   ✗
       ↓
Dashboard            ₹10L
```

The first incorrect boundary is the warehouse load/storage step, so investigation should start there.

If the database directly queried by the dashboard contains the correct ₹8.5L but the dashboard shows ₹10L, investigate the dashboard query, filters, or calculations instead.

## Boundary-based debugging

Use evidence instead of guessing:

1. identify the expected value
2. check the value at each major boundary
3. find the first boundary where it becomes wrong
4. investigate that step

Example boundaries:

```text
Source → Ingest → Validate → Transform → Store → Serve → Dashboard
```

This approach narrows the search area and avoids treating the whole system as one large unknown.

## Retrieval checks

Be able to answer without copying the note:

1. What is the main problem solved by a Backend Engineer?
2. What is the main problem solved by a Data Engineer?
3. What is the main problem solved by a Data Analyst?
4. What is the main problem solved by a Data Scientist?
5. Why is the tool used not enough to distinguish these roles?
6. If a source contains ₹8.5L, the transformed data contains ₹8.5L, but the warehouse contains ₹10L, where would you investigate first?
7. If the dashboard's source database contains the correct value but the dashboard shows the wrong value, what would you investigate?
