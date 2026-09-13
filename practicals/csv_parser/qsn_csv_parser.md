# Practical: CSV Parser

## Scenario

A company receives a daily sales CSV file from an external system. The file must be processed by a Python data pipeline before the records can be trusted by downstream systems.

Your task is to build a small, production-minded CSV ingestion and validation component.

## Input contract

The CSV file has this expected header:

```text
order_id,customer_name,amount,status,notes
```

Expected rules:

- `order_id`: required integer greater than 0
- `customer_name`: required non-empty text
- `amount`: required decimal number greater than or equal to 0
- `status`: required text; allowed values are `pending`, `shipped`, `delivered`, `cancelled`
- `notes`: optional text; an empty value is allowed
- delimiter: comma
- encoding: UTF-8

The business owner has defined these rules. Do not silently invent different business meanings.

## Sample input

Your implementation should be able to correctly handle records such as:

```csv
order_id,customer_name,amount,status,notes
1001,Rahul,1250.50,delivered,"Customer said ""box was damaged"""
1002,"Anita Sharma",899.00,shipped,"Call customer, tomorrow"
1003,John,0,pending,
1004,Meena,abc,delivered,Normal delivery
1005,Ravi,,shipped,Amount missing
1006,Sanjay,450.75,unknown,Invalid status
1007,"Smith, John",2300.00,delivered,"Normal delivery"
1008,Kiran,500.00,cancelled,"Customer requested, cancellation"
```

## Requirements

Build a reusable Python component that:

1. Reads the CSV safely using Python's standard library CSV support.
2. Does not use manual `split(",")` parsing.
3. Validates the expected header.
4. Validates the structure of each row.
5. Validates field values according to the input contract.
6. Converts valid values from CSV text into appropriate Python types.
7. Separates valid records from invalid records.
8. Keeps the original invalid record available for investigation.
9. Records a clear rejection reason for every invalid record.
10. Preserves enough information to identify the source row, including row number.
11. Produces a useful processing summary, including at least:
    - total rows read
    - valid rows
    - invalid rows
12. Handles malformed input without silently accepting bad data.
13. Handles quoted commas and embedded double quotes correctly.
14. Uses clear responsibilities rather than putting the entire pipeline into one large function.

## Engineering expectations

Treat this as production-minded code, not a classroom script.

Use where appropriate:

- type hints
- docstrings
- clear function/module responsibilities
- explicit error handling
- useful logging
- `pathlib` for filesystem paths where appropriate
- configuration rather than scattered magic values
- tests for important behaviour
- Ruff for code quality
- a CI workflow that runs the project's quality checks

You have **not been formally taught pytest yet**, so do not spend time learning the whole pytest framework before starting this task. If you use pytest, use only what is needed for this project; we will learn and review the testing concepts as they become necessary.

Do not add frameworks or dependencies just to make the project look advanced.

## Important design question

Think carefully about this case:

```text
1004,Meena,abc,delivered,Normal delivery
```

The row can be parsed structurally, but the amount is invalid.

Your pipeline should not throw away the whole file just because one row is bad. Decide how your design should process valid rows while preserving invalid rows for investigation.

Also think about what should happen if the **header itself is wrong**. This is different from one bad data row.

## Expected high-level flow

You should design the exact implementation yourself, but the system should ultimately follow this kind of boundary:

```text
                    CSV FILE
                       │
                       ▼
                    READ
                       │
                       ▼
                    PARSE
                       │
                       ▼
               STRUCTURE CHECK
                       │
                       ▼
                VALUE VALIDATION
                    /       \
                   /         \
                  ▼           ▼
               VALID       INVALID
                  │           │
                  ▼           ▼
               PROCESS     QUARANTINE
                  │           │
                  └─────┬─────┘
                        ▼
                    SUMMARY
```

This diagram describes the pipeline boundary, not the implementation for you.

## Acceptance criteria

The solution is considered successful when:

- quoted fields are parsed correctly
- the expected header is enforced
- valid rows become correctly typed records
- invalid rows are rejected with useful reasons
- invalid rows remain available for investigation
- row numbers can be traced back to the source file
- the final summary accurately reflects the input
- the code is readable and maintainable
- Ruff passes
- the CI workflow passes
- important behaviour is covered by tests
- the design can be explained clearly in an interview

## Constraints

- Python standard library for CSV parsing
- No Pandas for the parser itself
- No manual comma splitting
- No silent data correction unless the input contract explicitly permits it
- Do not over-engineer the solution

## Deliverable

Create the implementation inside this practical's directory.

You decide the final project structure, module names, test structure, and CI workflow based on the requirements above.

Before writing the implementation, be able to explain:

1. What are the responsibilities of each part?
2. Where does parsing end and validation begin?
3. What happens to a bad row?
4. What happens when the header is wrong?
5. What information should quarantine contain?
6. How would you test the important behaviours?
7. How would you make the component safe to maintain and extend?
