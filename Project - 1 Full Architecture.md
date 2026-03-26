[Step 1: Data Sources]
   ├── On-Prem SQL Server (Structured Data)
   ├── REST APIs (JSON Data)
   └── Azure Blob Storage (Files)
            │
            ▼

================ SQL SERVER FLOW ================

[SHIR Setup]
   - Installed & Configured (Secure Outbound HTTPS)
   ▼
[Linked Service (SQL Server)]
   - SQL Auth / Windows Auth
   ▼
[Dataset (Tables)]
   ▼
[ADF Pipeline - SQL]
   - Copy Activity (Full / Incremental Load)
   - Lookup Activity (Watermark)
   - ForEach Activity (Multiple Tables)
   - Stored Procedure Activity (Pre/Post Load)
   - Get Metadata Activity
   - If Condition Activity
   ▼

================ REST API FLOW ================

[Linked Service (REST API)]
   - HTTPS / Secure Endpoint
   ▼
[Dataset (JSON Response)]
   ▼
[ADF Pipeline - API]
   - Web Activity (API Call / Token Handling)
   - Copy Activity (API → ADLS)
   - Set Variable (Token/Page Count)
   - Until Activity (Pagination Loop)
   - ForEach Activity (Multiple APIs)
   - If Condition (Response Validation)
   ▼

================ 🔐 SECURITY LAYER (STEP-BY-STEP) ================

[Step S1: Azure Active Directory (AAD)]
   - Authentication & Service Principals
   ▼
[Step S2: Managed Identity]
   - Secure Service-to-Service Access
   ▼
[Step S3: Azure Key Vault]
   - Store Secrets (SQL, API Keys, Connection Strings)
   ▼
[Step S4: RBAC]
   - Role Assignment (Least Privilege)
   ▼
[Step S5: Network Security]
   - Firewall, Private Endpoints, VNet
   ▼
[Step S6: Encryption]
   - At Rest & In Transit (HTTPS)
   ▼
[Step S7: Monitoring]
   - Azure Monitor, Logs, Alerts
   ▼

================ INGESTION & ETL (ADF) ================

[ADF Orchestration Layer]

   🔹 Extraction:
   - Copy Activity (SQL/API → ADLS)
   - Web Activity (API Calls)

   🔹 Transformation (Light ETL):
   - Mapping Data Flow:
        • Filter
        • Derived Column
        • Join
        • Aggregate
   - Lookup (Reference Data)
   - If Condition (Validation)

   🔹 Loading:
   - Copy Activity (ADLS / Synapse)

   🔹 Orchestration:
   - Pipeline
   - Execute Pipeline
   - ForEach
   - Until
   - Trigger (Schedule/Event)

   🔹 Monitoring:
   - Set Variable
   - Wait
   - Fail
   - Logging
            │
            ▼

================ 🟫 BRONZE LAYER (RAW) ================

[ADLS Gen2 - Bronze]

   ✅ Activities:
   - Store Raw Data (JSON, CSV, Parquet)
   - Partitioning (Date/Source)
   - Maintain Original Data
   - Basic Validation (Row Count, Schema Check)
            │
            ▼

================ 🟪 SILVER LAYER (CLEANED) ================

[Azure Databricks - Silver]

   ✅ Activities:
   - Data Cleaning (Null, Duplicates)
   - Schema Enforcement
   - Data Type Casting
   - Joins Across Sources
   - Filtering Invalid Data
   - Standardization

            │
            ▼

[ADLS - Silver Layer]
            │
            ▼

================ 🟨 GOLD LAYER (BUSINESS) ================

[Azure Databricks - Gold]

   ✅ Activities:
   - Aggregations (KPIs, Metrics)
   - Business Logic Implementation
   - Fact & Dimension Tables
   - Star Schema Modeling
   - Performance Optimization

            │
            ▼

[ADLS - Gold Layer]
            │
            ▼

================ ⚡ DELTA LAKE OPTIMIZATION ================

[Delta Lake]

   ✅ Activities:
   - Delta Table Creation
   - Partitioning
   - Z-Ordering (Indexing)
   - Vacuum (Cleanup)
   - ACID Transactions
            │
            ▼

================ SERVING LAYER ================

[Azure Synapse Analytics]

   ✅ Activities:
   - External Tables
   - Load Gold Data
   - Query Optimization
   - Indexing
            │
            ▼

================ ANALYTICS LAYER ================

[Power BI]

   ✅ Activities:
   - Dashboard Creation
   - Report Development
   - DAX Measures
            │
            ▼

================ DEVOPS & SECURITY ================

[Azure DevOps]

   ✅ Activities:
   - CI/CD Pipeline Setup
   - Git Integration
   - Automated Deployment

[Security]

   ✅ Activities:
   - RBAC (Role-Based Access)
   - Managed Identity
   - Data Encryption
