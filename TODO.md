# Data Engineering TODO

## Current checkpoint

**Phase 01 — Data Formats & Schemas → CSV**

### CSV parser practical

Path: `practicals/csv_parser/`

- [x] Define CSV input contract
- [x] Create sample input data
- [x] Explore `csv.DictReader`
- [x] Verify quoted commas and embedded double quotes
- [x] Confirm CSV values arrive as text before validation
- [x] Decide to keep the first implementation as a single script
- [ ] Design `validate_row()` responsibility and return value
- [ ] Implement row validation
- [ ] Convert valid values to appropriate Python types
- [ ] Preserve invalid records with row number and rejection reason
- [ ] Write cleaned records to output CSV
- [ ] Write quarantined records to output CSV
- [ ] Produce processing summary
- [ ] Handle important malformed-input cases
- [ ] Add focused tests
- [ ] Run Ruff and fix findings
- [ ] Add/verify CI quality checks
- [ ] Review the practical against the acceptance criteria
- [ ] Recall the design and explain it as an interview scenario

### Expected sample result

- Total rows: **8**
- Valid rows: **5** — `1001`, `1002`, `1003`, `1007`, `1008`
- Invalid rows: **3** — `1004`, `1005`, `1006`

### Current design constraint

For this first practical, use **one Python script with clear functions**. Do not introduce multiple modules or package/import architecture unless a real project requirement later justifies it.

The current learning focus is CSV parsing, validation, type conversion, quarantine, output handling, testing, and data-pipeline reasoning.

## Later retrieval topics

- CSV edge cases and contracts
- parsing vs validation boundary
- business-owner rules vs engineering implementation
- quarantine and rejection reasons
- idempotency
- restartability and partial failure
- schema evolution
