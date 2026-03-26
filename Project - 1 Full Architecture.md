flowchart TD

%% ================= SOURCES =================
subgraph Sources
    A1["On-Prem SQL Server"]
    A2["REST APIs"]
    A3["Azure Blob Storage"]
end

%% ================= SQL FLOW =================
subgraph SQL_Server_Flow
    S1["SHIR Setup"]
    S2["Linked Service (SQL Server)"]
    S3["Dataset (Tables)"]
    S4["ADF Pipeline - SQL  
    Copy, Lookup, ForEach, SP, Metadata, If"]
end

%% ================= API FLOW =================
subgraph REST_API_Flow
    R1["Linked Service (REST API)"]
    R2["Dataset (JSON)"]
    R3["ADF Pipeline - API  
    Web, Copy, SetVar, Until, ForEach, If"]
end

%% ================= SECURITY =================
subgraph Security_Layer
    SEC1["AAD"]
    SEC2["Managed Identity"]
    SEC3["Key Vault"]
    SEC4["RBAC"]
    SEC5["Network Security"]
    SEC6["Encryption"]
    SEC7["Monitoring"]
end

%% ================= ADF =================
subgraph ADF_ETL
    ETL["ADF Orchestration  
    Extraction, Transform, Load, Control Flow"]
end

%% ================= BRONZE =================
subgraph Bronze_Layer
    BZ["ADLS Bronze  
    Raw Data Storage"]
end

%% ================= SILVER =================
subgraph Silver_Layer
    SL1["Databricks Silver  
    Cleaning & Transform"]
    SL2["ADLS Silver"]
end

%% ================= GOLD =================
subgraph Gold_Layer
    GL1["Databricks Gold  
    Business Logic"]
    GL2["ADLS Gold"]
end

%% ================= DELTA =================
subgraph Delta_Lake
    DL["Delta Lake  
    Partition, Z-Order, ACID"]
end

%% ================= SYNAPSE =================
subgraph Synapse_Layer
    SYN["Azure Synapse  
    External Tables, Load, Query"]
end

%% ================= ANALYTICS =================
subgraph Analytics
    BI["Power BI"]
end

%% ================= DEVOPS =================
subgraph DevOps
    DEV["Azure DevOps CI/CD"]
end

%% ================= FLOW =================
A1 --> S1 --> S2 --> S3 --> S4
A2 --> R1 --> R2 --> R3
A3 --> ETL

S4 --> ETL
R3 --> ETL

SEC1 --> ETL
SEC2 --> ETL
SEC3 --> ETL
SEC4 --> ETL
SEC5 --> ETL
SEC6 --> ETL
SEC7 --> ETL

ETL --> BZ
BZ --> SL1 --> SL2
SL2 --> GL1 --> GL2
GL2 --> DL
DL --> SYN
SYN --> BI
BI --> DEV
