# Financial Transaction Intelligence Platform

An end-to-end financial transaction intelligence system for **fraud detection, graph-based risk analysis, and automated investigation**.

## Overview

The platform processes financial transactions through a structured **ETL → feature engineering → machine learning → graph analytics → alert generation → case investigation** pipeline, with an LLM layer for natural-language analytics.

### Key Results

* Processed **31K+ transactions** across **200+ customers and 40+ merchants**
* Engineered behavioral, historical, and graph-based fraud-risk features
* Random Forest achieved **0.86 ROC-AUC** with graph-enhanced features
* Generated **944 fraud alerts** and consolidated them into **34 investigation cases**
* Detected **12/12 seeded fraud rings**
* Evaluated detection performance under multiple **adversarial fraud-ring scenarios**
* Integrated **LLM-powered natural-language-to-SQL analytics** with read-only SQL validation

## Pipeline

```text
Transactions
     ↓
Data Quality & ETL
     ↓
SQLite Data Warehouse
     ↓
Behavioral + Graph Features
     ↓
Random Forest Risk Scoring
     ↓
Fraud Alerts
     ↓
Case Consolidation
     ↓
Evidence & Investigation
     ↓
LLM Analytics
```

## Tech Stack

**Python · Pandas · NumPy · SQL · SQLite · scikit-learn · Random Forest · Graph Analytics · Gemini · Matplotlib**

## Project Focus

The project demonstrates how **transaction-level machine learning can be complemented by relationship-based graph intelligence** to identify coordinated fraud patterns and support analyst-oriented investigation workflows.

> **Note:** The dataset is synthetic and the project is intended for academic and portfolio purposes.
