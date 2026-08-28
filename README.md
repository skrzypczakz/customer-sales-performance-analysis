# Customer & Sales Performance Analysis


## Project Overview

The project presents an analysis of sales performance based on customer, order and product data. I used Power Query for data cleaning and transformation, and data quality issues were identified and handled in a separate analytical layer. I built a relational data model and created DAX measures together with an interactive Power BI dashboard. The analysis focused on monthly sales trends, category and product performance, as well as country results and customer segments.


## Data

The analysis is based on four CSV files:
- `customers.csv` – customer information, including country, segment and signup date,
- `orders.csv` – order-level data, including customer, order date, status and sales channel,
- `order_items.csv` – individual order lines with product, quantity and discount information,
- `products.csv` – product details, including category, unit cost and unit price.
  
The tables are connected through customer, order and product IDs to support relational analysis.


## Data Quality & Methodology

Raw CSV → Data Quality Audit → Power Query Cleaning → Quality Flags → Analytical Layer → Data Model → DAX → Dashboard

Raw data was preserved. Unambiguous issues were corrected, while uncertain values were flagged rather than guessed and excluded only from analyses they could distort.


## Data Model

Tables are connected through the following relationships:
- customers → orders by customer_id (1:*)
- orders → order_items by order_id (1:*)
- order_items → products by product_id (*:1)

Additionally, a Date table was added and connected to orders by date (1:*), which helped analyze the data by month, among other time-based views. All relationships use single-direction filtering.


## Key Measures

The project uses measures such as:
- `Total Sales` – calculates total sales including discounts (`SUMX`, `RELATED`)
- `Average Order Value` – calculates the average value of an order (`DIVIDE`)
- `Number of Orders` – calculates the number of unique orders (`DISTINCTCOUNT`)
- `Sales Change` – calculates the difference between October and November sales (`VAR`, `CALCULATE`)
- `Completed Sales` – calculates sales only for completed orders (`CALCULATE`)


## Dashboard

The main dashboard presents monthly sales trends, key KPIs, country performance and the products that contributed most to sales growth from October to November.

The Data Quality & Methodology page shows identified data quality issues and the steps taken to resolve or flag them.


## Key Insights

- Sales remained relatively high during the first half of the year, declined towards October, and recovered strongly in November.
- The Kitchen category recorded the highest sales increase from October to November, at approximately 15.7K.
- Within Kitchen, Electric Kettle and Toaster contributed the most to this growth, increasing by approximately 5.1K and 4.9K.
- Poland and Germany had different customer segment structures: Germany had a higher Corporate share, while Poland had a higher Small Business share. Consumer was the largest segment in both countries.
- Poland generated higher total sales mainly due to a higher number of orders. Germany had a higher Average Order Value, but not enough to offset Poland's higher order volume.

## 

<img width="1452" height="813" alt="dashboard-overview" src="https://github.com/user-attachments/assets/ed847f4b-1738-4aad-94a1-63ae419f0e3f" />

##
<img width="1452" height="817" alt="data-quality-methodology" src="https://github.com/user-attachments/assets/165a0bf3-a906-4e77-98e6-0db86574cac7" />



