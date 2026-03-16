## Project Explanation 1 – Cloud Data Pipeline Development (Final Version)

In my project titled “Cloud Data Pipeline Development”, I designed and implemented a complete end-to-end data engineering solution on Microsoft Azure to process large volumes of sales, customer, and product data. 

The objective was to build a scalable and automated data pipeline that could handle both batch and real-time (streaming) data efficiently. 

We used Azure Data Factory (ADF) as the orchestration tool to ingest data from multiple sources such as on-prem SQL Server, REST APIs, and Azure Blob Storage.

In ADF, I developed several pipelines using core components like Linked Services (to connect source (SQL) and destination (adls gen2) systems), Datasets (orders, customer, transaction, production) and Activities such as Copy Activity, For Each, and Databricks Notebook Activity for data movement and transformation orchestration.

The ingested raw data was stored in Azure Data Lake Storage Gen2 (ADLS) following the Medallion Architecture, consisting of Bronze, Silver, and Gold layers.

The Bronze layer held raw, unprocessed data directly from sources, the Silver layer stored cleaned and standardized data, and the Gold layer contained aggregated, business-ready data for analytics.

For the transformation stage, I used Azure Databricks with PySpark to perform data cleaning, validation, enrichment, and aggregation.

We implemented incremental load mechanisms using watermark columns and Delta Lake MERGE operations, allowing only new or updated records to be processed, which optimized both cost and performance.

The pipeline supported both batch ingestion (we should add ADF triggers schedule triggers) and streaming data through Azure Event Hubs and Databricks Structured Streaming, ensuring near real-time updates.

The transformed and curated data was stored in Delta Lake format within the ADLS Silver and Gold layers for ACID compliance and versioning.

Finally, the curated data from the Gold layer was loaded into Azure Synapse Analytics, where it served as a centralized data warehouse to build fact and dimension tables for analytical queries and reporting.

Power BI was connected to Synapse to create rich, interactive dashboards and visual reports showing key metrics like total revenue, profit margin, customer lifetime value, and regional sales performance.

To ensure governance and reliability, I implemented RBAC security, Managed Identity authentication, and Azure Monitor alerts for pipeline monitoring.

Additionally, Azure DevOps CI/CD pipelines were used to automate deployment of ADF, Databricks, and Synapse artifacts across development, QA, and production environments.

Overall, this solution provided a scalable, secure, and automated data ecosystem supporting both batch and streaming data, enabling incremental processing, improving data accuracy, and delivering real-time insights to business users through Power BI dashboards.
