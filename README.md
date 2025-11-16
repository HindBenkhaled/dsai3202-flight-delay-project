# dsai3202-flight-delay-project
Flight Delay Prediction – Azure Data Engineering &amp; ML Pipeline

Flight Delay Project – Phase 1

This repository contains Phase 1 of the Flight Delay Forecasting project, which focuses on data ingestion, cleaning, transformation, and feature engineering following the Medallion Architecture (Bronze → Silver → Gold) using Azure Databricks, PySpark, and Delta Lake.


Medallion Layers
1️⃣ Bronze Layer (Raw):

-Ingested original dataset

-No modifications applied

-Stored as Parquet/Delta

2️⃣ Silver Layer (Cleaned):

-Handled missing values and schema fixes

-Converted columns and extracted useful time features

-Ensured consistent, validated data

3️⃣ Gold Layer (Feature-Ready):

Engineered new predictors:

-DepHour

-DelayCategory

-AvgDepDelayCarrier

-AvgDepDelayOrigin

-Final curated dataset saved as Delta for ML use

Final Gold Columns:
Year, Month, DayOfMonth, DayOfWeek, FL_DATE,
DepDelay, ArrDelay, DepHour, Distance,
Origin, Dest, UniqueCarrier, DelayCategory,
AvgDepDelayCarrier, AvgDepDelayOrigin


Team Members:
Name	ID
Hind Benkhaled	60105179
Farah Abo Shariha	60104384
