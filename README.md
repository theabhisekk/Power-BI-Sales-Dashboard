# Power BI Sales Dashboard

An interactive Power BI dashboard analyzing sales performance, revenue trends, and profitability for a retail superstore, built from a real-world transactional dataset (~10,000 orders, 2014–2017).

## 📊 Project Overview

This project demonstrates an end-to-end BI workflow: data cleaning, data modeling, DAX measure creation, and interactive dashboard design.

**Business questions answered:**
- What are the overall sales, profit, and order volume KPIs?
- How has revenue trended over time?
- Which product categories and regions drive the most revenue?
- How profitable is each sub-category?
- How is revenue distributed across customer segments?

## 🛠️ Tools & Skills Used

- **Power BI Desktop** — data modeling, DAX, report design
- **Power Query** — data cleaning (fixed inconsistent date formats, removed unneeded columns, corrected data types)
- **DAX** — custom measures for KPIs and time intelligence
- **Data modeling** — built a dedicated Date table with a proper relationship to enable time-based analysis

## 🧹 Data Cleaning

The raw dataset had inconsistent date formats (mixed `MM-DD-YYYY` and `M/D/YYYY` strings in the same column). This was resolved in Power Query using `Date.FromText()` with explicit US locale parsing to avoid misinterpretation (e.g. `4/15/2017` being misread as day/month).

## 📐 Key DAX Measures

```dax
Total Sales = SUM('Sample_ Superstore'[Sales])
Total Profit = SUM('Sample_ Superstore'[Profit])
Total Orders = DISTINCTCOUNT('Sample_ Superstore'[Order ID])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
Avg Order Value = DIVIDE([Total Sales], [Total Orders], 0)
Total Quantity Sold = SUM('Sample_ Superstore'[Quantity])
```

## 📈 Dashboard Pages

### 1. Executive Summary
KPI cards (Total Sales, Total Profit, Profit Margin %, Total Orders), a year-over-year sales trend line, and a sales-by-category breakdown — all filterable via Year, Region, and Category slicers.

![Executive Summary](Executive%20Summary.png)

### 2. Revenue Analysis
Deeper breakdown of sales by region and category, a full sub-category profitability table, and customer segment distribution.

![Revenue Analysis](Revenue%20Analysis.png)

## 📁 Files

- `Power-BI-Sales-Dashboard.pbix` — the full Power BI report file
- `Sample__Superstore.csv` — source dataset
- `screenshots/` — dashboard page exports

## 🚀 How to Use

1. Download `Power-BI-Sales-Dashboard.pbix`
2. Open in [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop) (free)
3. Use the slicers on the Executive Summary page to filter by Year, Region, or Category

## 📌 Dataset

Sample Superstore dataset — a widely used public retail transactions dataset for BI/analytics practice (originally sourced via Kaggle).
