# ⚡ PySpark Architecture & Components (Project-Focused)

## 📌 Overview
PySpark is the Python API for Apache Spark used for distributed data processing.  
In our project, PySpark was used inside Azure Databricks to process large datasets using a cluster (Driver + Executors).

PySpark Components (What Exists Inside)


🔹 1. SparkSession (Entry Point)
Main entry point to PySpark
Used to read/write data and run SQL queries
spark = SparkSession.builder.appName("App").getOrCreate()



🔹 2. Driver Program (Brain 🧠)
Runs your main PySpark code
Responsibilities:
Creates SparkSession
Builds DAG (execution plan)
Divides job into stages & tasks
Sends tasks to executors


🔹 3. Cluster Manager
Manages cluster resources (CPU, Memory)
Allocates executors
Types:
YARN
Kubernetes
Standalone
(Databricks manages internally)


🔹 4. Executors (Workers ⚙️)
Run on worker nodes
Perform actual data processing
Responsibilities:
Execute tasks
Store data in memory/cache
Return results to driver


🔹 5. Tasks
Smallest unit of work
Each task processes one partition of data
Executed in parallel across executors


🔹 6. DAG (Directed Acyclic Graph)
Logical execution plan created by driver
Optimizes transformations before execution


🔹 7. Jobs → Stages → Tasks
Execution Hierarchy:
Job → Triggered by an action
Stage → Group of tasks (based on shuffle)
Task → Runs on executor


🔹 8. Transformations vs Actions
Transformations (Lazy Execution)
filter()
select()
join()
groupBy()
Actions (Trigger Execution)
show()
collect()
write()


🔹 9. Partitioning
Data is split into partitions
Each partition processed by one task
Improves parallelism


🔹 10. Shuffle (Important 🔥)
Data movement between executors
Happens during:
join()
groupBy()
Expensive operation → needs optimization


🔹 11. Cache / Persist
Stores data in memory
Avoids recomputation
df.cache()


🔹 12. Broadcast Variables
Used to send small data to all executors
Improves join performance


🔄 End-to-End Execution Flow
User writes PySpark code
SparkSession created
Driver builds DAG
Action triggers job
Job split into stages
Stages split into tasks
Tasks sent to executors
Executors process data in parallel
Results returned to driver





---

## 🏗️ PySpark Architecture Diagram

```mermaid
flowchart LR

%% ================= USER =================
USR["User (PySpark Code)"]:::user

%% ================= DRIVER =================
DRV["Driver Program
(SparkSession / DAG)"]:::driver

%% ================= CLUSTER MANAGER =================
CM["Cluster Manager
(Allocates Resources)"]:::manager

%% ================= EXECUTORS =================
EX1["Executor 1"]:::exec
EX2["Executor 2"]:::exec
EX3["Executor N"]:::exec

%% ================= TASKS =================
T1["Task"]:::task
T2["Task"]:::task
T3["Task"]:::task

%% ================= FLOW =================
USR --> DRV
DRV --> CM
CM --> EX1
CM --> EX2
CM --> EX3

EX1 --> T1
EX2 --> T2
EX3 --> T3

%% ================= STYLES =================
classDef user fill:#9467bd,color:#fff;
classDef driver fill:#1f77b4,color:#fff;
classDef manager fill:#ff7f0e,color:#000;
classDef exec fill:#2ca02c,color:#fff;
classDef task fill:#d62728,color:#fff;
