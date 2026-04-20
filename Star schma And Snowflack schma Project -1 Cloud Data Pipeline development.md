# Project 1 – Schema Diagrams

This document shows the **Star Schema** and **Snowflake Schema** for the Gold Layer of the Cloud Data Pipeline project.  
Both diagrams are rendered using Mermaid TD syntax and include color coding:

- **Fact tables** → Blue  
- **Dimension tables** → Green  

---

## 🌟 Star Schema

```mermaid
flowchart TD

subgraph Star_Schema
    FS["FACT_SALES
    order_id, customer_id, product_id, transaction_id, date_id
    revenue, discount, profit, quantity, total_amount"]:::fact
end

subgraph Dimensions
    DC["DIM_CUSTOMERS
    customer_id, customer_name, email, country, join_date, loyalty_status"]:::dim
    DP["DIM_PRODUCTS
    product_id, product_name, category, brand, price_range"]:::dim
    DD["DIM_DATE
    date_id, date, month, quarter, year"]:::dim
    DR["DIM_REGION
    region_id, region_name"]:::dim
end

FS --> DC
FS --> DP
FS --> DD
FS --> DR


