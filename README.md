# dsai3202-flight-delay-project
Flight Delay Prediction – Azure Data Engineering &amp; ML Pipeline
 
### Phase 1 – Data Engineering (Bronze → Silver → Gold)

This repository contains Phase 1 of the Flight Delay Forecasting project, which focuses on **data ingestion, cleaning, transformation, and feature engineering** following the **Medallion Architecture** using **Azure Databricks, PySpark, and Delta Lake**.

---

## Medallion Architecture Workflow

### 1️⃣ Bronze Layer (Raw)
- Ingested the original dataset from source  
- No transformations applied  
- Stored in Delta/Parquet format  

---

### 2️⃣ Silver Layer (Cleaned & Standardized)
- Removed/handled missing and incorrect values  
- Converted column types and extracted time-based fields  
- Ensured schema consistency and data quality  

---

### 3️⃣ Gold Layer (Feature-Ready for ML)
- Engineered features:
  - `DepHour`
  - `DelayCategory`
  - `AvgDepDelayCarrier`
  - `AvgDepDelayOrigin`
- Saved final curated Delta table for ML training  

---

## 📂 Final Gold Schema
Year (int)
Month (int)
DayOfMonth (int)
DayOfWeek (int)
FL_DATE (date)
DepDelay (double)
ArrDelay (double)
DepHour (int)
Distance (double)
Origin (string)
Dest (string)
UniqueCarrier (string)
DelayCategory (string)
AvgDepDelayCarrier (double)
AvgDepDelayOrigin (double)

## Team Members

| Name | Student ID |
|--------|------------|
| Hind Benkhaled | 60105179 |
| Farah Abo Shariha | 60104384 |
