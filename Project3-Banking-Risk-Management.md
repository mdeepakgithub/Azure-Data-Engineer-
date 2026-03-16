## Project 3 :– Banking Risk Management System

### Description:-

This project involved building a Banking Risk Management System using Microsoft Fabric, Azure Synapse, and Python to detect fraud and assess credit risk in real time across millions of financial transactions.

I designed and implemented real-time data ingestion pipelines using Fabric Event Streams and Data Factory to capture transaction data from payment gateways, core banking systems, and customer APIs.

The data was processed and stored in Fabric’s Delta Lake, where I performed feature engineering in PySpark notebooks to generate risk attributes and behavioral metrics.

Using Fabric Data Science integrated with Synapse Spark Pools, I developed machine learning models for credit risk scoring and fraud detection, applying both classification and anomaly detection techniques.

I tracked experiments and model metrics with MLflow, then deployed the optimized models to Fabric Real-time Analytics for live transaction scoring.

The system analyzed each incoming transaction instantly, assigned a risk score, and triggered alerts if suspicious patterns were detected.

These alerts were visualized through Power BI dashboards that monitored fraud trends, risk exposure, and credit score distribution.

I also implemented RBAC, encryption, and Microsoft Purview lineage tracking to ensure regulatory compliance.

A key challenge was minimizing false positives in fraud detection; I resolved this by improving training data quality and adopting ensemble ML models.

### Outcome:

✅ Achieved 95% fraud-detection accuracy with sub-second response times.  
✅ Processed thousands of transactions per second with reliable alerting.  
✅ Reduced manual fraud investigation effort by 40%.  
✅ Strengthened regulatory compliance and enhanced operational efficiency.

### Technologies Used:

Microsoft Fabric (Event Streams, Data Factory, Data Science, Real-time Analytics), Azure Synapse Analytics, Python, PySpark, MLflow, Delta Lake, Power BI, Microsoft Purview, Azure Active Directory
