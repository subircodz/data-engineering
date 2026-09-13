# CSV

## What CSV is

CSV is a text-based tabular data format commonly used to exchange data between systems.

The important Data Engineering question is not only whether a file looks like a table. The pipeline must be able to read it safely and know what each field means.

CSV values arrive as text. The pipeline must apply the expected data types and business rules.

## Delimiters

The separator is configurable. A CSV-like file may use:

- comma: `,`
- semicolon: `;`
- tab: `\t`

Do not assume the delimiter from the filename alone.

## Quoting

A delimiter inside a quoted field is data, not a field separator.

```text
105,"Smith, John",900.00
```

This contains three fields:

```text
105 | Smith, John | 900.00
```

Do not parse CSV with a simple `split(",")` because it cannot correctly handle quoted fields.

## Embedded quotes

A common CSV representation of a quote inside a quoted field uses two double quotes.

```text
103,John,"He said ""Hello"""
```

The value of the last field is:

```text
He said "Hello"
```

A real CSV parser should handle these rules.

## Header and structure checks

A pipeline should have an explicit expectation for the header and structure.

Useful checks include:

- expected column names
- expected column count
- expected delimiter
- expected field structure

Whether differences such as header case are accepted should come from the pipeline contract, not from an accidental parser behaviour.

## Encoding

A file is bytes before it becomes text. The pipeline must decode those bytes using the expected encoding.

UTF-8 is common, but encoding should not be guessed blindly when the source contract specifies it.

A UTF-8 BOM can also affect the first header. For example, an expected `id` may appear as `\ufeffid` if the BOM is not handled.

## Missing and null values

These values do not automatically mean the same thing:

```text
<empty field>
NULL
N/A
0
```

For example, `0` can be a real numeric value while `NULL` may mean unknown. The pipeline should use the rule defined by the data owner or data contract.

## Malformed rows

Examples of invalid input include:

- wrong number of fields
- invalid numeric format
- invalid date format
- missing required value
- value that violates a business rule

Invalid data should not silently enter the trusted dataset, and rejected data should not silently disappear.

## Validation flow

```text
                 CSV FILE
                    │
                    ▼
                 Decode
               (encoding)
                    │
                    ▼
                  Parse
         (delimiter + quoting)
                    │
                    ▼
            Check structure
        (header + field count)
                    │
                    ▼
           Validate values
         (types + null rules)
               /        \
              ▼          ▼
           VALID       INVALID
              │          │
              ▼          ▼
           Process    Quarantine
```

## Quarantine

A rejected record should normally remain available for investigation rather than disappearing.

Useful quarantine information includes:

- original/raw record
- source file
- row number
- rejection reason
- ingestion time

A pipeline may process valid records while quarantining invalid records when partial processing is allowed by the business requirement. It must still report the counts and status clearly so downstream users do not mistake partial processing for a complete successful load.

## Data ownership

The data owner, business owner, or data steward defines the business meaning and rules for the data.

The Data Engineer implements those rules reliably in the pipeline.

If a rule is ambiguous, the engineer should clarify it instead of silently inventing meaning.

Core rule:

> **Business owner defines what the data means; Data Engineer designs how to enforce that meaning reliably.**

## Current implementation direction

For Python ingestion, use the standard library `csv` module rather than manual string splitting.

The first practical implementation should demonstrate:

1. safe CSV reading
2. quoted-field handling
3. header inspection
4. row validation
5. separation of valid and invalid records
6. rejection reasons

The implementation will be treated as the practical demonstration for completing the CSV roadmap item.
