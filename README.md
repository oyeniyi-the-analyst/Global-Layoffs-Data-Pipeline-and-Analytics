

#Layoffs Data Analytics Project

<div align="center">
  <img src="https://github.com/oyeniyi-the-analyst/Global-Layoffs-Data-Pipeline-and-Analysis/blob/main/reports/executive_Overview.png?raw=true"
       alt="Executive Overview Dashboard"
       width="80%" />
</div>

# Global Layoffs Data Pipeline and Analysis (SQL + Power BI)

## Overview
This project designs and implements a structured SQL data pipeline to transform raw layoffs data into a clean, validated, and analysis-ready dataset.

The focus is on data quality, controlled transformation, and building a reliable foundation for business analysis.

---

## Problem Statement
Raw layoffs data contains multiple data quality issues, including:
- Missing values
- Duplicate records
- Inconsistent text formatting
- Mixed and incorrect data types

These issues can lead to misleading insights if not handled properly.

The goal of this project is to design a robust data pipeline that ensures data integrity and supports accurate reporting.

---

## Data Pipeline Architecture

The pipeline is built using a multi-layer approach:

### 🔹 Raw Layer
- Imported CSV data into MySQL
- Preserved original dataset without modification

### 🔹 Staging Layer
- Trimmed whitespace and standardised text fields
- Converted invalid values to NULL
- Normalised inconsistent entries (e.g. N/A, NULL strings)

### 🔹 Deduplication Layer
- Used `ROW_NUMBER()` window function
- Partitioned data across all relevant columns
- Removed duplicate records while preserving one valid instance

### 🔹 Clean Layer
- Converted data types safely (date, numeric fields)
- Applied regex validation before casting
- Retained NULL values to preserve data integrity

### 🔹 BI-Ready Export Layer
- Replaced NULLs with controlled defaults where necessary
- Added data status indicators (Reported vs Missing)
- Created derived fields such as Year and Month
- Prepared dataset for Power BI consumption

---

## Key Techniques Used
- SQL window functions for deduplication
- Regex-based validation for safe type conversion
- Multi-stage ETL pipeline design
- Data quality tracking using status flags
- Controlled NULL handling strategy
- Data transformation and standardisation

---

## Dashboard (Power BI)

The Power BI dashboard focuses on clear and actionable insights:

- KPI Cards:
  - Total Layoffs
  - Total Companies
  - Total Countries

- Primary Visual:
  - Layoffs Trend Over Time (Line Chart)

- Supporting Analysis:
  - Top companies by layoffs
  - Industry-level impact
  - Country-level distribution
  - Funding vs layoffs comparison

---

## Key Insights
- Layoffs occur in waves rather than evenly over time
- A small number of companies account for a large share of total layoffs
- Industry impact is uneven, with some sectors showing higher volatility
- Layoffs are concentrated in specific geographic regions
- Access to funding does not necessarily prevent workforce reductions

---


### 3. Generate Clean Dataset
- Final table: `layoffs_export_tb`
- Exported file: `layoffs_cleaned_dataset.csv`

### 4. Open Power BI Dashboard
- Load cleaned dataset into Power BI
- Explore trends and insights

---

## KPIs Defined
- Total Layoffs
- Total Companies
- Total Countries
- Monthly and yearly trends
- Industry and company level aggregations

---

## Design Decisions
- Preserved NULL values in the clean layer to maintain data integrity  
- Introduced status flags to track missing data  
- Applied safe casting to prevent data corruption  
- Separated data cleaning from reporting logic  
- Structured pipeline for scalability and reuse  

---
## Project Structure


layoffs-data-pipeline/
│
├── data/
│ ├── layoffs.csv
│ └── layoffs_cleaned_dataset.csv
│
├── sql/
│ └── layoffs_pipeline.sql (layer by layer)
│
├── powerbi/
│ └── layoffs_dashboard.pbix
│
├── images/
│ └── dashboard.png
│
└── README.md
## Data Limitations
- Some records contain missing layoffs data
- Data completeness depends on external reporting sources
- NULL values are handled explicitly in the reporting layer

---

## Conclusion
This project demonstrates how to build a structured SQL data pipeline that prioritises data quality and supports reliable business insights.

It highlights the importance of preparing clean and trustworthy data before performing analysis or building dashboards.

---
