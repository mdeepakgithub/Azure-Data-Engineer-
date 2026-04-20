flowchart TD

%% ================= STAR SCHEMA =================
subgraph Star_Schema
    FS["FACT_SALES  
    - order_id, customer_id, product_id, transaction_id, date_id  
    - revenue, discount, profit, quantity, total_amount"]

    DC["DIM_CUSTOMERS  
    - customer_id, customer_name, email, country, join_date, loyalty_status"]

    DP["DIM_PRODUCTS  
    - product_id, product_name, category, brand, price_range"]

    DD["DIM_DATE  
    - date_id, date, month, quarter, year"]

    DR["DIM_REGION  
    - region_id, region_name"]
end

%% ================= RELATIONSHIPS =================
FS --> DC
FS --> DP
FS --> DD
FS --> DR




    DCat["DIM_CATEGORY  
    - category_id, category_name"]

    DB["DIM_BRAND  
    - brand_id, brand_name"]

    DD["DIM_DATE  
    - date_id, date, day, month, quarter, year"]

    DM["DIM_MONTH  
    - month_id, month_name"]

    DQ["DIM_QUARTER  
    - quarter_id, quarter_name"]

    DY["DIM_YEAR  
    - year_id, year"]
end

%% ================= RELATIONSHIPS =================
FS --> DC
DC --> DG
DC --> DL
FS --> DP
DP --> DCat
DP --> DB
FS --> DD
DD --> DM
DD --> DQ
DD --> DY





