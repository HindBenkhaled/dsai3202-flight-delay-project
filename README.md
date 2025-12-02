#  Flight Delay Forecasting – Azure Data Engineering & Machine Learning Pipeline

This project builds a complete end-to-end **Flight Delay Prediction system** using  
**Azure Databricks, PySpark, Delta Lake, and MLflow**, following the **Medallion Architecture**.

We use the *Airline On-Time Performance Dataset* to clean, transform, engineer features, and train machine learning models that classify whether a flight will be **delayed or on-time**.

---

##  Project Overview

Flight delays are a major operational challenge for airlines.  
This project aims to **predict flight delays** by analyzing factors such as:

- Departure time  
- Day of week  
- Distance  
- Origin & destination  
- Airline performance  
- Historical average delays  

Our pipeline transforms **raw data → clean data → ML-ready features → trained models**.

---

# Phase 1 — Data Engineering (Bronze → Silver → Gold)

We implemented the **Medallion Architecture** to build a scalable data pipeline.

---

## 1️ Bronze Layer – Raw Data
- Ingested the original dataset exactly as provided  
- Stored in Delta/Parquet format  
- No transformations applied  

---

## 2️ Silver Layer – Cleaned & Standardized Data
Performed full preprocessing including:

- Handling missing values  
- Fixing incorrect column types  
- Trimming whitespace in string fields  
- Cleaning delay columns and converting them to numeric  
- Extracting time-based features (e.g., departure hour)  
- Ensuring schema consistency and data quality  

---

##  Gold Layer – Feature-Ready Dataset

Created a curated table for ML with engineered features:

### Engineered Features
- `DepHour` – scheduled departure hour  
- `DelayCategory` – (OnTime / Minor / Major)  
- `AvgDepDelayCarrier` – airline’s average historical delay  
- `AvgDepDelayOrigin` – airport’s average historical delay  

### Final Table
Saved as Delta under:
```
gold/features_v1
```

### Final Schema Includes
Year, Month, DayOfMonth, DayOfWeek, DepDelay, ArrDelay,  
DepHour, Distance, Origin, Dest, UniqueCarrier, DelayCategory,  
AvgDepDelayCarrier, AvgDepDelayOrigin

---

# Phase 2 — Machine Learning (Binary Classification)

Phase 2 builds a complete ML workflow using **PySpark MLlib** and **MLflow**.

---

## Problem Definition
We frame the prediction task as **binary classification**:

- **0 → On Time**
- **1 → Delayed**

This simplifies the model and improves predictive performance.

---

## Feature Preparation

### Numerical Features
- Year  
- Month  
- DayOfMonth  
- DayOfWeek  
- DepHour  
- Distance  
- AvgDepDelayCarrier  
- AvgDepDelayOrigin  

### Categorical Features
- Origin  
- Dest  
- UniqueCarrier  

Categorical features were encoded using **StringIndexer + OneHotEncoder**,  
then combined with numerical features using a **VectorAssembler**.

---

## Train/Test Split
The Gold dataset was split into:

- **70% training**
- **30% testing**

---

## Models Trained
We trained and evaluated four ML models:

- **Logistic Regression**  
- **Random Forest Classifier**  
- **Gradient Boosted Trees (GBT)**  
- **Linear SVM**

Each model was wrapped in a full preprocessing + training pipeline.

---

## Evaluation Metrics
For each model, we computed:

- Accuracy  
- F1-Score  
- AUC-ROC  
- Confusion Matrix  

These metrics were used to compare performance across models.

---

## MLflow Experiment Tracking
All runs were logged using **MLflow**, including:

- Metrics  
- Parameters  
- Confusion matrices  
- Saved Spark ML models  

This ensures reproducibility and easy comparison between models.

---

#  Team Members

| Name | Student ID |
|--------|------------|
| **Hind Benkhaled** | 60105179 |
| **Farah Abo Shariha** | 60104384 |

---



