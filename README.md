# Weather Data Ingestion & ETL Pipeline

A Python-based data engineering project that ingests weather data from a public API, validates and transforms the incoming data, and builds a progressively more realistic ETL pipeline for reliable storage and analytics.

This project is being developed from scratch to practice real-world **data ingestion, data quality, transformation, storage, incremental processing, error handling, and pipeline orchestration** concepts.

---

## Project Goals

The goal is to build a complete weather data pipeline while understanding the engineering decisions behind each component rather than simply following a tutorial.

The project will progressively cover:

- REST API data ingestion
- JSON data handling
- Data extraction and transformation
- Schema design and validation
- Data quality checks
- Raw and processed data layers
- Parquet-based storage
- Incremental data ingestion
- Deduplication
- Error handling and retries
- Logging
- Configuration and environment variables
- PostgreSQL integration
- SQL-based analytics
- Pipeline scheduling and orchestration

---

## Planned Architecture

```text
                Weather API
                    │
                    ▼
              Data Ingestion
                    │
                    ▼
             ┌──────────────┐
             │  Raw / JSON  │
             │    Bronze    │
             └──────┬───────┘
                    │
             Validation &
             Transformation
                    │
                    ▼
             ┌──────────────┐
             │   Parquet    │
             │    Silver    │
             └──────┬───────┘
                    │
                    ▼
               PostgreSQL
                    │
                    ▼
                Analytics
```

As the project becomes more realistic, scheduling, logging, retries, and additional pipeline controls will be introduced.

---

## Data Pipeline

The pipeline will eventually follow this flow:

```text
Extract
   ↓
Store Raw Data
   ↓
Validate
   ↓
Transform
   ↓
Data Quality Checks
   ↓
Store Processed Data
   ↓
Load to Database
   ↓
Run Analytics
```

---

## Example Data

The processed dataset is expected to contain fields such as:

| Field | Description |
|---|---|
| `city` | City name |
| `country` | Country |
| `latitude` | Location latitude |
| `longitude` | Location longitude |
| `temperature` | Current temperature |
| `humidity` | Relative humidity |
| `wind_speed` | Wind speed |
| `weather_condition` | Weather condition |
| `observation_time` | Time of the weather observation |
| `ingestion_time` | Time the pipeline collected the record |

The final schema may evolve as the pipeline becomes more realistic.

---

## Data Quality

The pipeline will include validation rules to prevent unreliable records from reaching downstream storage.

Examples include:

- Required fields must be present
- City names cannot be empty
- Humidity must be within a valid range
- Wind speed cannot be negative
- Temperature must contain a valid numeric value
- Timestamps must be valid
- Duplicate records should be detected
- Records with invalid data should be handled separately rather than silently discarded

---

## Project Structure

The structure will evolve as new pipeline components are introduced.

An expected final structure is:

```text
weather-data-pipeline/
│
├── src/
│   ├── ingestion/
│   ├── transformation/
│   ├── validation/
│   ├── storage/
│   └── pipeline/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── tests/
│
├── config/
│
├── logs/
│
├── .env.example
├── requirements.txt
└── README.md
```

The structure may change as the implementation develops.

---

## Technology Stack

### Current / Core

- **Python**
- REST APIs
- JSON
- HTTP
- Git & GitHub

### Planned

- Pandas
- Parquet
- PostgreSQL
- SQL
- Python logging
- Environment variables
- Scheduling / orchestration

Additional technologies may be introduced only when they solve a real problem in the pipeline.

---

## Development Roadmap

### Phase 1 — API Ingestion

- Select a suitable weather API
- Understand its API documentation
- Make HTTP requests using Python
- Handle API responses
- Parse JSON data
- Extract required fields

### Phase 2 — Raw & Processed Data

- Store the original API response
- Create structured records
- Transform API data
- Write processed data to files
- Introduce a consistent schema

### Phase 3 — Data Quality

- Define validation rules
- Detect invalid records
- Handle missing values
- Detect duplicates
- Separate rejected records
- Add data quality checks

### Phase 4 — Incremental Pipeline

- Introduce observation timestamps
- Introduce ingestion timestamps
- Prevent duplicate ingestion
- Support repeated pipeline runs
- Handle incremental data correctly

### Phase 5 — Reliability

- Add structured logging
- Handle API failures
- Handle timeouts
- Implement retries where appropriate
- Handle invalid requests and rate limits
- Make individual failures observable

### Phase 6 — Database & Analytics

- Introduce PostgreSQL
- Design tables
- Load processed weather data
- Query the dataset using SQL
- Build analytical queries
- Analyze weather trends across cities

### Phase 7 — Scheduling & Orchestration

- Run the pipeline automatically
- Introduce scheduling
- Separate pipeline stages
- Track pipeline execution
- Explore orchestration concepts such as Airflow

---

## Example Analytics

Once sufficient historical data has been collected, the pipeline can support questions such as:

- Which city has the highest average temperature?
- What is the daily average temperature for each city?
- Which cities have the highest humidity?
- How does temperature change over time?
- What was the latest available observation for each city?
- How many records were successfully processed?
- How many records failed validation?
- How frequently does the pipeline fail?

---

## Engineering Principles

This project focuses on understanding **why** data engineering systems are designed in a particular way.

Key principles include:

- Preserve raw source data
- Validate data before downstream processing
- Separate ingestion from transformation
- Make pipelines repeatable
- Avoid duplicate ingestion
- Handle failures explicitly
- Keep configuration separate from code
- Make pipeline behavior observable through logs
- Design schemas intentionally
- Prefer reliable and maintainable solutions over unnecessary complexity

---

## Learning Objectives

By completing this project, the aim is to gain practical experience with:

```text
Python
   ↓
API Ingestion
   ↓
ETL
   ↓
Data Validation
   ↓
Data Quality
   ↓
File-Based Data Storage
   ↓
Incremental Processing
   ↓
PostgreSQL + SQL
   ↓
Scheduling / Orchestration
```

The project is intentionally developed in stages so that each new component is introduced to solve a specific engineering problem.

---

## Status

🚧 **In Progress**

The pipeline is being developed incrementally, starting with basic API ingestion and progressing toward a more production-oriented ETL workflow.

---

## Author

**Nabeel Islam**

B.Tech — Computer Science & Engineering

Focused on building practical Data Engineering skills through hands-on projects.
