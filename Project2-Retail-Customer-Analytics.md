## Project 2 :- :– Retail Customer Analytics Platform

In this project, I designed and implemented a complete end-to-end Microsoft Fabric platform to integrate both batch and real-time data into a unified Lakehouse architecture. 

The objective was to consolidate multiple datasets such as Sales Transactions, POS Data, E-commerce Orders, Web Clickstream Events, Customer Master, Product Master, Inventory Levels, Promotions, Store Information, and Loyalty Program Data into One Lake to support real-time analytics and Power BI reporting.

I built the ingestion layer using Fabric Data Pipelines, Dataflows Gen2, and Event streams.

Batch datasets—such as Sales, Inventory, Customer Master, and Product Master—were ingested using Data Pipelines from SQL Server, Dynamics 365, and REST APIs, while slowly changing dimension tables were handled using Dataflows Gen2.

For real-time streaming, I integrated Azure Event Hub with Fabric Event streams to capture live events like add-to-cart actions, product views, checkout attempts, order confirmations, and website interactions.

All this data, both batch and streaming, landed in the Bronze layer of the Fabric Lakehouse.

I developed PySpark notebooks in Fabric Data Engineering to perform cleansing, deduplication, schema alignment, and incremental processing using Delta Lake features such as MERGE, Optimize, and Auto Compaction, building a clean Silver layer.

From the Silver layer, I created business-ready Gold datasets including Daily Sales Summary, Customer 360, Store Daily Performance, Online Conversion Funnel, Inventory Health Dashboard Data, and Marketing Campaign Response.

For low-latency streaming analytics, I used Fabric Real-Time Analytics (SQL Database) to store and query high-velocity clickstream and order events, enabling live dashboards for website activity, product performance, and cart abandonment trends.

The curated Gold tables were exposed through both Fabric Warehouse and the Lakehouse SQL endpoint, and connected to Power BI using Direct Lake, providing near real-time reporting without refresh delays.

Governance and security were implemented using Fabric Domains, One Lake Shortcuts, Workspace Access Controls, Sensitivity Labels, and Row-Level Security.

I also enabled Git integration in Fabric for CI/CD, versioning notebooks, pipelines, and semantic models.

Overall, this Microsoft Fabric solution delivered a scalable, automated, real-time analytics platform that unified all datasets, improved data freshness, and gave business teams instant insights for sales, marketing, supply chain, and digital operations.
