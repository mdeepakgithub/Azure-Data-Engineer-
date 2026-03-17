 🔷 On-Prem SQL Server to Azure Data Factory Pipeline

📌 Project Overview
This project demonstrates how to integrate an on-premises SQL Server with Azure Data Factory (ADF) to build a scalable and automated data pipeline.

---

 🏗️ Architecture
**On-Prem SQL Server → Self-Hosted Integration Runtime → Azure Data Factory → Azure Data Lake / Synapse**

---

 ⚙️ Key Components

 1. Self-Hosted Integration Runtime (SHIR)
- Acts as a bridge between on-prem SQL Server and Azure  
- Installed on local server  
- Enables secure data movement  

---

 2. Linked Services
- SQL Server (Source)  
- Azure Data Lake / Blob / Synapse (Target)  

---

3. Datasets
- Source dataset: SQL Server tables  
- Target dataset: Storage (ADLS Gen2 / Blob)  

---

 🔄 Pipeline Activities

 ✔ Copy Data Activity
- Transfers data from SQL Server to Azure storage  
- Supports full load and incremental load  

---

 ✔ Incremental Load (Watermark Logic)

```sql
SELECT * FROM Orders
WHERE LastModifiedDate > @LastRunTime;
```

---

 ✔ Control Flow Activities
- Lookup → Fetch last load time  
- Set Variable → Store values  
- ForEach → Loop multiple tables  
- If Condition → Apply logic  

---

 ✔ Data Transformation (Optional)
- Mapping Data Flow (ADF)  
- Azure Databricks (PySpark)  

---

 🔐 Security
- Authentication (SQL/Windows)  
- Azure Key Vault for secrets  
- Secure SHIR configuration  

---

 ⏰ Scheduling
- Trigger-based execution (Daily/Hourly)  

---

 📊 Monitoring
- Pipeline monitoring in ADF  
- Error handling and retry mechanisms  

---

🚀 Conclusion
This pipeline enables secure, scalable, and automated data integration from on-prem SQL Server to Azure cloud for analytics and reporting.




