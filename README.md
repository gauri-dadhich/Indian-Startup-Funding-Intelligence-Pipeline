

# Startup Funding Analytics Pipeline using Azure, Databricks & Medallion Architecture
## Notes

- If the notebooks do not render properly on GitHub, please use the **Raw** option to download the notebook or view the notebooks locally in Jupyter or Databricks.

- This project was developed using an **Azure for Students** subscription. Due to the limitations of the student subscription, **Unity Catalog (14-day trial)** was used for catalog and schema management.

- Sensitive credentials such as the **Azure Storage Account Key** are secured using **Azure Key Vault** and accessed through **Databricks Secret Scopes**, avoiding hardcoded secrets in the notebooks.

- Azure resources (ADLS Gen2, Azure Data Factory, Azure Databricks, and Azure Key Vault) must be configured in your own Azure subscription to execute this project end-to-end.


##  Project Overview

This project implements an end-to-end Startup Funding Analytics Pipeline using the Medallion Architecture (Bronze, Silver, Gold) on Microsoft Azure and Azure Databricks.

The pipeline automates data ingestion, transformation, analytics, and dashboard creation for Indian startup funding data. It demonstrates modern Data Engineering practices including Azure Data Factory orchestration, Delta Lake, Unity Catalog, Azure Key Vault, Databricks Dashboards, and secure credential management.

---

#  Architecture

The solution follows the Medallion Architecture:

```
Raw CSV
     │
     ▼
Azure Data Lake Storage Gen2
     │
     ▼
Azure Data Factory Pipeline
     │
     ▼
Bronze Notebook
     │
     ▼
Bronze Delta Table
     │
     ▼
Silver Notebook
     │
     ▼
Silver Delta Table
     │
     ▼
Gold Notebook
     │
     ▼
Gold Analytical Tables
     │
     ▼
Databricks SQL Dashboard
```

The complete architecture diagram is available in the **architecture/** folder.

---

#  Technology Stack

- Microsoft Azure
- Azure Data Lake Storage Gen2 (ADLS Gen2)
- Azure Data Factory (ADF)
- Azure Databricks
- Apache Spark (PySpark)
- Delta Lake
- Unity Catalog
- Azure Key Vault
- Databricks Secret Scope
- SQL
- Databricks SQL Dashboard
- Dashboard
- Git & GitHub

---

---

# 🔄 End-to-End Workflow

### Step 1 – Data Storage

- Uploaded the raw startup funding CSV dataset to Azure Data Lake Storage Gen2.

---

### Step 2 – Data Ingestion

- Azure Data Factory Copy Activity ingests the raw CSV into the Bronze layer.
- And orchestrate notebook using notebook activity
---

### Step 3 – Bronze Layer

- Raw data stored as Delta Lake tables.
- No business transformations applied.
- Preserved original dataset for traceability.

---

### Step 4 – Silver Layer

Performed data cleaning and transformation using PySpark:

- Removed duplicate records
- Handled missing values
- Standardized city names
- Standardized funding amounts
- Corrected inconsistent formats
- Applied validation checks

---

### Step 5 – Gold Layer

Created business-ready analytical tables:

- Top Funded Sectors
- City Funding Rank
- Sector YoY Snapshot
- Investor Deal Count
- Average Deal Size by Funding Stage

---

### Step 6 – Dashboard

Created an interactive Databricks SQL Dashboard using Gold Layer tables.

Visualizations include:

- Top Funded Sectors
- Top Cities by Startup Funding
- Top Investors by Number of Deals
- Average Deal Size by Funding Stage
- EdTech vs FinTech Funding Trend

---

# 📊 Business Insights

The dashboard answers the following business questions:

### 1. Which sectors attracted the highest investment?

FoodTech received the highest cumulative funding followed by Consumer Electronics and Retail.

---

### 2. Which cities attracted the most startup funding?

Pune ranked first followed by Kolkata and Delhi.

---

### 3. Who are the most active investors?

Info Edge completed the highest number of investments followed by Zodius Capital and Kalaari Capital.

---

### 4. What is the average funding amount by investment stage?

The "Other" funding stage had the highest average deal size followed by Series B.

---

### 5. How did EdTech and FinTech funding change over time?

Funding trends fluctuated across years, highlighting changing investor preferences between the two sectors.

---

#  Security Implementation

To secure sensitive credentials:

- Azure Key Vault stores the Storage Account Key.
- Databricks Secret Scope securely retrieves secrets.
- Storage credentials are never hardcoded.
- Azure IAM Role-Based Access Control (RBAC) is used to manage permissions.

---

#  Data Storage

The project uses Delta Lake for storing processed data.

Bronze Layer

- Raw Delta Tables

Silver Layer

- Cleaned Delta Tables

Gold Layer

- Business-ready Analytical Tables

---

#  Unity Catalog

The project uses **Unity Catalog** for managing catalogs, schemas, and tables.

As this project was developed using an **Azure for Students subscription**, Unity Catalog was used instead of advanced enterprise governance features that require higher-tier Azure Databricks configurations.

Catalog structure:

```
startup_bronze
startup_silver
startup_gold
```

Unity Catalog provides:

- Centralized metadata management
- Organized schemas
- Table discovery
- Secure data access

---

#  Azure Data Factory Pipeline

Pipeline activities include:

- Copy Activity
- Notebook Activity – Bronze
- Notebook Activity – Silver
- Notebook Activity – Gold

Pipeline execution:

```
CSV
 ↓
Copy Activity
 ↓
Bronze Notebook
 ↓
Silver Notebook
 ↓
Gold Notebook
 ↓
Dashboard
```

---

#  Dashboard

The Databricks SQL Dashboard provides interactive business analytics built directly on Gold Layer tables.

Charts included:

- Column Chart
- Horizontal Bar Chart
- Line Chart

---

#  Project Screenshots

The repository contains screenshots of:

- Azure Resources
- ADLS Gen2
- Azure Data Factory
- Databricks Workspace
- Unity Catalog
- Azure Key Vault
- Bronze Layer
- Silver Layer
- Gold Layer
- Dashboard
- Final Pipeline Execution

---

#  Features

- End-to-End Data Engineering Pipeline
- Medallion Architecture
- Delta Lake
- Azure Data Factory Orchestration
- PySpark Data Processing
- SQL Analytics
- Databricks Dashboard
- Azure Key Vault Integration
- Secret Scope Authentication
- Unity Catalog
- IAM Role-Based Security

---

#  Future Enhancements

- Incremental Data Loading
- Streaming Data using Auto Loader
- CI/CD using Azure DevOps
- Azure Monitor & Log Analytics
- Data Quality Monitoring
- Parameterized Pipelines
- Automated Testing

---

#  Project Highlights

✔ End-to-End Azure Data Engineering Pipeline

✔ Automated Workflow using Azure Data Factory

✔ Medallion Architecture (Bronze–Silver–Gold)

✔ Delta Lake Implementation

✔ Unity Catalog Integration

✔ Secure Credential Management using Azure Key Vault

✔ Interactive Databricks SQL Dashboard

✔ Business Analytics using SQL & PySpark

---

#  Author

**Gauri Dadhich**

Azure Data Engineering Project
