# Structured, Semi-structured, and Unstructured Data

## Structured data

Structured data follows a predefined data model. The fields are clearly defined and data is usually organised into rows and columns.

Examples:

- PostgreSQL tables
- SQL tables
- CSV files
- Excel tables

```text
id,product,quantity,price
101,Laptop,2,50000
102,Mouse,5,800
103,Keyboard,3,1500
```

## Semi-structured data

Semi-structured data has an identifiable structure, but the structure is flexible. Fields can be optional, nested, or different between records.

Examples:

- JSON
- XML
- API responses
- logs and events

```json
{
  "customer": {
    "id": 101,
    "name": "Rahul"
  },
  "orders": [
    {"product": "Laptop", "quantity": 1}
  ]
}
```

## Unstructured data

Unstructured data does not follow a predefined data model that directly organises its business information into fields.

Examples:

- images
- videos
- audio
- PDFs and scanned documents
- free-form text

Unstructured data can still contain useful information. A data pipeline may extract that information and create structured or semi-structured data from it.

Example:

```text
"Rahul Das bought a laptop on 10-Sep-2026.
He says the screen is damaged."
```

Possible extracted structure:

```text
customer = Rahul Das
product  = laptop
date     = 2026-09-10
issue    = damaged screen
```

## Important distinction

The format being structured does not guarantee that the actual data is clean.

For example, an Excel sheet may have rows and columns but still contain blank rows, totals mixed with data, inconsistent values, or other problems.

So keep these ideas separate:

```text
Structure  → how the data is organised
Quality    → whether the data is correct, complete, and usable
```

## Practical classification

| Data | Classification | Reason |
|---|---|---|
| PostgreSQL orders table | Structured | Fixed schema with rows and columns |
| Nested JSON API response | Semi-structured | Fields and nesting exist, but the structure is flexible |
| Free-form complaint text | Unstructured | No predefined business fields |
| Customer photo | Unstructured | Business information is contained in visual content rather than predefined fields |

## Engineering use

The classification helps decide how data should be ingested, validated, parsed, stored, and transformed.

A pipeline may also convert one type into another. For example:

```text
Unstructured text/image
        ↓
Information extraction
        ↓
Structured / semi-structured data
        ↓
Validation + transformation
        ↓
Database / warehouse
```
