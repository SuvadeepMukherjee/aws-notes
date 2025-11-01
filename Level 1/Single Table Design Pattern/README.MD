# Single Table Design Pattern

**Q1**:What is data modelling ? 

**Solution**:

- strategy used to structure and organise data in a DB 

**Q2**:What is an entity in the context of DB ? 

**Solution**:

-  distinct object like a user our application needs to store data about

**Q3**:What is Composite Primary Key in Single Table Design Pattern ? 

**Solution**:

Partion_key ➡️ 

- Main key that determines where an item is stored 
- all items  with the same partiotion key are grouped together 

Sort_key ➡️

- defines how items within the same partition are ordered letting us query related data efficiently

Together they form a Composite Primary Key ➡️ `primary_key` + `sort_key`

**Q4**:What is the Single Table Design Pattern ? 

**Solution**:

- Data modelling approach used in Amazon DynamoDB 
- instead of creating multiple tables for different entities all related data is stored in a single table using composite primary keys (primary_key + sort_key)

**Q4**:Key features of Single Table Design Pattern 

**Solution**:

- Because all data lives in one table DynamoDB can scale horizontally 
- We design one flexible table simplifying database management

**Q5**:Common use cases of Single Table Design Pattern 

**Solutiobn**:

- Multiple microservices can query and update the same table immediately 
- APIs that require fetching multiple related items in one request (like a user and all their orders) benefit from this pattern

 