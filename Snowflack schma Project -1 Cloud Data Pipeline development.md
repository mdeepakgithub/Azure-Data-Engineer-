


# ❄️ Snowflake Schema

```mermaid
flowchart LR

%% ================= FACT TABLE =================
FS["FACT_SALES
order_id, customer_id, product_id, transaction_id, date_id
revenue, discount, profit, quantity, total_amount"]:::fact

%% ================= DIMENSIONS =================
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










