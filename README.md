# Uber Trip Data – ETL & Dimensional Modeling

Transforms raw NYC taxi trip records (TLC Yellow Taxi format) into an analytics-ready **star schema** using Python and pandas.

![Data model](img/uber%20data%20model.png)

## What it does

1. **Extract** – loads 100,000 trip records from `data/uber_data.csv`.
2. **Transform** – parses timestamps and builds 7 dimension tables plus 1 fact table:

| Table | Content |
|---|---|
| `datetime_dim` | Pickup/drop-off timestamps broken into hour, day, month, year, weekday |
| `passenger_count_dim` | Distinct passenger counts |
| `trip_distance_dim` | Distinct trip distances |
| `rate_code_dim` | Rate code ID mapped to name (Standard rate, JFK, Newark, ...) |
| `pickup_location_dim` | Pickup latitude/longitude |
| `dropoff_location_dim` | Drop-off latitude/longitude |
| `payment_type_dim` | Payment type ID mapped to name (Credit card, Cash, ...) |
| **`fact_table`** | Surrogate keys to every dimension + fare, extra, MTA tax, tip, tolls, surcharge, total amount |

3. **Load-ready output** – each table is a clean DataFrame with surrogate keys, ready to load into a data warehouse.

## Tech stack

Python · pandas · Jupyter Notebook · dimensional modeling (star schema)

## How to run

```bash
pip install pandas jupyter
jupyter notebook uber_data_pipeline.ipynb
```

## Repository structure

```
├── data/uber_data.csv          # 100k raw trip records
├── img/uber data model.png     # Star schema diagram
└── uber_data_pipeline.ipynb    # Transformation notebook
```
