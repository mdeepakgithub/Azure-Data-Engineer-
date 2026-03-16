## Project : 1 Data Bricks (medallion architecture)

### 🧱 1️⃣ Bronze Layer (Raw Zone – Ingested via ADF)

➡️ Data comes directly from SQL Server, REST APIs, and Blob Storage without any transformation.

| Source System | Dataset Name | Description | File Format | Sample Fields |
|---|---|---|---|---|
| SQL Server | orders_raw | Raw order data from on-prem transactional system | CSV / Parquet | order_id, customer_id, product_id, order_date, order_status, quantity, price, discount, region, modified_date |
| SQL Server | customers_raw | Customer master data | CSV / JSON | customer_id, name, email, gender, country, join_date, phone, status |
| REST API | product_catalog_raw | Product details fetched via API | JSON | product_id, product_name, category, brand, base_price, stock_count, rating, last_updated |
| Blob Storage | transactions_raw | Payment transactions uploaded by payment gateway | CSV | transaction_id, order_id, payment_mode, amount, currency, payment_status, timestamp |

---

### 🧹 2️⃣ Silver Layer (Cleaned & Standardized – Transformed in Databricks)

➡️ Data is cleaned, validated, joined, and standardized here using PySpark notebooks triggered from ADF.

| Dataset Name | Description | Transformations Applied | Sample Fields |
|---|---|---|---|
| orders_clean | Cleansed order data | Removed nulls, standardized date/time, fixed prices, added total_amount | order_id, customer_id, product_id, order_date, region, total_amount, order_status |
| customers_clean | Valid and active customers only | Removed duplicates, filtered inactive customers, standardized names | customer_id, customer_name, email, country, join_date, is_active |
| products_clean | Curated product master | Removed discontinued products, added category hierarchy | product_id, product_name, category, brand, base_price, stock_count |
| transactions_clean | Verified successful transactions | Filtered only successful payments, added order linkage | transaction_id, order_id, payment_mode, amount, timestamp |

---

### 💎 3️⃣ Gold Layer (Business & Analytics Zone – Aggregated Models)

➡️ Final curated data for reporting and BI dashboards. Stored in Synapse Analytics and ADLS Gold zone.

| Dataset / Table Name | Type | Purpose / KPI | Sample Fields |
|---|---|---|---|
| fact_sales | Fact Table | Central fact combining orders + transactions | order_id, customer_id, product_id, order_date, revenue, discount, profit, region |
| dim_customers | Dimension Table | Customer dimension for analytics | customer_id, customer_name, country, join_date, loyalty_status |
| dim_products | Dimension Table | Product hierarchy details | product_id, product_name, category, brand, price_range |
| sales_summary_by_region | Aggregated View | Regional daily sales trends | region, date, total_sales, total_orders, avg_order_value |
| customer_lifetime_value | Derived Table | For customer retention analytics | customer_id, total_orders, total_spent, avg_purchase_value, CLV |
