# E-Commerce Sales & Profitability Analysis Capstone

## Overview
This capstone project focuses on analyzing global e-commerce order transactions to evaluate regional revenue trends, product category profitability, and seasonal sales performance. The goal was to build a clean end-to-end pipeline—moving from initial data cleaning and exploratory analysis in Python, to structured relational data modeling in SQL, and concluding with an interactive Power BI reporting dashboard.

---

## Tech Stack
* **Python (Pandas, Jupyter Notebook):** Data cleaning, missing value handling, and exploratory data analysis.
* **SQL Server (SSMS):** Database setup, aggregation queries, and window functions to segment performance.
* **Power BI:** Interactive dashboard design, KPI card setup, and trend modeling.
* **Git & GitHub:** Version control and repository management.

---

## Project Structure
```text
ECommerce_Analytics_Project/
├── Data/
│   ├── ecommerce_raw_data.csv
│   └── ecommerce_clean_export.csv
├── Python/
│   └── ecommerce_eda.ipynb
├── SQL/
│   └── ecommerce_analysis.sql
└── Powerbi/
    └── ecommerce_sales_dashboard.pbix

Work Breakdown & Key Findings
1. Data Cleaning & Exploration (Python)
Ingested raw e-commerce transaction records using Pandas.

Cleaned up date fields, checked for duplicate records, and handled missing values across order categories.

Exported the processed data as a clean CSV ready for SQL database ingestion.

2. SQL Analysis & Business Queries (SSMS)
Financial Summary: Calculated total revenue, total profit, order volume, and net profit margins across the dataset.

Regional Insights: Identified high-performing sales regions alongside lower-margin territories that may require strategy adjustments.

Category Breakdown: Grouped revenue by product categories to pinpoint primary growth drivers.

Rankings: Applied ROW_NUMBER() OVER() window functions to isolate top-tier orders within individual regions.

3. Reporting & Visualization (Power BI)
Built an executive dashboard with top-level KPI cards for quick metric assessment (Revenue, Net Profit, Total Orders, Profit Margin %).

Designed regional comparison charts and category distribution visuals for straightforward stakeholders analysis.

Plotted monthly order timelines to track seasonal revenue patterns over time.
