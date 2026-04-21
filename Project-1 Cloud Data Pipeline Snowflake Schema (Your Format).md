## ❄️ Snowflake Schema – Cloud Data Pipeline

```mermaid
flowchart LR

%% ================= FACT TABLE =================
FS["FACT_SALES
order_id, customer_id, product_id, date_id, store_id
revenue, discount, profit, quantity"]:::fact

%% ================= DIMENSIONS =================
DC["DIM_CUSTOMER
customer_id, customer_name, email"]:::dim
DG["DIM_GEOGRAPHY
geo_id, city, state, country"]:::dim
DL["DIM_LOYALTY
loyalty_id, loyalty_status"]:::dim

DP["DIM_PRODUCT
product_id, product_name, price"]:::dim
DCat["DIM_CATEGORY
category_id, category_name"]:::dim
DB["DIM_BRAND
brand_id, brand_name"]:::dim

DD["DIM_DATE
date_id, full_date"]:::dim
DM["DIM_MONTH
month_id, month"]:::dim
DQ["DIM_QUARTER
quarter_id, quarter"]:::dim
DY["DIM_YEAR
year_id, year"]:::dim

DS["DIM_STORE
store_id, store_name"]:::dim
DR["DIM_REGION
region_id, region_name"]:::dim

%% ================= RELATIONSHIPS =================
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

FS --- DS
DS --- DR

%% ================= STYLES =================
classDef fact fill:#1f77b4,stroke:#000,color:#fff;
classDef dim fill:#2ca02c,stroke:#000,color:#fff;
