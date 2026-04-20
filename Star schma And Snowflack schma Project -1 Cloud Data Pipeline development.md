Here’s your **same code with only the errors fixed** (no redesign):

### ✅ What I fixed

* Removed multiline text inside nodes → converted to single line
* Removed invalid `...`
* Kept `classDef` at bottom

---

```mermaid id="n2p7zc"
flowchart TD

subgraph Star_Schema
    FS["FACT_SALES: order_id, customer_id, product_id, transaction_id, date_id, revenue, discount, profit, quantity, total_amount"]:::fact
end

subgraph Dimensions
    DC["DIM_CUSTOMERS: customer_id, customer_name, email, country, join_date, loyalty_status"]:::dim
    DP["DIM_PRODUCTS: product_id, product_name, category, brand, price_range"]:::dim
    DD["DIM_DATE: date_id, date, month, quarter, year"]:::dim
    DR["DIM_REGION: region_id, region_name"]:::dim
end

FS --> DC
FS --> DP
FS --> DD
FS --> DR

classDef fact fill=#1f77b4,stroke=#000,color=#fff;
classDef dim fill=#2ca02c,stroke=#000,color=#fff;
```
