# E-Commerce Sales Dashboard
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-18-blue?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-yellow?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)

An end-to-end data analytics project built with **PostgreSQL** and **Power BI** — covering data ingestion, star schema modeling, SQL analysis, and an interactive business intelligence dashboard.

---

## Dashboard Preview
<img width="1340" height="754" alt="image" src="https://github.com/user-attachments/assets/ffd2fc1e-3a19-443c-9c6f-8b91b6247a9c" />

---

## Model View
<img width="1049" height="772" alt="image" src="https://github.com/user-attachments/assets/5afa20bc-8495-4021-941a-997619192129" />

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
- **Columns:** 18 fields
- **Years:** 2015 – 2018
- **Fields:** Order ID, Order Date, Ship Date, Ship Mode, Customer, Segment, Region, Category, Sub-Category, Product, Sales

---

## Project Structure
```
ecommerce-sales-dashboard/
│
├── sql/
│   ├── 01_star_schema_creation.sql     # Dimension and fact table creation
│   └── 02_all_queries.sql              # KPI queries, window functions, RFM
│
├── screenshots/
│   └── dashboard.png                   # Final dashboard screenshot
│
├── ecommerce.csv                        # Source dataset
├── sales_dashboard.pbix                 # Power BI file
└── README.md
```

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

- **fact_sales** — 9,799 rows, one per order line item
- **dim_date** — continuous date spine from 2015–2018, no gaps
- **dim_customer** — unique customers with segment
- **dim_product** — unique products with category and sub-category
- **dim_geography** — city, state, region, country

---

## SQL Analysis
Queries written across three areas:

**Aggregations**
- Total revenue, orders, unique customers by year
- Revenue by category, sub-category, region, segment

**Window Functions**
- Month-over-month growth using `LAG()`
- Revenue running total using `SUM() OVER()`
- Category share using `PARTITION BY`

**Advanced**
- Customer RFM analysis (Recency, Frequency, Monetary)
- Shipping mode performance with average ship days
- Top 10 products by revenue

---

## Dashboard Features
- **KPI Cards** — Total Revenue, Total Orders, Avg Order Value, Unique Customers with YoY comparison
- **Monthly Revenue Trend** — line chart with area fill
- **Revenue by Category** — horizontal bar chart
- **Revenue by Sub-Category** — Top N filtered bar chart
- **Revenue by Segment** — horizontal bar chart
- **Revenue by Region** — column chart
- **Top Products Table** — ranked by total revenue
- **Orders by Ship Mode** — column chart
- **Slicers** — Region, Segment, Month, Year with reset button

---

## Key Findings
- **Technology** is the top revenue category, followed closely by Furniture and Office Supplies
- **West region** generates the highest revenue across all years
- **Consumer segment** accounts for the largest share of orders
- **Standard Class** is the dominant shipping mode, used in over half of all orders
- Revenue shows a consistent upward trend toward Q4 each year

---

## Analysis & Insights

**Regional Performance**
West has the highest revenue in all 4 years. In 2016, 2017, and 2018, the West region's revenue is 2x higher compared to South. The exception is 2015, where the gap was only $40K with West at $146K total revenue. This shows that West is consistently dominant across all 4 years. We should prioritize the West more in terms of revenue since it's the highest driver, and we should investigate why South is underperforming.

**Seasonality**
There is a seasonality pattern. After September, sales drops but after October sales always go up. This shows that it always peaks in November and December, but always drops in January and February. The business should focus on promotions or sale discounts in those months where sales are its lowest, like January and February.

**Segment Performance**
Consumer is the highest driver for revenue in all years at 1.15M, this means that consumer is the top segment and should be prioritized. The lowest driver for revenue is home office. We should try to figure out what should be the best way to maximize or increase our revenue in Home Office.

**Category & Sub-Category Performance**
Technology is the highest driver for revenues in categories at 827K. In every year, phones and chairs subcategory is always the top 2 highest revenue even though in every year it's not in the top products. This shows that phones and chairs are volume driven revenue and the top products are high value single transaction revenue. This suggests that we should focus on figuring out what's the best way on increasing revenue in phones and chairs, like adding a bundled package.

**Orders & Revenue**
2018 has the highest total revenue at 722K, a 20.3% increase vs past year. 2018 also has the highest total orders, it has 1,661 total orders, 28.3% higher than last year but order value dropped at 6.2% ($434.71). Highest order value was at $506.41 on 2015 but had a 11% decrease in the following year but a 7.6% increase in total orders. This could mean that revenue growth is positive but the declining order value is worth monitoring.

**Top Products**
Canon imageCLASS 2200 Advanced Copier has the highest total revenue among all products at $35,700 in 2018, which is almost 3x higher than the second product at $11,826, even though it shows little volume. We should ensure that this product or whichever product that shows high revenue-little volume, is well stocked and maintained, and also look to prioritize similarly high value single transaction products.

**Unique Customers**
Unique customers also increases if total orders increase. The highest unique customers were in 2018 at 690, an 8.7% vs last year. The lowest unique customers were on 2016 at 567, even though the total order increases at 7.6% vs last year, the unique customer decreases at 3.7%. This suggests that in 2016, the same customers were buying more instead of new customers coming in. The business should look into why it failed to attract new customers that year to prevent it from happening again.

**Shipping**
Standard class is the most used ship mode compared to second class, first class, and same day. People may prefer to wait few more days in Standard class, compared to the others, and they may prefer the cheaper one which is Standard Class. The business could either cut or keep the other delivery options, but I suggest to don't cut it because there may be people who are willing to pay more for the other delivery options.
