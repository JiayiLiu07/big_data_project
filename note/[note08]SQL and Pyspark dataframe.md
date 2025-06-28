## -----↓补充↓-----
>Add details for filter, join, group by, windows expression.

两者在功能上相似：

SQL：适用于需要事务支持、复杂查询和小规模数据处理的场景。

PySpark：适用于需要分布式计算、大规模数据处理和机器学习的场景。

| 功能类别                   | SQL                                                                                                                             | PySpark                                                                                                                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **功能描述**               | 数据查询语言，用于关系型数据库                                                                                                                 | 分布式数据处理框架，用于大规模数据处理                                                                                                                                                          |
| **filter**             | 用于筛选数据，基于`WHERE`子句                                                                                                              | 用于筛选DataFrame中的行                                                                                                                                                             |
| **语法**                 | `SELECT column1, column2, ... FROM table_name WHERE condition;`                                                                 | `df.filter(condition)`                                                                                                                                                       |
| **示例**                 | `SELECT id, name, age, salary FROM employees WHERE age > 30;`                                                                   | `employees.filter(employees.age > 30)`                                                                                                                                       |
| **join**               | 用于将两个或多个表连接起来                                                                                                                   | 用于将两个DataFrame连接起来                                                                                                                                                           |
| **语法**                 | `SELECT column1, column2, ... FROM table1 JOIN table2 ON table1.common_column = table2.common_column;`                          | `df1.join(df2, join_column, join_type)`                                                                                                                                      |
| **示例**                 | `SELECT e.id, e.name, e.age, e.salary, d.department_name FROM employees e JOIN departments d ON e.department_id = d.id;`        | `employees.join(departments, employees.department_id == departments.id)`                                                                                                     |
| **group by**           | 用于按指定列分组并进行聚合计算                                                                                                                 | 用于按指定列分组并进行聚合计算                                                                                                                                                              |
| **语法**                 | `SELECT column1, aggregate_function(column2) FROM table_name GROUP BY column1;`                                                 | `df.groupBy(column1).agg(aggregate_function(column2))`                                                                                                                       |
| **示例**                 | `SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;`                                                         | `employees.groupBy("department_id").agg(count("id").alias("employee_count"))`                                                                                                |
| **windows expression** | 用于对数据集进行分组计算，不减少行数，为每一行生成一个计算结果（常见的窗口函数有ROW_NUMBER、RANK、DENSE_RANK、SUM、AVG等）                                                                                                              | 用于对DataFrame进行分组计算，不减少行数，为每一行生成一个计算结果                                                                                                                                                     |
| **语法**                 | `SELECT column1, column2, window_function(column3) OVER (PARTITION BY column4 ORDER BY column5 ROWS/RANGE clause)`              | `from pyspark.sql.window import Window; window_spec = Window.partitionBy(column1).orderBy(column2); df.withColumn("new_column", window_function(column3).over(window_spec))` |
| **示例**                 | `SELECT id, name, department_id, salary, RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank FROM employees;` | `window_spec = Window.partitionBy("department_id").orderBy(desc("salary")); employees.withColumn("rank", rank().over(window_spec))`                                          |


## -----↓初始版笔记↓-----
# PySpark DataFrame
是 Apache Spark 的 Python API（PySpark）中的一个重要数据结构，用于处理大规模数据集。专为分布式计算设计。

```python
from pyspark.sql import SparkSession

# 初始化 SparkSession
spark = SparkSession.builder.appName("example").getOrCreate()

# 从 CSV 文件加载数据创建 DataFrame
df = spark.read.csv("path/to/file.csv", header=True, inferSchema=True)

# 显示 DataFrame 的前几行
df.show()

# 选择特定列
selected_df = df.select("column1", "column2")

# 过滤行
filtered_df = df.filter(df["column1"] > 10)

# 聚合数据
grouped_df = df.groupBy("Name").agg(avg("Age").alias("Average_Age"))#使用groupBy("Name")按照Name列进行分组，将相同姓名的行分到同一组。在groupBy之后，使用聚合函数avg("Age")计算每个组的平均年龄，并将结果列重命名为Average_Age。

# 创建DataFrame
df = spark.createDataFrame(data, columns)


# 保存结果到文件
aggregated_df.write.csv("path/to/output.csv", header=True)
```


### 关键特点：

#### 分布式数据结构：
PySpark DataFrame 旨在在集群上分布式地存储和处理数据，这使得它能够处理大规模数据集。
#### 列式存储：
数据以**列式格式存储**，这有助于优化内存使用和提升查询性能，特别是对于聚合和筛选操作。
#### 惰性评估：
在 PySpark 中，DataFrame 操作是惰性评估的，意味着只有在**需要结果时才会执行操作**。这允许 Spark 优化执行计划。
#### 丰富的操作支持：
PySpark DataFrame 提供了丰富的内置函数和支持各种操作，如选择、过滤、聚合、连接、排序等。
#### 与 RDD 的互操作性：
DataFrame 可以与 Spark 的底层数据结构 RDD（弹性分布式数据集）互操作，允许更精细的数据控制。
#### 支持多种数据源：
PySpark DataFrame 可以从多种数据源加载数据，如 CSV、JSON、Parquet、Hive、JDBC 等，并且可以轻松地将数据保存回这些格式。
#### SQL 支持：
PySpark DataFrame 允许使用 SQL 语言进行查询，使得熟悉 SQL 的用户能够轻松地使用 Spark。
#### 容错性：
Spark 的分布式特性使得 DataFrame 在面对节点失败时具有容错性。
优化执行：
Spark 的 Catalyst 优化器会优化 DataFrame 的执行计划，以提高性能。
#### API 一致性：
PySpark DataFrame API 在不同语言（如 Scala、Java）之间保持一致，使得多语言开发成为可能。

### 基本操作：

#### 创建 DataFrame
#### 查看数据：show() 
#### 选择列：select() 
#### 过滤行：filter() 
#### 聚合数据：groupBy() 和 avg() 
#### 保存结果