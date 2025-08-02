## -----↓ Addendum: Transaction Support ↓-----
### What is a transaction:
- Explanation 1: MySQL transactions are primarily used to process data with large volumes and high complexity. For example, in a personnel management system, if you delete a person, you need to delete not only the person's basic information but also their associated information, such as email addresses, posts, and so on. These database operations constitute a transaction.

- Explanation 2: A transaction is the fundamental unit used to ensure data consistency and integrity in a database management system. It is a collection of operations that must either all succeed or all fail, ensuring that the database transitions from one consistent state to another.

### What problems does transaction support solve?
1. **Data Integrity Issue**: Atomicity and Consistency
- **Atomicity**: All operations in a transaction must either complete or not complete.
- Bank transfer: A transfers 100 yuan to B. This operation involves deducting 100 yuan from A's account and adding 100 yuan to B's account. Both operations must be completed.

- **Consistency**: Before and after a transaction is executed, the database transitions from one consistent state to another.
- Bank transfer: When A transfers money to B, the total balance of A and B remains consistent before and after the transfer.

2. **Concurrency Control Issue**: Isolation
- **Isolation**: When multiple transactions are executed concurrently, the execution of one transaction cannot be interfered with by other transactions.
- Ticket purchasing system: Multiple people want to purchase tickets for the same show (with a limited number of tickets). Without an isolation mechanism, two users might simultaneously read an error indicating that tickets are available, leading to an oversold situation.

3. **System Failure Recovery Issue**: Persistence
- **Persistence**: Once a transaction is committed, its changes to the database are permanent and will not be lost even if the system fails.
- Computer power outage: After a transaction successfully completes its database updates, even if the computer suddenly loses power, these updates will not be lost.

### Typical Transaction Application Scenarios
- Financial transactions: Bank transfers, stock trading, etc.
- **Bank transfer transaction support**: This operation involves deducting 100 yuan from account A and adding 100 yuan to account B. These two steps must be processed as a single transaction. If either step fails (for example, the deduction from account A succeeds, but the transfer to account B fails), the entire transaction is rolled back, ensuring that the funds in account A are not lost and that account B does not receive an incorrect amount.
- E-commerce: Online shopping, payment processing, etc.
- Operations: User payment order --> Includes: Online shopping inventory checks, order generation, deducting user account balances, reducing inventory quantities, etc.
- Healthcare information systems: Medical record updates, drug inventory management, etc.
- Operations: Doctors updating patient medical records --> Includes: Checking patient information, updating diagnosis results, and recording treatment progress, etc.
- Operations: Pharmacy administrators updating drug inventory --> Includes: Checking drug inventory, updating inventory quantities, and recording incoming and outgoing shipments, etc.
- Enterprise Resource Planning (ERP) systems: Financial data processing, inventory management, etc. - Operations: Finance personnel handle accounting tasks, such as bookkeeping and transfers.
- Operations: Warehouse managers update inventory information.
- Ticketing system: Online ticket purchases, ticket information updates, etc.
- Operations: Users purchase tickets.
- Operations: Administrators update ticket information.
- Logistics system: Order processing, inventory management, etc.
- Operations: Logistics personnel process orders.
- Online education platform: Course purchases, user information updates, etc.

## -----↓Addendum↓-----
>Add details for filter, join, group by, and Windows expression.

Both are functionally similar:

SQL: Suitable for scenarios requiring transaction support, complex queries, and small-scale data processing.

PySpark: Suitable for scenarios requiring distributed computing, large-scale data processing, and machine learning.

| Function Category | SQL | PySpark |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Function Description** | Data query language for relational databases | Distributed data processing framework for large-scale data processing |
| **filter** | Used to filter data based on the `WHERE` clause | Used to filter rows in a DataFrame |
| **Syntax** | `SELECT column1, column2, ... FROM table_name WHERE condition;` | `df.filter(condition)` |
| **Example** | `SELECT id, name, age, salary FROM employees WHERE age > 30;` | `employees.filter(employees.age > 30)` |
| **join** | Used to join two or more tables | Used to join two DataFrames |
| **Syntax** | `SELECT column1, column2, ... FROM table1 JOIN table2 ON table1.common_column = table2.common_column;` | `df1.join(df2, join_column, join_type)` |
| **Example** | `SELECT e.id, e.name, e.age, e.salary, d.department_name FROM employees e JOIN departments d ON e.department_id = d.id;` | `employees.join(departments, employees.department_id == departments.id)` |
| **group by** | Used to group by specified columns and perform aggregate calculations | Used to group by specified columns and perform aggregate calculations |
| **Syntax** | `SELECT column1, aggregate_function(column2) FROM table_name GROUP BY column1;` | `df.groupBy(column1).agg(aggregate_function(column2))`|
| **Example** | `SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;` | `employees.groupBy("department_id").agg(count("id").alias("employee_count"))` |
| **window expression** | Used to perform grouped calculations on a dataset without reducing the number of rows, generating a single result for each row (common window functions include ROW_NUMBER, RANK, DENSE_RANK, SUM, AVG, etc.) | Used to perform grouped calculations on a DataFrame without reducing the number of rows, generating a single result for each row |
| **Syntax** | `SELECT column1, column2, window_function(column3) OVER (PARTITION BY column4 ORDER BY column5 ROWS/RANGE clause)` | `from pyspark.sql.window import Window; window_spec = Window.partitionBy(column1).orderBy(column2); df.withColumn("new_column", window_function(column3).over(window_spec))` |
| **Example** | `SELECT id, name, department_id, salary, RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank FROM employees;` | `window_spec = Window.partitionBy("department_id").orderBy(desc("salary")); employees.withColumn("rank", rank().over(window_spec))` |

## -----↓Initial Version Notes↓-----
# PySpark DataFrame
The PySpark DataFrame is an important data structure in Apache Spark's Python API (PySpark) for processing large datasets. It is designed for distributed computing.

```python
from pyspark.sql import SparkSession

# Initialize SparkSession
spark = SparkSession.builder.appName("example").getOrCreate()

# Load data from a CSV file to create a DataFrame
df = spark.read.csv("path/to/file.csv", header=True, inferSchema=True)

# Display the first few rows of the DataFrame
df.show()

# Select specific columns
selected_df = df.select("column1", "column2")

# Filter rows
filtered_df = df.filter(df["column1"] > 10)

# Aggregate data
grouped_df = df.groupBy("Name").agg(avg("Age").alias("Average_Age")) # Use groupBy("Name") to group by the Name column, grouping rows with the same name into the same group. After the groupBy operation, we use the aggregation function avg("Age") to calculate the average age of each group and rename the resulting column to Average_Age.

# Create a DataFrame
df = spark.createDataFrame(data, columns)

# Save the results to a file
aggregated_df.write.csv("path/to/output.csv", header=True)
```

### Key Features:

#### Distributed Data Structure:
PySpark DataFrames are designed to store and process data in a distributed manner across a cluster, making them suitable for handling large datasets.
#### Columnar Storage:
Data is stored in a columnar format, which helps optimize memory usage and improve query performance, especially for aggregation and filtering operations.
#### Lazy Evaluation:
In PySpark, DataFrame operations are lazily evaluated, meaning that the operation is executed only when the result is needed. This allows Spark to optimize the execution plan. #### Rich Operation Support:
PySpark DataFrame provides a rich set of built-in functions and supports various operations, such as selection, filtering, aggregation, joins, sorting, and more.
#### Interoperability with RDDs:
DataFrames can interoperate with Spark's underlying data structure, RDDs (Resilient Distributed Datasets), allowing for more granular data control.
#### Support for Multiple Data Sources:
PySpark DataFrames can load data from a variety of data sources, such as CSV, JSON, Parquet, Hive, and JDBC, and can easily save data back to these formats.
#### SQL Support:
PySpark DataFrames allow queries using SQL, making it easy for users familiar with SQL to use Spark.
#### Fault Tolerance:
Spark's distributed nature makes DataFrames fault-tolerant to node failures.

Optimized Execution:
Spark's Catalyst optimizer optimizes DataFrame execution plans to improve performance. #### API Consistency:
The PySpark DataFrame API is consistent across languages (such as Scala and Java), enabling multi-language development.

### Basic Operations:

#### Creating a DataFrame
#### Viewing Data: show()
#### Selecting Columns: select()
#### Filtering Rows: filter()
#### Aggregating Data: groupBy() and avg()
#### Saving Results