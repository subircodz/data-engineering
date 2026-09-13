# Source of Truth and Data Ownership

## Source of truth

A source of truth is the system or dataset that is officially authoritative for a specific piece of data.

There may be many copies of the same information, but they do not all have equal authority.

```text
Application DB ──┐
CRM             ──┼──> Same business data
Excel           ──┘

          ↓
  Which one is authoritative?
          ↓
     SOURCE OF TRUTH
```

Source of truth is usually **data-specific**, not necessarily one system for the whole company.

Examples:

- Customer contact details → CRM
- Payment status → payment system
- Product price → product system
- Employee salary → HR system
- Sales transactions → application database

A warehouse is not automatically the source of truth. It is often a downstream copy used for analytics.

## Ownership

Data ownership means a person or team is responsible for the meaning, quality, rules, access, and resolution of issues for that data.

The Data Engineer should not decide business truth alone when systems disagree. The Data Engineer should work with the appropriate data owner, system owner, or data steward.

## When sources disagree

Never choose a source just because it is:

- a database
- newer-looking
- easier to query
- maintained by a familiar team
- the source currently used by the pipeline

First establish the officially authoritative source.

Then use it as the reference when investigating discrepancies.

Example:

```text
Application DB → ACTIVE
CRM            → INACTIVE  ← official source of truth
Excel          → ACTIVE

Warehouse      → ACTIVE
                         ↓
                    MISMATCH
                         ↓
                Investigate pipeline
```

Possible investigation areas include:

- wrong source selected
- stale source extract
- incorrect transformation
- incorrect join
- duplicate or old record
- partial load
- previous pipeline run overwriting the value
- another process changing the warehouse

Do not silently replace the value based on a guess. The discrepancy itself may indicate a pipeline, source, ownership, or business-rule problem.

## What should be documented

For important datasets, document:

- source system
- authoritative dataset/table
- data owner or responsible team
- field meaning
- expected schema
- update frequency
- freshness expectation
- quality expectations
- downstream consumers

## Production mental model

```text
                 DATA
                  │
          ┌───────┴────────┐
          │                │
       SOURCE           COPIES
          │                │
          ▼                ▼
   Source of Truth     CRM / files /
          │            warehouse / etc.
          │
          └──────┬─────────┘
                 ▼
          Pipeline checks
                 │
          discrepancy found
                 │
                 ▼
        investigate first
```

The key rule is:

> **Establish authority first. When data disagrees, use the source of truth as the reference and investigate the pipeline or source instead of guessing.**
