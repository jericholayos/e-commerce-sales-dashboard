# E-Commerce Sales Dashboard

[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-yellow?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)

An end-to-end data analytics project built with **PostgreSQL** and **Power BI**, covering data ingestion, star schema modeling, SQL analysis, and an interactive BI dashboard.

---

## Dashboard Preview
<img width="1340" height="754" alt="Dashboard Preview" src="https://github.com/user-attachments/assets/ffd2fc1e-3a19-443c-9c6f-8b91b6247a9c" />

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| PostgreSQL 15 | Database, star schema, SQL analysis |
| Power BI Desktop | Dashboard, DAX measures, visualizations |
| Power Query | Data transformation and cleaning |
| DAX | KPI measures, time intelligence |

---

## Dataset

- **Source:** E-Commerce Sales Dataset
- **Rows:** 9,799 records
- **Years:** 2015 – 2018
- **Fields:** Order ID, Order Date, Ship Date, Ship Mode, Customer, Segment, Region, Category, Sub-Category, Product, Sales

---

## Data Model

Star schema with one fact table and four dimension tables:

```
dim_date ──────┐
dim_customer ──┤
               ├──▶ fact_sales
dim_product ───┤
dim_geography ─┘
```

| Table | Description |
|-------|-------------|
| `fact_sales` | 9,799 rows, one per order line item |
| `dim_date` | Continuous date spine from 2015–2018 |
| `dim_customer` | Unique customers with segment |
| `dim_product` | Products with category and sub-category |
| `dim_geography` | City, state, region, country |

---

## SQL Analysis

**Aggregations**
- Total revenue, orders, and unique customers by year
- Revenue by category, sub-category, region, and segment

**Window Functions**
- Month-over-month growth using `LAG()`
- Running revenue total using `SUM() OVER()`
- Category share using `PARTITION BY`

**Advanced**
- Customer RFM analysis (Recency, Frequency, Monetary)
- Shipping mode performance with average ship days
- Top 10 products by revenue

---

## Dashboard Features

- **KPI Cards:** Total Revenue, Total Orders, Avg Order Value, Unique Customers with YoY comparison
- **Monthly Revenue Trend:** line chart with area fill
- **Revenue by Category / Sub-Category / Segment / Region:** bar and column charts
- **Top Products Table:** ranked by total revenue
- **Orders by Ship Mode:** column chart
- **Slicers:** Region, Segment, Month, Year with reset button

---

## Key Findings

| Area | Finding |
|------|---------|
| **Category** | Technology is the top revenue category at $827K |
| **Region** | West generates the highest revenue across all years |
| **Segment** | Consumer accounts for the largest share at $1.15M |
| **Shipping** | Standard Class is used in over half of all orders |
| **Seasonality** | Revenue consistently peaks in Q4 (Nov–Dec) and dips in Jan–Feb |
| **Top Product** | Canon imageCLASS 2200 Advanced Copier leads at $35,700 in 2018 |
| **Growth** | 2018 had the highest revenue at $722K, a 20.3% YoY increase |
