---
name: financial-data
description: Inspect and validate unfamiliar market datasets before feature engineering or backtesting.
---

# Financial data

Choose pandas, NumPy or PyArrow to match the format and schema. Declare dependencies with `uv add`; run readers with `uv run --locked`. Preserve source dtypes and nulls.

Inventory files, fields, units, instrument identifiers, ordering and provenance. Establish timezone, exchange calendar, interval meaning and value availability. Check OHLCV price/volume validity and bar construction; trade ordering and corrections; book sides, depth, updates and sequence gaps. Profile missing values, duplicates, outliers, corporate actions and universe changes. Document resampling boundaries and return conventions: simple/log and adjusted/raw. Specify and test every imputation or exclusion, including forward-fills. Preserve raw inputs and the reproducible cleaning record.
