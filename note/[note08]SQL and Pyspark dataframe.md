## -----↓ 补充：事务支持 ↓-----
### 什么是事务：
- 解释一： MySQL 事务主要用于处理操作量大，复杂度高的数据。比如说，在人员管理系统中，你删除一个人员，你即需要删除人员的基本资料，也要删除和该人员相关的信息，如信箱，文章等等，这样，这些数据库操作语句就构成一个事务。

- 解释二： 事务（Transaction）是数据库管理系统中用于确保数据一致性和完整性的基本单位。它是一组操作的集合，这些操作要么全部成功，要么全部失败，以保证数据库从一个一致的状态转换到另一个一致的状态。

### 事务支持解决了什么问题？
1. **数据完整性问题**：原子性和一致性
- **原子性**：事务中的所有操作要么全部完成，要么全部不做
    - 银行转账： A 给 B 转账100块，这个操作包含了A账户扣除100块和B账户增加100块，这两个操作都得实现。

- **一致性**：事务执行前后，数据库从一个一致的状态转换到另一个一致的状态 
    - 银行转账： A 给 B 转账，A 和 B 的总余额在转账前和转账后是一致的。

2. **并发控制问题**：隔离性
- **隔离性**：多个事务并发执行时，一个事务的执行不能被其他事务干扰。
    - 购票系统：多个人要购买同一场次的票（票数有限），没有隔离性机制，可能会出现两个用户同时读取到还有票的错误信息，导致超卖。

3. **系统故障恢复问题**：持久性
- **持久性**：一旦事务提交，它对数据库的改变就是永久性的，即使系统出现故障也不会丢失。
    - 电脑断电：一个事务成功完成对数据库的更新操作后，即使之后电脑突然断电，这些更新也不会丢失。

### 事务的典型应用场景
- 金融交易：银行转账、股票交易等。
    - **银行转账的事务支持**：这个操作包括从A账户扣除100元和向B账户增加100元。这两个步骤必须作为一个事务来处理。如果其中一个步骤失败（例如，从A账户扣款成功，但向B账户转账失败），整个事务会回滚，确保A账户的钱不会丢失，B账户也不会收到错误的金额。
- 电子商务：在线购物、支付处理等。
    - 操作：用户支付订单 --> 包含：在线购物检查库存、生成订单、扣除用户账户余额、减少库存数量等
- 医疗信息系统：病历更新、药品库存管理等。
    - 操作：医生更新患者的病历信息 --> 包含：检查患者信息、更新诊断结果、记录治疗过程等
    - 操作：药房管理员更新药品库存 --> 包含：检查药品库存、更新库存数量、记录入库或出库信息等
- 企业资源规划（ERP）系统：财务数据处理、库存管理等。
    - 操作：财务人员处理账务，如记账、转账等
    - 操作：仓库管理员更新库存信息
- 票务系统：在线购票、票务信息更新等。
    - 操作：用户购买票务
    - 操作：管理员更新票务信息 
- 物流系统：订单处理、库存管理等。
    - 操作：物流人员处理订单
- 在线教育平台：课程购买、用户信息更新等。


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