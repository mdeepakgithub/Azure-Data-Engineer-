# PySpark Interview Questions & Answers

---

## 1. What is Big Data

**Answer:**  
Big Data refers to extremely large, fast-growing, and complex datasets that traditional databases and tools cannot store, process, or analyze efficiently.

### Key characteristics (5 Vs):

- **Volume**: Massive amounts of data (terabytes to petabytes)  
- **Velocity**: Data generated and processed at high speed (real-time or near real-time)  
- **Variety**: Multiple data types (structured, semi-structured, unstructured)  
- **Veracity**: Data quality and reliability  
- **Value**: Business insights derived from the data  

---

## 2. Difference Between Hadoop and Spark

Hadoop and Spark are both open-source big data frameworks, but they differ mainly in processing.

### Hadoop: Disk-Based Batch Processing

- Uses MapReduce
- Reads/writes data to disk (HDFS)

**Flow:**
1. Data read from HDFS  
2. Map output written to disk  
3. Reduce reads again from disk  
4. Output written to HDFS  

**Impact:**
- Heavy disk I/O  
- Slower execution  
- Best for batch jobs  
- Not efficient for ML  

---

### Spark: In-Memory Computation

- Uses RAM for processing  
- Stores intermediate data in memory  

**Flow:**
1. Load data once  
2. Process in memory  
3. Reuse data  
4. Write only final output  

**Impact:**
- Faster processing  
- Minimal disk I/O  
- Ideal for real-time & ML  

---

### Comparison Table

| Aspect | Hadoop | Spark |
|--------|--------|-------|
| Core purpose | Storage + batch | Fast processing |
| Processing | Disk-based | In-memory |
| Speed | Slow | Fast |
| Data processing | Batch | Batch + Streaming |
| Ease | Complex | Easy APIs |
| Fault tolerance | HDFS replication | RDD lineage |
| Use cases | Batch jobs | Real-time, ML |

**Summary:**
- Hadoop → Storage + batch  
- Spark → Fast analytics  

---

## 3. MapReduce vs Spark

**MapReduce:**
- Distributed processing (Map + Reduce)  
- Disk-based → slow  

**Spark Advantages:**
- In-memory processing  
- Faster  
- Supports streaming, SQL, ML  
- Easy APIs  

👉 Spark is faster and more flexible.

---

## 4. Role of Data Engineer Using PySpark

- Data ingestion (DB, APIs, files)  
- Data cleaning & transformation  
- ETL/ELT pipelines  
- Performance tuning  
- Batch & streaming  
- Store data in lakes/warehouses  

👉 Focus: Scalable pipelines

---

## 5. Spark Architecture

### Components:
- **Driver** → Main program  
- **Cluster Manager** → Resource manager  
- **Executors** → Execute tasks  
- **Worker Nodes** → Run processing  

### Flow:
Driver → Cluster Manager → Executors → Process → Output  

### Advantages:
- Parallelism  
- Fault tolerance  
- Flexibility  
- Speed  

---

## 6. How Spark Executes Code

1. Driver starts  
2. DAG created  
3. Lazy evaluation  
4. Split into stages  
5. Split into tasks  
6. Run on executors  
7. Return results  

👉 DAG → Stages → Tasks  

---

### Deploy Modes

**Client Mode**
- Driver runs locally  
- Less reliable  

**Cluster Mode**
- Driver runs in cluster  
- More reliable  

👉 Only driver location changes  

---

## 7. Current Node vs Edge Node

**Current Node**
- Where you work  

**Edge Node**
- Gateway to cluster  

👉 Edge node is entry point  

---

## 8. Why DataFrames over RDD

### Advantages:
- Faster (Catalyst Optimizer)  
- Less code  
- SQL support  
- Auto optimization  

### RDD Limitations:
- No optimization  
- More code  
- Slower  

👉 DataFrames are preferred  

---

## 9. DataFrame Creation

### Using RDD:
- Manual schema  
- Less optimized  

### Without RDD:
- Direct from source  
- Fully optimized  

👉 Direct DF is better  

---

## 10. CSV Reading Best Practices

- Header = true  
- Define schema  
- Validate data types  
- Correct delimiter  
- Handle nulls  
- Handle corrupt records  
- Encoding (UTF-8)  
- Handle quotes  
- Optimize performance  

👉 Focus on data quality  

---

## 11. InferSchema vs Custom Schema

**InferSchema**
- Auto-detect  
- Slower  

**Custom Schema**
- Manual  
- Faster  

👉 Use custom schema  

---

## 12. Why Nullable Not Auto Updated

- DataTypes can change  
- Nullable is a constraint  

👉 Spark won’t assume no nulls  

---

## 13. Why nullable = false

- Enforces data integrity  
- Prevents null values  

👉 Ensures data quality  

---

## 14. Parquet vs ORC

**Parquet Advantages:**
- Columnar format  
- High compression  
- Faster queries  
- Spark optimized  

👉 Preferred in Spark  

---

## 15. Why Parquet Over ORC

- Better ecosystem  
- Works across tools  
- Cloud friendly  

👉 More flexible  

---

## 16. GROUP BY vs PARTITION BY

| Feature | GROUP BY | PARTITION BY |
|--------|---------|-------------|
| Rows | Reduced | Not reduced |
| Use | Aggregation | Window |

👉 GROUP BY aggregates  

---

## 17. Window Functions

- OVER() → Mandatory  
- PARTITION BY → Optional  
- ORDER BY → Required for ranking  

👉 ORDER BY needed for RANK  

---

## 18. PartitionBy vs GroupBy

- GROUP BY → Aggregates  
- PARTITION BY → Keeps rows  

---

## 19. UNION vs UNION ALL

- UNION → Removes duplicates  
- UNION ALL → Keeps duplicates  

👉 UNION ALL is faster  

---

## 20. select vs selectExpr

- select → Column-based  
- selectExpr → SQL expressions  

---

## 21. Flatten vs Explode

- Flatten → Removes nesting  
- Explode → Expands arrays  

👉 Explode increases rows  

---

## 22. withColumn vs withColumnRenamed

- withColumn → Add/modify  
- withColumnRenamed → Rename  

---

## 23. Rank vs DenseRank

| Rank | DenseRank |
|------|----------|
| Skips numbers | No gaps |

---

## 24. Narrow vs Wide Transformations

**Narrow:**
- map  
- filter  

**Wide:**
- groupBy  
- join  

👉 Wide = shuffle  

---

## 25. Actions Examples

- show()  
- collect()  
- count()  
- write()  

---

## 26. Storage Format

👉 Parquet (most preferred)  

---

## 27. Broadcast Join

- Used when one dataset is small  
- Improves performance  

---

## 28. Logical vs Physical Plan

- Logical → What to do  
- Physical → How to do  

---

## 29. Catalyst Optimizer

- Optimizes query execution  
- Improves performance  

---

## 30. AQE (Adaptive Query Execution)

- Adjusts plan at runtime  
- Improves joins & partitions  

---

## 31. Parquet ACID Support

❌ Not directly  
✅ Supported via Delta Lake  

---

## 32. Modes in Spark

- Append  
- Overwrite  
- Ignore  
- Error  

---

## 33. Repartition

- Increase/decrease partitions  
- Causes shuffle  

---

## 34. Coalesce

- Reduce partitions only  
- No shuffle  

---

## 35. Repartition vs Coalesce

- Repartition → Shuffle  
- Coalesce → No shuffle  

👉 Use coalesce for reducing files  

---

## 36.

(To be added)

---

# ⭐ End of Document
