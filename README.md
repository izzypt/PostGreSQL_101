# PostGresSQL_101
Learn PGSQL basic concepts , uses and examples.

# Index

- [What is Postgres](#whatispostgres)
- [Change Database to Dark Theme](#darktheme)
- [PostGreSQL server](#psqlserver)
- [What are Schemas and Owners](#schemasandowners)
- [Connecting to a Database](#connecting)
- [Create a Database](#createDB)
- [Database Objects](#DBObjects)
- [Design a Database](#designdb)
- [Make a Table](#createtable)
- [Data Types](#datatypes)
- [Adding Data to Table](#datatotable)
- [To See Data](#seedata)
- [Create Custom Type](#customtype)
- [Change Column Data Type](#changecolumndatatype)
- Thinking About Tables
- Breaking Up Tables
-  Primary & Foreign Keys
- Foreign & Primary Keys
- Altering Tables Many Examples
- Getting Data from One Table
- Where
- Conditional Operators
- Logical Operators
- Order By
- Limit
- GROUP BY
- Distinct
- Getting Data from Multiple Tables
- Inner Join
- Join 3 Tables
-  Arithmetic Operators
- Join with Where
- Outer Joins
- Cross Joins
- Unions
- Extract
- IS NULL
- SIMILAR LIKE & ~ 
- GROUP BY
-  HAVING
- AGGREGATE FUNCTIONS
- WORKING WITH VIEWS
- SQL Functions
- Dollar Quotes
- Functions that Return Void
- Get Maximum Product Price
- Get Total Value of Inventory
- Get Number of Customers
- Named Parameters
- Return a Row / Composite
- Get Multiple Rows
- PL/pgSQL
- Variables in Functions
- Store Rows in Variables
- IN INOUT and OUT
- Using Multiple Outs
- Return Query Results
- IF ELSEIF and ELSE
-  CASE Statement
- Loop Statement
- FOR LOOP
- Result Sets, Blocks & Raise Notice
- For Each and Arrays
- While Loop
- Continue
- Stored Procedures
- Triggers
- Cursors
- Installation

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

<a id="darktheme"></a>

# Change Database to Dark theme

In `pgAdmin`:

- File -> Preferences -> Miscellaneous -> Themes -> Theme -> Dark


<a id="psqlserver"></a>

# PostGreSQL server

### PostgreSQL Server Hierarchy

1. **PostgreSQL Server**: This is the top-level instance that manages everything. It can run on a physical or virtual machine and can host multiple databases. When you install PostgreSQL, you are setting up this server.

2. **Databases**: Each PostgreSQL server can contain multiple databases. Databases are separate from each other, and each one can hold its own set of schemas and data. 

3. **Schemas**: Within each database, there can be multiple schemas. Schemas help organize database objects like tables, views, functions, etc.

4. **Database Objects**: These include tables, views, indexes, sequences, functions, and more, which reside within schemas.

### Connecting to PostgreSQL

- **Client Connection**: Clients connect to the PostgreSQL server using client software (e.g., `psql`, PgAdmin, applications using database drivers). The connection is typically made to a specific database on the server.

### Example of a Typical Setup

1. **PostgreSQL Server**: Runs on a machine with an IP address and a port (default is 5432).
2. **Databases on the Server**:
   - `database1`
   - `database2`
3. **Schemas within `database1`**:
   - `public` (default schema)
   - `schema1`
4. **Tables within `schema1` in `database1`**:
   - `table1`
   - `table2`

### Connecting to the Server

1. **Server Connection**: Connect to the PostgreSQL server using an IP address or hostname and port number.
2. **Database Selection**: Specify which database you want to connect to on that server.

### Example Commands

1. **Starting the PostgreSQL Server**:
   - Typically, the server starts automatically, but it can also be started manually with:
     ```bash
     pg_ctl start -D /path/to/data_directory
     ```

2. **Connecting to the Server and a Specific Database**:
   - Using `psql`:
     ```bash
     psql -h localhost -p 5432 -U username -d database1
     ```
     Here:
     - `-h localhost` specifies the host (local machine in this case).
     - `-p 5432` specifies the port number.
     - `-U username` specifies the username.
     - `-d database1` specifies the database to connect to.

### Visual Representation

Here's a simplified visual representation:

```
PostgreSQL Server (IP: localhost, Port: 5432)
  ├── Database: database1
  │     ├── Schema: public
  │     │     ├── Table: table1
  │     │     └── Table: table2
  │     └── Schema: schema1
  │           ├── Table: table3
  │           └── Function: function1
  ├── Database: database2
        └── Schema: public
              ├── Table: table4
              └── View: view1
```

### Summary

- **PostgreSQL Server**: The top-level instance managing all databases.
- **Databases**: Multiple databases can exist within a single PostgreSQL server.
- **Schemas**: Each database can have multiple schemas for organizing objects.
- **Client Connections**: Clients connect to the server and specify which database to use.

<a id="schemasandowners"></a>

# What are Schemas and Owners

### **Schemas**
Think of a **schema** like a bookshelf in a library. In a library, there are many bookshelves, and each one holds a collection of books that belong together. For example, one bookshelf might have all the science books, another has storybooks, and another has history books. 

In PostgreSQL, a schema is like that bookshelf. It helps keep all the database objects (like tables and other things) organized. So, instead of all the books (or database objects) being mixed up, they are neatly placed in different sections (schemas).

### **Owners**
Now, let's talk about **owners**. Imagine that every bookshelf in the library has a librarian who takes care of it. This librarian makes sure that the books are in order, decides who can borrow the books, and who can put new books on the shelf. 

In PostgreSQL, the owner is like that librarian. The owner of a schema or table is the person (or role) who has full control over it. They can decide who gets to see or use the data and who can add new data.

### Importance
- **Schemas (Bookshelves)**: Keep everything organized. Just like you wouldn't want storybooks mixed in with science books, schemas keep different parts of the database neat and easy to find.
- **Owners (Librarians)**: Make sure everything is taken care of properly. They decide who can see and use the data, just like a librarian decides who can borrow which books.

### Example
Let's say we have a school library. We could have:

- **Schema (Bookshelf) for Science**: All science tables (books) go here.
- **Schema (Bookshelf) for Stories**: All story tables (books) go here.

Each bookshelf has its own librarian:
- **Owner (Librarian) for Science**: Mrs. Smith takes care of the science bookshelf.
- **Owner (Librarian) for Stories**: Mr. Brown takes care of the story bookshelf.

Mrs. Smith and Mr. Brown make sure the books (tables) are well-organized and decide who can read them.

By having schemas and owners, PostgreSQL keeps everything tidy and well-managed, just like a well-run library.

In PostgreSQL, it is the database (DB) that holds multiple schemas, not the other way around. Here's how it works:

### Database and Schemas Relationship

- **Database (DB)**: This is the top-level container. A PostgreSQL server can manage multiple databases.
- **Schemas**: These are organizational units within a single database. Each schema can contain multiple tables, views, functions, and other database objects.

### Visual Representation

Think of it like this:

```
PostgreSQL Server
  ├── Database 1
  │     ├── Schema A
  │     │     ├── Table 1
  │     │     ├── Table 2
  │     │     └── Function 1
  │     └── Schema B
  │           ├── Table 3
  │           └── View 1
  ├── Database 2
  │     ├── Schema C
  │     └── Schema D
  └── Database 3
        └── Schema E
```

### Example Explanation

- **PostgreSQL Server**: The server can have many databases.
- **Database 1**: Contains Schema A and Schema B.
- **Schema A**: Contains Table 1, Table 2, and Function 1.
- **Schema B**: Contains Table 3 and View 1.
- **Database 2**: Contains Schema C and Schema D.
- **Database 3**: Contains Schema E.

### Key Points

- **A schema is part of a single database**.
- **A database can have multiple schemas**.
- **Each schema can have multiple database objects (tables, views, etc.)**.

### Creating Databases and Schemas

Here's how you create databases and schemas in PostgreSQL:

1. **Create a Database**
   ```sql
   CREATE DATABASE library;
   ```

   This command creates a new database named `library`.

2. **Connect to the Database**
   ```sql
   \c library
   ```

   This command connects to the `library` database. In SQL client tools like `psql`, this is how you switch to a different database.

3. **Create Schemas in the Database**
   ```sql
   CREATE SCHEMA science;
   CREATE SCHEMA stories;
   ```

   These commands create two schemas named `science` and `stories` within the `library` database.

### Summary

- **A PostgreSQL server** can have multiple databases.
- **Each database** can contain multiple schemas.
- **Each schema** can contain multiple database objects like tables, views, and functions.


<a id="connecting"></a>

# Connecting to a DB

To connect to a PostgreSQL database, you typically need several key pieces of information. Here’s a breakdown of the essential requirements:

### Essential Requirements for Connecting to a PostgreSQL Database

1. **Host**:
   - The hostname or IP address of the server where the PostgreSQL instance is running. If the server is on the same machine you are connecting from, you can use `localhost`.

2. **Port**:
   - The port number on which the PostgreSQL server is listening for connections. The default port is `5432`.

3. **Database Name**:
   - The name of the specific database you want to connect to within the PostgreSQL server.

4. **User**:
   - The username of the PostgreSQL role that you are using to connect. This role must have the appropriate permissions to access the database.

5. **Password**:
   - The password associated with the user/role, if password authentication is required.

### Additional Optional Requirements

1. **SSL Mode**:
   - Specifies whether to use SSL for the connection and what level of validation to perform. Options include `disable`, `allow`, `prefer`, `require`, `verify-ca`, and `verify-full`.

2. **Client Encoding**:
   - Specifies the character set encoding to use for the connection.

### Example Connection Strings

#### Using `psql` Command-Line Tool

```bash
psql -h localhost -p 5432 -U myuser -d mydatabase
```

- `-h localhost`: Specifies the host.
- `-p 5432`: Specifies the port.
- `-U myuser`: Specifies the user.
- `-d mydatabase`: Specifies the database name.

The tool will prompt for the password unless provided in a secure way (e.g., a `.pgpass` file).

#### Using a Connection String in a Programming Language (e.g., Python with `psycopg2`)

```python
import psycopg2

connection = psycopg2.connect(
    host="localhost",
    port=5432,
    user="myuser",
    password="mypassword",
    dbname="mydatabase"
)

cursor = connection.cursor()
cursor.execute("SELECT version();")
print(cursor.fetchone())
connection.close()
```

- `host="localhost"`: Specifies the host.
- `port=5432`: Specifies the port.
- `user="myuser"`: Specifies the user.
- `password="mypassword"`: Specifies the password.
- `dbname="mydatabase"`: Specifies the database name.

### Summary of Connection Requirements

1. **Host**: The server address (e.g., `localhost` or an IP address).
2. **Port**: The server port (default is `5432`).
3. **Database Name**: The name of the database you want to connect to.
4. **User**: The username for authentication.
5. **Password**: The password for authentication.
6. **SSL Mode** (Optional): For secure connections.
7. **Client Encoding** (Optional): For character set encoding.

By providing these details, you can establish a connection to a PostgreSQL database from various clients and programming environments.

<a id="createDB"></a>

# Create a Database

- Servers -> PostgreSQL -> Databases (right click) -> Create -> Database

- <img width="1626" alt="image" src="https://github.com/user-attachments/assets/78e85642-8b37-45c8-b9e5-866076188ace">

When you start creating a DB, you need to: 

- Make sure 1 table only represent 1 real world object, for example: 
  - customers
  - orders
  - sales

- Columns are going to store only 1 piece of information, like:
  - name
  - address
  - state
 
- How do different tables relate?
  - If we have a sales order we are going to need to relate our customer table to the sales table.

<a id="DBObjects"></a>

# Database Objects

### Database Objects Include:

1. **Tables**: Store data in rows and columns.
2. **Indexes**: Improve query performance.
3. **Views**: Simplify complex queries.
4. **Sequences**: Generate unique values.
5. **Functions**: Perform operations and return results.
6. **Triggers**: Execute procedures automatically on specific events.
7. **Constraints**: Ensure data integrity.
8. **Types**: Define custom data types.
9. **Schemas**: Organize database objects within a database.
10. **Extensions**: Add additional functionality.

1. **Tables**: The primary storage objects for data. Tables are structured with rows and columns.
   - Example:
     ```sql
     CREATE TABLE employees (
         id SERIAL PRIMARY KEY,
         name VARCHAR(100) NOT NULL,
         position VARCHAR(50),
         salary NUMERIC CHECK (salary > 0)
     );
     ```

2. **Indexes**: Used to speed up the retrieval of rows by creating quick lookup references for table data.
   - Example:
     ```sql
     CREATE INDEX idx_employees_name ON employees (name);
     ```

3. **Views**: Virtual tables that are based on the result of a SELECT query. They simplify complex queries and provide a level of abstraction.
   - Example:
     ```sql
     CREATE VIEW high_salary_employees AS
     SELECT name, salary
     FROM employees
     WHERE salary > 50000;
     ```

4. **Sequences**: Objects that generate unique numeric values, often used for auto-incrementing primary keys.
   - Example:
     ```sql
     CREATE SEQUENCE employee_id_seq
     START WITH 1
     INCREMENT BY 1;
     ```

5. **Functions**: Stored procedures that perform operations and return a result. They can be written in various languages, including SQL, PL/pgSQL, and others.
   - Example:
     ```sql
     CREATE FUNCTION get_employee_count() RETURNS INTEGER AS $$
     BEGIN
         RETURN (SELECT COUNT(*) FROM employees);
     END;
     $$ LANGUAGE plpgsql;
     ```

6. **Triggers**: Procedures that are automatically executed in response to certain events on a table or view, such as INSERT, UPDATE, or DELETE.
   - Example:
     ```sql
     CREATE TRIGGER update_timestamp
     BEFORE UPDATE ON employees
     FOR EACH ROW
     EXECUTE FUNCTION update_modified_column();
     ```

7. **Constraints**: Rules enforced on table columns to ensure data integrity. These include PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK, and NOT NULL constraints.
   - Example:
     ```sql
     ALTER TABLE employees ADD CONSTRAINT unique_name UNIQUE (name);
     ```

8. **Types**: Custom data types that can be defined to extend PostgreSQL's built-in types.
   - Example:
     ```sql
     CREATE TYPE mood AS ENUM ('happy', 'sad', 'neutral');
     ```

9. **Schemas**: As mentioned, schemas themselves are also objects that help organize the above objects within a database.
   - Example:
     ```sql
     CREATE SCHEMA hr;
     ```

10. **Extensions**: Packages that add additional functionality to PostgreSQL. Common extensions include PostGIS (for geographic objects) and pg_trgm (for text search and similarity).
    - Example:
      ```sql
      CREATE EXTENSION IF NOT EXISTS postgis;
      ```

<a id="createtable"></a>

# Create a Table

Go into the `Query`tool and 

```
CREATE TABLE customer(
first_name VARCHAR(30) NOT NULL,
last_name VARCHAR(30) NOT NULL,
email VARCHAR(60) NOT NULL,
company VARCHAR(60) NOT NULL,
street VARCHAR(50) NOT NULL,
city VARCHAR(40) NOT NULL,
state CHAR(2) NOT NULL,
zipcode SMALLINT NOT NULL,
phone VARCHAR(20) NOT NULL,
birth_data DATE NULL,
sex CHAR(1) NOT NULL,
date_entered TIMESTAMP NOT NULL,
id SERIAL PRIMARY KEY
)

```

<img width="1687" alt="image" src="https://github.com/user-attachments/assets/85c09c51-f92f-4427-8bc2-cb0cfd550dbd">


It should appear under your dbname-> Schemas -> Tables -> tableName (customer)

Let's create  asecond table for the sales person:

<img width="1706" alt="image" src="https://github.com/user-attachments/assets/7eb9e7f7-c80d-488a-9e20-adb0ceacd439">


<a id="datatypes"></a>
# Data Types

### Numeric Types
- **SMALLINT**: Small-range integer
- **INTEGER**: Standard integer
- **BIGINT**: Large-range integer
- **DECIMAL**: Exact numeric with user-defined precision
- **NUMERIC**: Exact numeric with user-defined precision
- **REAL**: Single precision floating-point number
- **DOUBLE PRECISION**: Double precision floating-point number
- **SERIAL**: Auto-incrementing integer
- **BIGSERIAL**: Auto-incrementing large integer

### Character Types
- **CHAR(N)**: Fixed-length character string
- **VARCHAR(N)**: Variable-length character string
- **TEXT**: Variable-length character string with no length limit

### Binary Data Types
- **BYTEA**: Binary data ("byte array")

### Date/Time Types
- **DATE**: Calendar date (year, month, day)
- **TIME**: Time of day (without time zone)
- **TIME WITH TIME ZONE**: Time of day (with time zone)
- **TIMESTAMP**: Date and time (without time zone)
- **TIMESTAMP WITH TIME ZONE**: Date and time (with time zone)
- **INTERVAL**: Time span

### Boolean Type
- **BOOLEAN**: Boolean value (true/false)

### Enumerated Type
- **ENUM**: Enumeration of predefined values

### Geometric Types
- **POINT**: Geometric point
- **LINE**: Infinite line
- **LSEG**: Line segment
- **BOX**: Rectangular box
- **PATH**: Geometric path (open or closed)
- **POLYGON**: Closed geometric path
- **CIRCLE**: Circle

### Network Address Types
- **CIDR**: IPv4 or IPv6 network
- **INET**: IPv4 or IPv6 host address
- **MACADDR**: MAC address

### Bit String Types
- **BIT(N)**: Fixed-length bit string
- **VARBIT(N)**: Variable-length bit string

### Text Search Types
- **TSVECTOR**: Text search vector
- **TSQUERY**: Text search query

### UUID Type
- **UUID**: Universally unique identifier

### JSON Types
- **JSON**: Textual JSON data
- **JSONB**: Binary JSON data, optimized for storage and querying

### Arrays
- **ARRAY**: Array of any data type

### Composite Types
- **Composite Types**: Custom user-defined composite types

### Range Types
- **INT4RANGE**: Range of integers
- **INT8RANGE**: Range of big integers
- **NUMRANGE**: Range of numerics
- **TSRANGE**: Range of timestamps without time zone
- **TSTZRANGE**: Range of timestamps with time zone
- **DATERANGE**: Range of dates


<a id="datatotable"></a>

# Adding data to Table

<img width="1673" alt="image" src="https://github.com/user-attachments/assets/075d886b-e1e7-4380-8fda-0108b14824b2">

<a id="seedata"></a>

# To see data

![image](https://github.com/user-attachments/assets/f515a723-84c0-43f1-8ece-7f146432a25c)

<a id="customtype"></a>

# Create Custom Type

<img width="1704" alt="image" src="https://github.com/user-attachments/assets/37c94174-e939-4df5-bcfe-57465502c318">

<a id="changecolumndatatype"></a>

# Change Column Data Type

<img width="1604" alt="image" src="https://github.com/user-attachments/assets/e76e765e-cfdb-47ad-a787-3cd4e14a6055">
