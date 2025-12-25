# Task A: ETL Architecture Diagram

## ETL Architecture Diagram – Visual Representation

The following diagrams illustrate the conceptual serverless ETL pipeline designed for GreenStream Energy.

### High-Level ETL Workflow
![Electricity Data Workflow Steps](images/DiagramFlowComponents.png)

### Detailed Serverless ETL Architecture
![ETL Architecture Diagram](images/ETLArchitecture.png)

---

## Overview
The pipeline moves data from smart meters to analytics-ready storage using a **serverless approach**. 
Data processing triggers automatically when new files arrive.

## Workflow
1. **Source:** Raw CSV files from 50,000 smart meters.
2. **Raw Storage:** Landing zone to store original files for reference.
3. **Transformation Layer:** Cleaning, standardization, validation. Triggered automatically on new upload.
4. **Destinations:**
   - Structured DB (SQL) for daily reports and quick checks.
   - Analytical Archive (Parquet) for long-term research and AI models.
5. **Orchestration (Success/Failure):**
   - Success: Data saved, log created.
   - Failure: Retries 3 times, then moves to Dead Letter Queue for manual inspection.
