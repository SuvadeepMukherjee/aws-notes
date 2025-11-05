# DynamoDB

**Q1**:What kind of database is DynamoDB - relational or non-relational ? 

**Solution**:

- DynamoDB is a NoSQL database 

**Q2**:What kind of data models does DynamoDB support ? 

**Solution**:

- DynamoDB supports both document and key-value data models

**Q3**:What is the primary key in DynamoDB and what are its 2 possible types ? 

**Solution**:

The primary key uniquely identifies each item in a table and it can be of 2 types 

- Partition Key (simple primary key) - a single attribute 
- Partition key + Sort key (composite primary key) - two attributes used together to organise data 

**Q4**:What is the role of the partition key in DynamoDBs internal architecture ? 

**Solution**:

partition key decides which physical partition our item is stored in

**Q5**:What is sort key used for in a DynamoDB table that has a composite primary key ? 

**Solution**:

 sort key determines the order of items within the same partition

**Q6**:What are RCU and WCU in DynamoDB ? 

**Solution**:

**RCU (Read Capacity Unit):** 1 RCU = one *strongly consistent read* per second for items up to 4 KB, or two *eventually consistent reads* per second for items up to 4 KB.
**WCU (Write Capacity Unit):** 1 WCU = one *write per second* for items up to 1 KB.

**Q7**:**What’s the difference between provisioned capacity mode and on-demand capacity mode in DynamoDB?**

**Solution**:

**Provisioned capacity mode:** You manually specify how many RCUs and WCUs you want. DynamoDB allocates that capacity and charges you whether you use it fully or not. It’s useful when your traffic is predictable.
**On-demand capacity mode:** You don’t set any capacity in advance. DynamoDB automatically scales to handle requests and you pay per request — great for unpredictable workloads.

**Q8**:**What is a Global Secondary Index (GSI) in DynamoDB used for?**

**Solution**:

A **Global Secondary Index (GSI)** lets you **query your data using an alternate key** instead of the table’s primary key. You define a **different partition key (and optionally a sort key) for the index.** DynamoDB then maintains a copy of that data internally, so you can efficiently query by those new attributes.

**Q9**:What's the difference between a Global Secondary Index (GSI) and a Local Secondary Index (LSI) ? 

**Solution**:

|                        | key                                                          | When is created                                              |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Global Secondary Index | can have a different partition key from the main table       | can be created anytime even after the table already exists   |
| Local Secondary Index  | Uses the same partition key as the main table but a different sort key | Must be defined when creating the table (can't be added later) |

**Q10**:What is a dynamoDB stream ? 

**Solution**:

A **DynamoDB Stream** is like a change log for your table. Whenever an item is **inserted, updated, or deleted**, DynamoDB can capture that event and store it in a stream.

You can then connect that stream to AWS services like **Lambda** — for example, to automatically trigger a function whenever a table changes.
 It’s great for **real-time processing**, **replication**, or **audit trails**.

**Q11**:**What’s the purpose of the PutItem operation in DynamoDB ?** 

**Solution**:

The **PutItem** operation in DynamoDB is used to **create a new item** or **replace an existing one** in a table.

If an item with the same primary key already exists, PutItem will overwrite it (unless you add a condition to prevent that).

**Q12**:**What’s the difference between the** **GetItem** **and** **Query** **operations in DynamoDB?**

**Solution**:

**GetItem**: Fetches **a single item** using its **exact primary key** (partition key and optionally sort key). It’s like asking, “Give me the record with userId = 123.”

**Query**: Finds **multiple items** that share the **same partition key**, and optionally filters them by sort key or other attributes.

**Q13**:**What’s the difference between a Query and a Scan operation in DynamoDB?**

**Solution**:

A Query is selective — it looks for items that match a specific partition key (and optional filters).

A Scan reads every item in the table, which can be slow and expensive for large datasets.

**Q14**:What is eventual consistency in DynamoDB reads ? 

**Solution**:

**Eventual consistency** means that when you write new data, it might **take a short time** before all copies of that data across different storage nodes are updated.
 So, if you immediately read after a write, you *might* get the old value — but eventually, all reads will return the latest data.

In contrast, **strongly consistent reads** always return the latest data, but they’re a bit slower and cost double in RCU terms.

**Q15**:What kind of data types can dynamoDB attributes have ? 

**Solution**:

- **Scalar types** – single values like
  - String (S), Number (N), Binary (B), Boolean (BOOL), and Null (NULL).
- **Document types** – structured values:
  - Map (M) and List (L).
- **Set types** – collections of unique scalar values:

String Set (SS), Number Set (NS), Binary Set 

 **Q16**:What is the purpose of AWS SDK or CLI when working with DynamoDB ? 

**Solution**:

The **AWS SDK (Software Development Kit)** and **AWS CLI (Command Line Interface)** are tools that let you **interact with DynamoDB programmatically**.

- With the **SDK**, you can write code (for example, in Node.js or Python) to create tables, read or write items, and perform queries directly from your application.

With the **CLI**, you can run DynamoDB commands from your terminal without writing any code — useful for testing, scripting, or managing resources quickly.

**Q17**:**What is the difference between a table , an item and an attribute in DynamoDB?** 

**Solution**:

- **Table** → the container for all data.
- **Item** → one record (like a row).
- **Attribute** → a single data field (like a column).

DynamoDB tables don’t require all items to have the same attributes — it’s **schema-less**, which is a key difference from relational tables.

**Q18**:**What’s the maximum size of a single item in DynamoDB?**

**Solution**:

The **maximum size of a single item** in DynamoDB is **400 KB**, including all its attribute names and values.That’s why large data (like images or big JSON blobs) is usually stored in **S3**, and only a reference (like a URL) is kept in DynamoDB.

**Q19**:**What is TTL (Time to Live) in DynamoDB, and what does it do?**

**Solution**:

**TTL (Time to Live)** is an optional feature that automatically deletes items after a specified timestamp.

You define a **TTL attribute** (a UNIX epoch time in seconds), and when that time passes, DynamoDB automatically removes the item — great for cleaning up old sessions, logs, or temporary data.

**Q20**:**Comparison of DynamoDB over other NoSQL databases like MongoDB**

**Solution**:

- **Set-up**
  - Setting up DynamoDB is **easier** **compared to MongoDB**
- **Security**
  - Security for DynamoDB is governed by **AWS Identity and Access Management(IAM)** which makes it **more secure than MongoDB**
- **Cost**
  - Both DynamoDB and MongoDB are **free** for a pre-defined period of time.After free usage expires , **DynamoDB calculates cost on the basis of reads and writes** , while **MongoDB calculates cost according to consumed storage** 