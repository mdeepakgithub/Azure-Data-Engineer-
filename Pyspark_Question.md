# PySpark Interview Questions & Answers

---

## 1. What is Big Data?

Big Data refers to extremely large, fast-growing, and complex datasets that traditional databases cannot process efficiently.

### 5 Vs:
- **Volume** – Huge amount of data
- **Velocity** – High speed of data generation
- **Variety** – Different types (structured, unstructured)
- **Veracity** – Data quality
- **Value** – Business insights

---

## 2. Difference Between Hadoop and Spark

| Aspect | Hadoop | Spark |
|--------|--------|-------|
| Processing | Disk-based | In-memory |
| Speed | Slower | Faster |
| Use Case | Batch processing | Batch + Real-time |
| Ease of Use | Complex | Easy APIs |

### Summary:
- Hadoop → Storage + Batch  
- Spark → Fast processing + Real-time  

---

## 3. MapReduce vs Spark

**MapReduce**
- Disk-based
- Slow
- Batch only

**Spark Advantages**
- In-memory processing
- Faster
- Supports ML, Streaming, SQL

👉 Spark is faster and more flexible than MapReduce.

---

## 4. Role of Data Engineer Using PySpark

- Data ingestion (DB, API, Files)
- Data cleaning & transformation
- ETL/ELT pipelines
- Performance tuning
- Batch & streaming processing

👉 Focus: Scalable data processing

---

## 5. Spark Architecture

### Components:
- **Driver** → Controls execution
- **Cluster Manager** → Resource allocation
- **Executors** → Run tasks
- **Worker Nodes** → Perform processing

### Flow:
Driver → Cluster Manager → Executors → Process → Output

### Advantages:
- Parallel processing
- Fault tolerance
- High speed

---

## 6. How Spark Executes Code

1. Driver starts program  
2. Creates DAG  
3. Lazy evaluation  
4. Split into stages  
5. Split into tasks  
6. Run on executors  
7. Return results  

👉 Spark executes using DAG → Stages → Tasks

---

## 7. Client Mode vs Cluster Mode

| Mode | Description |
|------|------------|
| Client Mode | Driver runs on local machine |
| Cluster Mode | Driver runs inside cluster |

👉 Only driver location changes

---

## 8. Current Node vs Edge Node

- **Current Node** → Where you work  
- **Edge Node** → Gateway to cluster  

👉 Edge node is entry point

---

## 9. Why DataFrames over RDD?

### Advantages:
- Faster (Catalyst Optimizer)
- Less code
- SQL support
- Automatic optimization

### RDD Limitations:
- No optimization
- More code
- Slower

👉 DataFrames are preferred

---

## 10. Creating DataFrame

### With RDD:
- Manual schema
- Less optimized

### Without RDD:
- Direct from source
- Optimized

👉 Direct DF is better

---

## 11. CSV Reading Best Practices

- Header = true
- Define schema
- Correct delimiter
- Handle nulls
- Encoding (UTF-8)
- Handle bad records
- Performance tuning

👉 Focus on data quality + performance

---

## 12. InferSchema vs Custom Schema

### InferSchema:
- Auto-detect types
- Slower

### Custom Schema:
- Defined manually
- Faster

👉 Custom schema is recommended

---

## 13. Why Nullable Not Auto Updated?

- Data types can change
- Nullable is a constraint

👉 Spark won’t assume no nulls

---

## 14. Why Nullable = False?

- Enforces data integrity
- Prevents null values

👉 Ensures data quality

---

## 15. Parquet vs ORC

### Parquet Advantages:
- Columnar storage
- High compression
- Faster queries
- Spark optimized

👉 Preferred in Spark

---

## 16. Why Parquet Over ORC?

- Better ecosystem support
- Works across tools
- Cloud friendly

👉 More flexible

---

## 17. GROUP BY vs PARTITION BY

| Feature | GROUP BY | PARTITION BY |
|--------|---------|-------------|
| Rows | Reduced | Not reduced |
| Use | Aggregation | Window functions |

👉 GROUP BY aggregates, PARTITION BY does not

---

## 18. Window Functions

- OVER() → Mandatory  
- PARTITION BY → Optional  
- ORDER BY → Required for ranking  

👉 ORDER BY needed for RANK()

---

## 19. PartitionBy vs GroupBy (Concept)

- GROUP BY → Aggregates data  
- PARTITION BY → Keeps rows  

👉 Window functions need PARTITION BY

---

## 20. Union vs Union All

- UNION → Removes duplicates  
- UNION ALL → Keeps duplicates  

👉 UNION ALL is faster

---

## 21. select vs selectExpr

- select → Column-based  
- selectExpr → SQL expressions  

👉 selectExpr is flexible

---

## 22. Flatten vs Explode

- Flatten → Removes nesting  
- Explode → Expands arrays  

👉 Explode increases rows

---

## 23. withColumn vs withColumnRenamed

- withColumn → Add/modify column  
- withColumnRenamed → Rename  

---

## 24. Rank vs DenseRank

| Rank | DenseRank |
|------|----------|
| Skips numbers | No gaps |

---

## 25. Narrow vs Wide Transformations

### Narrow:
- map
- filter

### Wide:
- groupBy
- join

👉 Wide = shuffle

---

## 26. Actions Examples

- show()
- collect()
- count()
- write()

---

## 27. File Format for Storage

👉 Parquet (most preferred)

---

## 28. Broadcast Join

- When one dataset is small  
- Improves performance  

---

## 29. Logical vs Physical Plan

- Logical → What to do  
- Physical → How to do  

---

## 30. Catalyst Optimizer

- Optimizes query execution  
- Improves performance  

---

## 31. AQE (Adaptive Query Execution)

- Adjusts plan at runtime  
- Improves joins & partitions  

---

## 32. Does Parquet Support ACID?

❌ No (Directly)  
✅ Supported via Delta Lake  

---

## 33. Modes in Spark

- Append  
- Overwrite  
- Ignore  
- Error  

---

## 34. Repartition

- Increase/decrease partitions  
- Causes shuffle  

---

## 35. Coalesce

- Reduce partitions only  
- No shuffle  

👉 Used for optimization

---

## 36. Repartition vs Coalesce

- Repartition → shuffle  
- Coalesce → no shuffle  

👉 Use coalesce for reducing files

---

# ⭐ End of Document
