# Netflix Azure Data Engineering Project

## Project Overview

An end-to-end Azure Data Engineering project that ingests Netflix datasets, processes them using Medallion Architecture, and creates analytics-ready Delta tables.

## Technologies Used

- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2
- Azure Databricks
- PySpark
- Databricks Auto Loader
- Delta Lake
- Unity Catalog
- Databricks Workflows

## Architecture

GitHub CSV Sources → Azure Data Factory → ADLS Gen2 → Databricks Bronze → Silver → Gold

## Data Processing

### Bronze Layer
- Incremental CSV ingestion using Databricks Auto Loader
- Delta Lake storage
- 6,236 ingested records

### Silver Layer
- Filter invalid identifiers
- Remove duplicates
- Trim string columns
- Convert numeric and date columns
- Add processing timestamps
- 6,232 cleaned records
- 6,221 successfully parsed dates in the latest validated transformation

### Gold Layer
Four analytics tables:
- Content type summary
- Release-year summary
- Rating distribution
- Movie-duration summary

## Data Validation

- Bronze records: 6,236
- Silver records: 6,232
- Movies: 4,263
- TV Shows: 1,969
- Gold content total: 6,232

## Workflow Orchestration

A Databricks Job with two dependent notebook tasks:

1. Bronze and Silver processing
2. Gold analytics transformations

## Engineering Challenges

- Handling CSV and Delta format conflicts
- Correcting malformed date parsing
- Managing null identifiers
- Troubleshooting notebook and workflow errors
- Validating Silver and Gold record counts

## Future Enhancements

- Incremental Silver processing using Delta MERGE
- Automated data-quality checks
- CI/CD deployment
- Power BI dashboards
- Pipeline monitoring and alerting

