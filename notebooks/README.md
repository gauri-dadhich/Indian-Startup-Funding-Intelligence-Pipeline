# Databricks Notebooks

This folder contains the Databricks notebooks used to implement the Medallion Architecture for the Indian Startup Funding Analytics Pipeline.

## Notebooks

### 01_Bronze_Ingestion.ipynb
- Reads raw startup funding data from Azure Data Lake Storage Gen2.
- using copy activity data is copied from raw to bronze notebook
- Creates the Bronze Delta table without modifying the source data.


### 02_Silver_Transformation.ipynb
- Reads data from the Bronze Delta table.
- Performs data quality validation.
- Handles null values and duplicate records.
- Standardizes data types and text fields.
- Validates funding amounts and city names.
- Writes the cleaned dataset to the Silver Delta table.

### 03_Gold_Analytics.ipynb
- Reads data from the Silver Delta table.
- Generates business-ready analytical tables.
- Creates:
  - Top Funded Sectors
  - City Funding Rank
  - Investor Deal Count
  - Average Deal Size by Stage
  - Sector Year-over-Year Snapshot (SCD Type 2)

These notebooks are orchestrated sequentially using Azure Data Factory.
