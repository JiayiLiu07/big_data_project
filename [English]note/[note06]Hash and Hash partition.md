# **Hash and Hash Partition**

### 1. **Hash**

Hashing is the process of converting data into a fixed-length value using an algorithm. This value is often called a "hash value" or "hash code."

- For example:

Suppose we have a set of names, such as "Zhang San," "Li Si," and "Wang Wu," and we want to quickly find them. We can use a simple hash algorithm, such as taking the pinyin initials of the first character in the name.

"Zhang San" → "Z"

"Li Si" → "L"

"Wang Wu" → "W"

These "Z," "L," and "W" are the hash values. This way, we can quickly locate each name.

### 2. **Hash Partition**

Hash partitioning is a data storage and management technique that divides data into partitions based on hash values. This improves data storage efficiency and query speed.

For example:

Suppose we have a database that stores a lot of user information, and we want to quickly find users by user ID. We can use a hashing algorithm to convert the user ID into a hash value, and then assign users to different partitions based on the hash value.

Suppose we have four partitions, and the hashing algorithm is to take the remainder of dividing the user ID by 4.

User ID is 1 → Hash value = 1 % 4 = 1 → Partition 1

User ID is 2 → Hash value = 2 % 4 = 2 → Partition 2

User ID is 3 → Hash value = 3 % 4 = 3 → Partition 3

User ID is 4 → Hash value = 4 % 4 = 0 → Partition 0

User ID is 5 → Hash value = 5 % 4 = 1 → Partition 1

Example:

User IDs: 1, 2, 3, 4, 5

Hash algorithm: User ID % 4

Partitions:

Partition 0: 4

Partition 1: 1, 5

Partition 2: 2

Partition 3: 3

Partitioning is based on a function of one or more columns in each record (the hash partition key). The hash partitioner examines one or more fields (the hash key fields) of each input record. All records with the same hash key field value are assigned to the same processing node. ![alt text](<06hash partition.png>)

### 3. **Reasons for using Hash Partitions?**
- Improved query efficiency: When we need to find a user, we only need to calculate their hash value to quickly locate the corresponding partition without searching the entire database.
- Load balancing: The hash algorithm evenly distributes data across partitions, preventing overcrowding in some partitions.
- Parallel processing: Each partition can perform independent operations, such as queries and updates, improving the system's concurrent processing capabilities.

4. **Hash Function**

A hash function is a mathematical function or algorithm that converts input data of arbitrary length (called a "message") into an output string of fixed length (called a "hash value" or "hash").