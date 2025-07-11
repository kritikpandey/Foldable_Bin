# 📊 SQL Queries – Foldable Bin Sales Dashboard

## 📋 Dataset Overview

### 🟢 Sample Data 1:

| Types         | Month | Volumes | Revenues  | Prices | Comments        |
|---------------|--------|---------|-----------|--------|------------------|
| Target Price  | Jan    | 500     | 32032.89  | 64.07  | Market-defined   |
| TP Rebate 1   | Jan    | 45      | 2594.66   | 60.86  | 5%               |
| TP Rebate 2   | Jan    | 35      | 1905.96   | 64.07  | 0%               |
| Freebies      | Jan    | 100     | 0.00      | 0.00   | null             |
| Target Price  | Feb    | 600     | 38439.47  | 64.07  | Market-defined   |
| TP Rebate 1   | Feb    | 95      | 5781.94   | 60.86  | 5%               |
| TP Rebate 2   | Feb    | 45      | 2681.15   | 64.07  | 0%               |
| Freebies      | Feb    | 100     | 0.00      | 0.00   | null             |

### 🟢 Sample Data 2:

| Types        | Total_Revenues       |
|--------------|----------------------|
| TP Rebate 2  | 48,433.70            |
| Freebies     | 0.00                 |
| Target Price | 1,793,841.77         |
| TP Rebate 1  | 142,767.24           |

Below are the SQL queries used to generate visualizations in Databricks for the Foldable Bin project.
---

## 1️⃣ Monthly Revenue by Month (Bar Chart)

**📈 Widget:** Sum of Revenues per Month  
**📊 Chart Type:** Bar Chart  
**📝 Description:** Shows total revenue per month from January to July.
```sql
SELECT  data1.Types,data1.month, data1.Volumes, data1.Revenues,data2.Prices,data2.Comments
FROM workspace.default.m_ba_data_11 AS data1
Join workspace.default.mbadata_22 AS data2 
on data2.Types = data1.Types;
```
## 2️⃣ Revenue Breakdown by Type (Donut Chart)

**📈 Widget:** Revenue Share by Type  
**📊 Chart Type:** Donut Chart  
**📝 Description:** Percentage-wise revenue contribution of each type (Freebies, Target Price, TP Rebate 1, TP Rebate 2).
```sql
SELECT data1.Types, SUM(data1.Revenues) AS Total_Revenues
FROM workspace.default.m_ba_data_11 AS data1
JOIN workspace.default.mbadata_22 AS data2
ON data2.Types = data1.Types
GROUP BY data1.Types;
```
## 3️⃣ Average Revenue by Month (Stacked Area Chart)

**📈 Widget:** Average Revenue Trend Over Months  
**📊 Chart Type:** Stacked Area Chart  
**📝 Description:** Displays average revenue by type over time.
```sql
SELECT  data1.Types,data1.month, data1.Volumes, data1.Revenues,data2.Prices,data2.Comments
FROM workspace.default.m_ba_data_11 AS data1
Join workspace.default.mbadata_22 AS data2 
on data2.Types = data1.Types;
```
## 4️⃣ Total Revenue by Type (Bar Chart)
**📈 Widget:** Total Revenue by Type  
**📊 Chart Type:** Vertical Bar Chart  
**📝 Description:** Compares total revenue across each sales type.  
```sql
SELECT data1.Types, SUM(data1.Revenues) AS Total_Revenues
FROM workspace.default.m_ba_data_11 AS data1
JOIN workspace.default.mbadata_22 AS data2
ON data2.Types = data1.Types
GROUP BY data1.Types;
```
