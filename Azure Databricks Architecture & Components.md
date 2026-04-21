# ⚡ Azure Databricks Architecture & Components (Step-by-Step)

## 📌 Overview
Azure Databricks is a unified analytics platform built on Apache Spark, used for large-scale data processing, transformation, and analytics.

---

## 🏗️ Architecture Diagram

```mermaid
flowchart LR

%% ================= CONTROL PLANE =================
CP["Control Plane
(Managed by Azure Databricks)"]:::control

%% ================= DATA PLANE =================
DP["Data Plane (Customer Subscription)"]:::data

%% ================= COMPONENTS =================
WS["Workspace
(UI, Notebooks, Jobs)"]:::comp

CL["Cluster
Driver + Worker Nodes"]:::comp

NB["Notebooks (PySpark, SQL, Scala)"]:::comp

DBFS["DBFS / ADLS Storage"]:::storage

DL["Delta Lake"]:::storage

JOB["Jobs & Scheduling"]:::comp

%% ================= FLOW =================
CP --> WS
DP --> CL
WS --> NB
NB --> CL
CL --> DBFS
DBFS --> DL
WS --> JOB
JOB --> NB

%% ================= STYLES =================
classDef control fill:#1f77b4,color:#fff;
classDef data fill:#ff7f0e,color:#000;
classDef comp fill:#2ca02c,color:#fff;
classDef storage fill:#8c564b,color:#fff;




