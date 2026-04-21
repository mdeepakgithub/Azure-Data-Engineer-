## 🌟 Star Schema – Cloud Data Pipeline

```mermaid
flowchart LR

%% ================= FACT TABLE =================
FS["FACT_SALES
order_id, customer_id, product_id, store_id, date_id
quantity, sales_amount, discount, profit"]:::fact

%% ================= DIMENSIONS =================
DC["DIM_CUSTOMER
customer_id, customer_name, email, phone, city, state, country"]:::dim

DP["DIM_PRODUCT
product_id, product_name, category, sub_category, price"]:::dim

DS["DIM_STORE
store_id, store_name, location, region"]:::dim

DD["DIM_DATE
date_id, date, day, month, quarter, year"]:::dim

%% ================= RELATIONSHIPS =================
FS --- DC
FS --- DP
FS --- DS
FS --- DD

%% ================= STYLES =================
classDef fact fill:#1f77b4,stroke:#000,color:#fff;
classDef dim fill:#2ca02c,stroke:#000,color:#fff;
