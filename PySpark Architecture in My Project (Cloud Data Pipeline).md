# ⚡ PySpark Architecture in My Project (Cloud Data Pipeline)

## 📌 Overview
In my project, PySpark was used in Azure Databricks to process large-scale data using distributed computing.  
We implemented Medallion Architecture (Bronze → Silver → Gold) to transform raw data into business-ready datasets for analytics.

---

## 🏗️ Architecture Diagram (Project Flow)

```mermaid
flowchart LR

%% ================= SOURCE =================
SRC["Data Sources
SQL Server | REST APIs | Blob"]:::source

%% ================= INGESTION =================
ADF["Azure Data Factory"]:::tool

%% ================= STORAGE =================
ADLS["ADLS Gen2 (Bronze Layer)"]:::storage

%% ================= DRIVER =================
DRV["Driver Node
(PySpark Logic / DAG Creation)"]:::driver

%% ================= CLUSTER =================
EX1["Executor 1"]:::exec
EX2["Executor 2"]:::exec
EX3["Executor N"]:::exec

%% ================= PROCESSING =================
SL["Silver Layer
(Cleaned Data)"]:::silver

GL["Gold Layer
(Business Tables)"]:::gold

%% ================= CONSUMPTION =================
BI["Power BI / Synapse"]:::tool

%% ================= FLOW =================
SRC --> ADF --> ADLS
ADLS --> DRV
DRV --> EX1
DRV --> EX2
DRV --> EX3

EX1 --> SL
EX2 --> SL
EX3 --> SL

SL --> GL
GL --> BI

%% ================= STYLES =================
classDef source fill:#9467bd,color:#fff;
classDef tool fill:#17becf,color:#000;
classDef storage fill:#8c564b,color:#fff;
classDef driver fill:#1f77b4,color:#fff;
classDef exec fill:#2ca02c,color:#fff;
classDef silver fill:#7f7f7f,color:#fff;
classDef gold fill:#d4af37,color:#000;
