# HADOOP, YARN, ZOOKEEPER, HIVE, FLINK

## -----↓Addendum↓-----
The essence of `Hadoop` is the program: HDFS and MapReduce.

`Hive` is essentially a translator. It corresponds to the engine's language.

> Program execution
>> Computers are abstracted into nodes: Namenode and Worknode

>> Actual storage is on the worknode's hard drive. The hard drive is abstracted as a file resource manager.

`Flink` **Streaming data** (works with Kafka) / `Spark` **Batch data** / `MapReduce` are largely unused -> These three have similar functions.

**Streaming data** is mostly stored in memory.

**Batch data** is stored in Hadoop's HDFS.

## Hadoop
![alt text](07hadoop_2.png)
`Hadoop` is an open source framework for efficiently storing and processing large datasets ranging from gigabytes to petabytes. Hadoop allows you to cluster multiple computers to analyze massive data sets in parallel, faster than using a single mainframe to store and process data.

It has two main components:

HDFS (Hadoop Distributed File System): This is Hadoop's file system, like the shelves in a warehouse, storing data in blocks across different servers. This way, even if a server fails, data is not lost because backups are available.

MapReduce: This is Hadoop's computational framework, like the warehouse's movers. It helps you retrieve data and process it according to your needs, such as counting the number of images or finding the number of occurrences of a word.

![alt text](07hadoop_1.png)
## YARN
YARN is a resource manager, which can be thought of as the "manager" of the warehouse. It manages the warehouse's resources, such as the server's CPU and memory. When someone (such as MapReduce/Spark) needs resources to process data, YARN allocates the appropriate servers and resources, ensuring that everyone can work smoothly and avoid competing for resources.
## Zookeeper
Zookeeper is like a "coordinator," primarily responsible for **coordinating communication and collaboration between components**. For example, when multiple servers are running Hadoop, Zookeeper helps them maintain mutual status, such as which server is working and which has failed. It also ensures data consistency, acting like a supervisor, ensuring that data is well synchronized across servers and avoids any confusion.
## Hive
Hive is a **data warehouse tool**, like a "librarian" in a warehouse. It helps you organize data according to certain rules, making it easy to quickly search and analyze. For example, you can use Hive to store data by date, type, and other categories, and then use SQL (a database query language) to query the data, such as "find all images uploaded on April 17, 2025." It makes data management and querying very convenient. ## Flink
`Flink` is a powerful stream processing engine, like a delivery driver. It's specifically designed to process real-time data streams, such as data from sensors and user clicks on websites. Flink can quickly process this data and provide real-time results. For example, it can count the number of hits per minute on a website or monitor the temperature of a device for abnormalities.
## Relationships

![alt text](<07learning summary.png>)

`Hadoop` is the foundation, providing storage (HDFS) and computation (MapReduce). Many other components run on Hadoop.

`YARN` is the resource manager, responsible for allocating resources to Hadoop's MapReduce, Flink, and other computational frameworks, ensuring their smooth operation.

`Zookeeper` is the coordinator, facilitating communication and coordination between components like Hadoop, Hive, and Flink, ensuring the proper functioning of the entire system.

Hive is a data warehouse tool built on Hadoop, leveraging Hadoop's storage and computing capabilities to facilitate data management and querying.

Flink is a standalone stream processing engine, but it can also integrate with Hadoop's storage system (HDFS) to read data from Hadoop and store processed results in Hadoop. Flink also relies on YARN for resource management and Zookeeper for coordination.