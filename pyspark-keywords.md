## 🧩 1️⃣ Core PySpark Keywords

| Category | Common PySpark Keyword / Function | Purpose in Your Project |
|---|---|---|
| Session Initialization | SparkSession.builder.appName() getOrCreate() | To create Spark environment inside Databricks for processing. |
| Reading Data | spark.read.csv() spark.read.json() spark.read.format("delta") | To read raw data from ADLS (Bronze layer). |
| Writing Data | df.write.mode("overwrite").format("delta").save() | To write cleaned/transformed data back into ADLS Silver/Gold layers in Delta format. |
| Schema Definition | StructType, StructField, StringType, IntegerType, DoubleType | To define custom schema for reading files instead of using inferSchema. |
| Filtering | df.filter(df["column"] == "value") df.where() | To remove unwanted rows, e.g., invalid or null transactions. |
| Column Operations | withColumn(), drop(), select(), alias() | Add new columns like total_amount, rename or drop unnecessary columns. |
| Aggregations | groupBy().agg(sum(), avg(), count()) | To create summary tables like total sales per region. |
| Joins | join(df2, ["key_column"], "inner") | To join orders, customers, and product datasets. |
| Sorting / Ordering | orderBy("date", ascending=False) | To sort sales records by latest date. |
| Distinct / Drop Duplicates | dropDuplicates(["order_id"]) | To remove duplicate orders or transactions. |
| Null Handling | fillna(), dropna() | To handle missing or invalid data values. |
| Conditional Logic | when(), otherwise() from pyspark.sql.functions | To apply conditional logic (e.g., discount calculation or status categorization). |
| Date & Time Functions | to_date(), year(), month(), date_format() | To standardize and extract date/time fields for reporting. |
| Data Cleaning | trim(), lower(), regexp_replace() | To clean string columns like customer names or product categories. |
| Union / Merge | unionByName() | To merge multiple source files or datasets. |
| Window Functions | Window.partitionBy().orderBy() | To calculate ranking, running totals, or deduplicate rows. |
| Delta Lake Operations | MERGE INTO, UPDATE, DELETE, VACUUM, OPTIMIZE | To perform incremental updates and manage ACID transactions in Delta Lake. |
| UDF (User Defined Functions) | udf(lambda x: custom_logic, returnType) | For applying custom transformations (e.g., string manipulation, risk scoring). |
