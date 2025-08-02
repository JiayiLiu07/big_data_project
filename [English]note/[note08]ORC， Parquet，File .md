# Data Storage Formats: ORC, Parquet, and Common File Formats (e.g., CSV, JSON, etc.)
>https://www.imooc.com/article/360115
## -----↓Optimized Version↓-----
## CSV (Comma-Separated Values)

### Why it came into being:
- An old file format, it's been around since the dawn of computing.
- Goal: To store and exchange tabular data in a simple, universal way.

### What Problems Does It Solve:
- `Data Exchange`: Facilitates the exchange of tabular data between different systems and applications.
- `Small Dataset Processing`: Suitable for fast reading and writing of small datasets.

### What Problems Does It Encounter:
- `Unable to Store Complex Data Structures`: Limited to simple tables, does not support hierarchies or key-value pairs.
- `Difficulty Handling Special Characters`: For example, commas themselves require additional escaping.
- `No Data Type Support`: Does not store type information; type information must be specified manually.
- Unsuitable for large-scale data: **Row-oriented**, resulting in slow queries and relatively large file sizes.

## JSON (JavaScript Object Notation)

### Why it emerged:
- To meet the needs of data exchange in the **internet era**.
- Web applications require a **lightweight, human-readable and easy-to-write format, as well as machine-parseable and easy-to-generate**. JSON is text-based, making it easy to read and write, as well as machine-parseable and easy-to-generate.

### What problems does it solve:
- Data exchange: Convenient for exchanging data objects, **supporting complex data structures** (nested key-value pairs, arrays).
- Flexibility: Easy to add and delete fields, suitable for dynamic data structures.

### What problems does it encounter:
- Slow reading: **Row-oriented**, queries require reading row by row, making it unsuitable for fast queries on large-scale data.
- Large file size: Relatively verbose structures, typically larger than CSV and Parquet.
- Schema validation is not supported: Schema validation cannot be validated, potentially leading to data inconsistencies.

## Parquet

### Why it emerged:
- With the development of big data technology, traditional row-oriented formats (CSV, JSON) have encountered performance bottlenecks.
- Goal: Improve the efficiency of large-scale data processing and reduce storage costs.

### What problems does it solve:
- Improving query efficiency: Using columnar storage, it quickly reads specific columns and significantly reduces the data scan range.
- Compression and storage optimization: Supports efficient compression and multiple encodings, reducing size and optimizing read and write operations.
- Support for complex data structures: It can store nested data structures.

### What problems does it encounter?
- Requires specialized knowledge: It cannot be opened with ordinary text editors and requires specialized tools/languages (such as Apache Spark and Apache Hadoop).
- Limited community support: It is primarily available within the Apache Spark and Apache Hadoop ecosystems, with limited external support.

## ORC (Optimized Row Columnar)

### Why it exists:
- Further optimizes **write performance** and **transaction support** in big data processing.

### What problems does it solve:
- Write performance optimization: Suitable for **write-intensive tasks**, efficiently handling large-scale data writes.
- ACID transaction support: Supports **ACID transactions** (updates, deletes, and merges) in Apache Hive.
- The ORC format has built-in transaction support mechanisms:
- Delta Files: When data changes, Hive does not directly modify the original ORC file. Instead, it creates special "delta files" in the table directory. These files record the insert, update, or delete change events.
- Read-Time Merge: When querying data, the Hive engine reads the baseline data file and applies changes in real time based on these delta files, presenting an up-to-date, consistent view of the data. - Compaction: To prevent query performance degradation caused by excessive delta files (each query requires merging numerous small files), Hive's background process periodically merges these delta files with the baseline data files to generate new, more compact ORC files.
- ACID is a set of properties in database transaction management that aims to ensure transaction reliability and data integrity.
- A - Atomicity - Either everything happens or nothing happens.
- C - Consistency - Data rules must be maintained.
- I - Isolation - Multiple transactions do not interfere with each other.
- D - Durability - Once committed, data cannot be lost.
- Excellent Performance: Provides efficient read and write performance for large-scale data processing.

### What are its inherent challenges?
- Weak Community Support: Compared to Parquet, it has weaker community support.
- Community support refers to the help, resources, and activity provided by the community of developers, users, and contributors surrounding a technology, software, or project (such as the ORC or Parquet file formats).
- Weak community support means: It's harder to quickly find ready-made solutions when problems arise. Related learning resources (e.g., blogs) may not be as abundant or up-to-date as those for Parquet. Support for ORC in certain programming languages or tools may not be as mature or comprehensive as that for Parquet. The developer and active user community surrounding ORC is relatively small, leading to less active discussions and contributions.
- Limited applicability: Primarily used in the Apache Hive and Hadoop ecosystems, with limited support for other platforms.

## -----↓ Original Notes (Too Shallow)↓-----
### 1. ORC File Format

- **ORC's Approach**: It reorganizes the information in the book, placing everyone's age in one place, everyone's name in another, and everyone's address in a third. This way, if you want to calculate the average age, you can simply look in the dedicated age section without having to flip through each page.

- **Pros**: Data search is extremely fast, especially when you only need to look at specific information (such as age or income). It also compresses the data, making the book thinner and saving space.

- **Cons**: This format is relatively complex, and not all tools can directly read it. It is mainly used in big data analysis scenarios.

### 2. Parquet File Format

- **Parquet's Approach**: It's like a standardized Lego set, with all the blocks designed with a uniform shape and interface. This makes it easy to assemble regardless of the tool you use (such as different big data processing software).

- **Pros**: It's somewhat similar to ORC, storing data in columns, making data search fast and compressing. But it also has a special advantage—it's designed as a "universal format" that can be used by almost all big data tools, just like Lego blocks, making it universally applicable.

- **Cons**: Like ORC, it's relatively complex and not suitable for simple scenarios.

### 3. CSV File Format

- **CSV Approach**: It's like a simple paper spreadsheet, with commas (or other symbols) separating each column of information. For example, "John, 25, New York" is a row of data.

- **Pros**: It's very simple and easy for anyone to understand. It can be opened with a regular text editor. Almost all tools can handle this format, just like a paper spreadsheet.

- **Cons**: Because it's so simple, without compression or optimization, it can be slow to find data, especially when the data is large.

### 4. JSON File Format

- **JSON Approach**: It organizes information into a "card story" format. Each piece of information has a name (such as "name," "age," or "address"), and is enclosed in curly braces {}. For example: { "name": "John", "age": 25, "address": "New York" }.

- **Pros**: This format is flexible and can represent complex information (such as nested stories). It's also very readable and pleasing to humans.

- **Disadvantages**: It lacks compression, so it takes up more space when the data volume is large. Furthermore, data retrieval isn't as fast as ORC and Parquet.

### Comparing ORC and Parquet
- **Similarities**:
- Both use columnar storage;
- Both support data compression;
- Both support complex data types
- **Differences**: ORC has built-in indexing, while Parquet does not.

- **Summary**:
1. ORC: Like an "efficient but specialized" storage container, it offers fast read speeds and high storage efficiency, but is primarily used within the Hadoop ecosystem.
2. Parquet: Like a "flexible and versatile" storage container, it offers fast write speeds and excellent compatibility, making it suitable for a variety of big data tools.

| Features | ORC | Parquet | CSV | JSON |
| --- | --- | --- | --- | --- |
| Storage | Column-based storage | Column-based storage | Row-based storage | Nested structures |
| Compression support | Supports multiple compression algorithms | Supports multiple compression algorithms | Generally not compressed | Generally not compressed |
| Encoding technology | Dictionary encoding, RLE, etc. | Dictionary encoding, Delta encoding, etc. | None | None |
| Data type support | Supports complex data types | Supports complex data types | No data type information | Supports complex nested data types |
| Compatibility | Primarily used in the Hadoop ecosystem | Cross-platform compatibility | Highly versatile | Highly versatile |
| Applicable scenarios | Data warehouse analysis | Data exchange, data lake | Data import and export | Web data exchange, complex nested data storage |