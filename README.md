# Aml-transaction-monitoring-pipeline((Batch + Streaming)

## Overview
This project demonstrates an end-to-end data pipeline that ingests transactions, applies enrichment + rules,
runs data quality checks, and produces analytics-ready outputs for compliance reporting and investigation workflows.

## Problem Statement
Banks receive high-volume transaction feeds from multiple sources. Data arrives with schema drift, duplicates,
late events, and inconsistent customer identifiers. Compliance teams need consistent outputs with auditability.

## Solution (High-Level)
- Batch ingestion for historical loads + daily files
- Streaming ingestion for near real-time transaction events
- Standardization + enrichment (customer, accounts, geo)
- Data quality + reconciliation (counts, nulls, duplicates, thresholds)
- Curated outputs for reporting + downstream systems

## Architecture
(Add an image under /docs and link it here)
![Architecture](docs/architecture.png)

## Tech Stack
- Python, PySpark
- Kafka (streaming)
- AWS S3 / Glue or Databricks (processing)
- Snowflake (warehouse) / Postgres (local demo)
- Great Expectations (optional for quality checks)

## Data Flow
1. Ingest raw data to `raw/`
2. Transform to standardized `staging/`
3. Apply rules + enrichment into `curated/`
4. Run quality checks and generate audit report

## How to Run (Local Demo)
```bash
# create venv
python -m venv .venv
source .venv/bin/activate  # windows: .venv\Scripts\activate

pip install -r requirements.txt
python src/ingest/run_ingest.py
python src/transform/run_transform.py
python src/quality/run_quality.py

Sample Input/Output

Input: sample_data/input.csv

Output: sample_data/output.csv

Key Features

Schema validation + duplicate handling

Late-arriving event handling strategy

Reconciliation report (source vs target)

Config-driven rules (easy to extend)

***Future Enhancements***

Add unit tests for transformations

Add orchestration (Airflow)

Add monitoring dashboards
