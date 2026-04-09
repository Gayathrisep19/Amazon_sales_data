
# Amazon Sales Data – Medallion Architecture (Databricks + PySpark)

## Project Overview
This project processes Amazon sales data to derive business insights using a **Medallion (Bronze–Silver–Gold) architecture** implemented in **Databricks with PySpark and Delta Lake**.

The pipeline ensures data reliability, schema enforcement, and scalable analytics-ready outputs.

---

## Architecture
Raw data flows through three layers:

**Bronze → Silver → Gold**

---

## Bronze Layer (Raw Ingestion)
- Raw sales data is read from **Databricks Volumes**
- Data is ingested as-is into **Bronze Delta tables**
- Schema is explicitly defined and enforced
- Metadata such as source file name and ingestion timestamp is captured
- Designed to track schema changes and maintain raw data lineage

---

## Silver Layer (Clean & Standardized)
- Reads data from Bronze Delta tables
- Performs data quality checks:
  - Null handling
  - Range and validity checks
  - Correct data type casting
  - Standardized column naming
- Produces clean, trusted datasets stored as **Silver Delta tables**
- No aggregations are performed at this stage

---

## Gold Layer (Business Aggregates)
- Reads from Silver Delta tables
- Applies aggregations to derive business insights such as:
  - Monthly sales trends
  - Category-level performance
  - Customer-level metrics
- Curated outputs are stored as **Gold Delta tables**
- Views are created on top of Gold tables where flexibility is required

---

## Technologies Used
- PySpark
- Databricks
- Delta Lake
- Databricks Volumes

---

## Outcome
The final Gold layer provides analytics-ready datasets that can be used directly for reporting, dashboards, and downstream consumption.
``
