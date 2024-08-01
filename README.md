# PostGresSQL_101
Learn PGSQL basic concepts , uses and examples.

# Index

- [What is Postgres](#whatispostgres)
- Change Database Theme
- Create a Database
- Design a Database
- Turn Invoice into a Database
- Make a Table
- Data Types
- Adding Data to Table
- To See Data
- SELECT
- Create Custom Type
- Change Column Data Type
- Thinking About Tables
- Breaking Up Tables
-  Primary & Foreign Keys
- Foreign & Primary Keys
- Altering Tables Many Examples
- Getting Data from One Table
- Where
- Conditional Operators
- Logical Operators
58:12 Order By
59:32 Limit
1:01:45 GROUP BY
1:03:11 Distinct
1:05:00 Getting Data from Multiple Tables
1:05:21 Inner Join
1:08:50 Join 3 Tables
1:13:15  Arithmetic Operators
1:13:45 Join with Where
1:14:55 Outer Joins
1:17:03 Cross Joins
1:18:16 Unions
1:19:27 Extract
1:21:05 IS NULL
1:22:03 SIMILAR LIKE & ~ 
1:29:25 GROUP BY
1:31:14  HAVING
1:32:18  AGGREGATE FUNCTIONS
1:34:22 WORKING WITH VIEWS
1:45:01 SQL Functions
1:49:00 Dollar Quotes
1:50:06 Functions that Return Void
1:52:38 Get Maximum Product Price
1:53:39 Get Total Value of Inventory
1:54:26 Get Number of Customers
1:56:15 Named Parameters
2:01:30 Return a Row / Composite
2:03:38 Get Multiple Rows
2:07:08 PL/pgSQL
2:11:35 Variables in Functions
2:15:55 Store Rows in Variables
2:19:17 IN INOUT and OUT
2:21:01 Using Multiple Outs
2:25:56 Return Query Results
2:33:42 IF ELSEIF and ELSE
2:38:48  CASE Statement
2:42:01 Loop Statement
2:45:20 FOR LOOP
2:48:34 Result Sets, Blocks & Raise Notice
2:51:11 For Each and Arrays
2:53:20 While Loop
2:54:54 Continue
3:01:34 Stored Procedures
3:09:35 Triggers
3:29:25 Cursors
3:39:45 Installation

<a id="whatispostgres"></a>

# What is Postgres ?

Is a powerful, open-source relational database management system (RDBMS) that emphasizes extensibility and SQL compliance.

To start using `PostgreSQL`, you can install it on your local machine, set up a PostgreSQL server, and use client tools like `psql` (command-line interface) or graphical interfaces like `pgAdmin`. The official PostgreSQL documentation provides detailed installation guides and tutorials to help you get up and running.

### Key Features of PostgreSQL

1. **Open Source**: PostgreSQL is released under the PostgreSQL License, a permissive free software license. This means it is free to use, modify, and distribute.

2. **SQL Compliance**: PostgreSQL supports a substantial portion of the SQL standard and offers many modern features such as foreign keys, triggers, views, and stored procedures.

3. **Extensibility**: One of the standout features of PostgreSQL is its extensibility. You can define your own data types, operators, index types, and even functional languages to use in your queries.

4. **Advanced Data Types**: In addition to standard SQL data types, PostgreSQL supports advanced data types like arrays, hstore (key-value store), JSON/JSONB, XML, and geometric types.

5. **ACID Compliance**: PostgreSQL is fully ACID (Atomicity, Consistency, Isolation, Durability) compliant, ensuring reliable transactions and data integrity.

6. **Concurrency Control**: PostgreSQL uses Multi-Version Concurrency Control (MVCC) to handle concurrent transactions efficiently without requiring read locks.

7. **Full-Text Search**: Built-in support for full-text search, enabling efficient searching within text fields.

8. **Replication and Backup**: PostgreSQL supports various forms of replication (streaming replication, logical replication) and offers tools for robust backup and recovery (pg_dump, pg_basebackup).

9. **Indexing**: It offers a wide range of indexing techniques, including B-tree, hash, GiST, GIN, and BRIN indexes, which can significantly improve query performance.

10. **Community and Ecosystem**: PostgreSQL has a vibrant community and a rich ecosystem of tools, extensions, and third-party applications. Popular extensions include PostGIS for geographic data, pg_stat_statements for tracking query performance, and many more.

### Why Choose PostgreSQL?

- **Reliability and Stability**: PostgreSQL is known for its robustness and stability, making it a trusted choice for critical applications.
- **Performance**: With its advanced features and optimization capabilities, PostgreSQL can handle large-scale, high-transaction databases efficiently.
- **Flexibility**: Whether you need to handle simple relational data or complex, unstructured data, PostgreSQL's flexible data model can accommodate various needs.
- **Community Support**: The active and supportive PostgreSQL community provides extensive documentation, forums, and third-party resources to help you troubleshoot issues and learn new features.

### Use Cases for PostgreSQL

- **Web Applications**: Many web applications use PostgreSQL as their backend database due to its reliability and performance.
- **Data Warehousing**: PostgreSQL's powerful querying and indexing capabilities make it suitable for data warehousing and business intelligence applications.
- **Geospatial Data**: With the PostGIS extension, PostgreSQL becomes a powerful database for handling geographic information system (GIS) data.
- **Financial Systems**: Its ACID compliance and support for complex transactions make PostgreSQL a popular choice for financial applications.
