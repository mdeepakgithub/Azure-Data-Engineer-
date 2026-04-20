# Project 1 – Schema Diagrams

This document shows the **Star Schema** and **Snowflake Schema** for the Gold Layer of the Cloud Data Pipeline project.  
Both diagrams are rendered using Mermaid TD syntax and include color coding:

- **Fact tables** → Blue  
- **Dimension tables** → Green  

---

## 🌟 Star Schema

```mermaid
flowchart LR

FS["FACT_SALES
order_id, customer_id, product_id, transaction_id, date_id
revenue, discount, profit, quantity, total_amount"]:::fact

DC["DIM_CUSTOMERS
customer_id, customer_name, email, country, join_date, loyalty_status"]:::dim
DP["DIM_PRODUCTS
product_id, product_name, category, brand, price_range"]:::dim
DD["DIM_DATE
date_id, date, month, quarter, year"]:::dim
DR["DIM_REGION
region_id, region_name"]:::dim

FS --- DC
FS --- DP
FS --- DD
FS --- DR




flowchart LR

FS["FACT_SALES
order_id, customer_id, product_id, transaction_id, date_id
revenue, discount, profit, quantity, total_amount"]:::fact

DC["DIM_CUSTOMERS
customer_id, customer_name, email, join_date"]:::dim
DG["DIM_GEOGRAPHY
country_id, country_name, region_id"]:::dim
DL["DIM_LOYALTY
loyalty_id, loyalty_status"]:::dim

DP["DIM_PRODUCTS
product_id, product_name, base_price"]:::dim
DCat["DIM_CATEGORY
category_id, category_name"]:::dim
DB["DIM_BRAND
brand_id, brand_name"]:::dim

DD["DIM_DATE
date_id, date, day, month, quarter, year"]:::dim
DM["DIM_MONTH
month_id, month_name"]:::dim
DQ["DIM_QUARTER
quarter_id, quarter_name"]:::dim
DY["DIM_YEAR
year_id, year"]:::dim

FS --- DC
DC --- DG
DC --- DL
FS --- DP
DP --- DCat
DP --- DB
FS --- DD
DD --- DM
DD --- DQ
DD --- DY




