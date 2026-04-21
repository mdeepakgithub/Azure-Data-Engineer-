# ⚡ Databricks Process – Cloud Data Pipeline

## 📌 Overview
This architecture uses Azure Databricks with Medallion Architecture (Bronze, Silver, Gold) to process data from multiple sources and deliver analytics-ready datasets.

---

## 🏗️ Architecture Diagram

```mermaid
flowchart LR

%% ================= DATA SOURCES =================
SRC["Data Sources
SQL Server | REST APIs | Blob Storage"]:::source

%% ================= INGESTION =================
ADF["Azure Data Factory
(Ingestion & Orchestration)"]:::tool

%% ================= STORAGE =================
ADLS["ADLS Gen2 (Raw Storage)"]:::storage

%% ================= DATABRICKS =================
DBX["Azure Databricks"]:::dbx
CL["Cluster (Driver + Workers)
Auto Scaling"]:::compute
NB["PySpark Notebooks"]:::compute

%% ================= LAYERS =================
BR["Bronze Layer (Raw Data)"]:::bronze
SL["Silver Layer (Cleaned Data)"]:::silver
GL["Gold Layer (Business Data)"]:::gold

%% ================= CONSUMPTION =================
BI["Power BI / Synapse"]:::tool

%% ================= FLOW =================
SRC --> ADF --> ADLS
ADLS --> BR
BR --> DBX
DBX --> CL --> NB
NB --> SL
SL --> GL
GL --> BI

%% ================= STYLES =================
classDef source fill:#9467bd,color:#fff;
classDef tool fill:#17becf,color:#000;
classDef storage fill:#8c564b,color:#fff;
classDef dbx fill:#ff7f0e,color:#000;
classDef compute fill:#bcbd22,color:#000;
classDef bronze fill:#8c564b,color:#fff;
classDef silver fill:#7f7f7f,color:#fff;
classDef gold fill:#d4af37,color:#000;
