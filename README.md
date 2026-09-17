# E-Commerce Revenue Intelligence Pipeline & Dashboard

## 📌 Project Overview
An end-to-end data engineering and business intelligence project designed to analyze multi-year e-commerce sales. This project translates raw transaction logs into an executive Power BI dashboard, focusing on accurate target tracking, unit economics (AOV), and granular profitability analysis. 

## 🏗️ Architecture & Tech Stack
**Data Extraction & Transformation (ETL):** Python (Pandas, NumPy)
**Storage & Database:** SQLite
**Business Intelligence & Visualization:** Power BI, DAX
**Data Modeling:** Star Schema with a custom Composite Key

## ⚙️ Data Pipeline (Python/Pandas)
* Merged disjointed order history and transaction details using "Order ID".
* Standardized inconsistent date formats and handled null values across financial columns.
* Extracted temporal features ("Order_Month", "Order_Year", "Month_No") upstream to prevent circular dependency sorting errors in Power BI.
* Engineered a 'Category_Month_Year' composite key to bridge daily sales facts with monthly target goals.
* Exported the transformed relational tables directly into an `ecommerce.db` SQLite database.

## 📊 Business Intelligence (Power BI)
* **Data Modeling:** Established a precise Many-to-One relationship between "sales" and "target" tables using the engineered composite key, resolving target over-counting (fan-out) errors.
* **DAX Engineering:** Authored dynamic measures for "Average Order Value (AOV)", "Target Achieved %", and "Profit Margin %" using "DIVIDE()" to prevent "average-of-averages" row-level aggregation errors.
* **Actionable Insights:** 
  * Utilized Top N filtering to identify the top 10 revenue-driving customers.
  * Applied conditional formatting to instantly flag loss-leading sub-categories and underperforming regions.
