# SQL Note

![NoSQL Databases](/Screenshot%202022-09-01%20at%2018.24.55.png"Query NoSQL Databases")

- Since organizations frequently store data using multiple technologies, there is a need to unplug SQL from a particular database server and provide a service that can span multiple databases. For example, a report may need to bring together data stored in Oracle, Hadoop, JSON files, CSV files, and Unix log files. 

- A new generation of tools have been built to meet this type of challenge, and one of the most promising is <a href='https://drill.apache.org/'> Apache Drill</a>, which is an open source query engine that allows users to write queries that can access data stored in most any database or filesystem.


 My Note on SQL from beginner to Advance (MySQL)
  - <bold> Bullet point texts are critical ! <bold>

| Term  |  Definition |
|---|---|
| Entity  | Something of interest to the database user community. Examples include customers, parts, geographic locations, etc.  |
| Column |  An individual piece of data stored in a table. |
| Row  |  A set of columns that together completely describe an entity or some action on an entity. Also called a record. |
| Table |  A set of rows, held either in memory (nonpersistent) or on permanent storage (persistent).  |
| Result set  |  Another name for a nonpersistent table, generally the result of an SQL query. |
| Primary key | One or more columns that can be used as a unique identifier for each row in a table.  |
| Foreign key |  One or more columns that can be used together to identify a single row in another table. |

# SQL OPERATION IN 4 STEPS

## Step 1: Create a database

To create a new database, you would use the SQL schema statement create database database_name and set it as a default database to work with.<br />
`CREATE DATABASE COMPANY_DATA;`<br />
`USE COMPANY_DATA;`<br />

Likewise, to create a new table in your database, you would use the SQL schema statement create table, whereas the process of populating your new table with data would require the SQL data statement insert.

## Step 2: Create a table

Here’s an SQL schema statement that creates a table called corporation:<br />
    `CREATE TABLE corporation`<br/>
     `(corp_id SMALLINT,`<br />
      `name VARCHAR(30)`,<br />
      `CONSTRAINT pk_corporation PRIMARY KEY (corp_id));`<br />

The reason for `pk_corporation` is for deletion purpose of the primary key constraint on the corp_id column.
<br>
This statement creates a table with two columns, corp_id and name, with the corp_id column identified as the primary key for the table.

## Step 3: Insert data into the table

Next, here’s an SQL data statement that inserts a row into the corporation table for Acme Paper Corporation:<br />
    `INSERT INTO corporation (corp_id, name)`<br />
    `VALUES (1, 'Omar Paper Corporation'),`<br/>
    `(2, 'Tony Marcus Media House');`<br />

This statement adds a row to the corporation table with a value of 27 for the corp_id column and a value of Acme Paper Corporation for the name column.

## Step 4: Query the table and print out the results

Finally, here’s a simple select statement to retrieve the data that was just created:<br />
    `SELECT name`<br />
    `FROM corporation;`<br />

|corp_id    | name                      |
|-----|---                        |
|1  | Omar Paper Corporation   |
|2  | Tony Marcus Media House    |

Along with querying your database, you will most likely be involved with populating and modifying the data in your database. <br />
Here’s a simple example of how you would insert a new row into the product table:<br />
    `INSERT INTO corporation (corp_id, name)`<br />
    `VALUES (3, 'WayBoll Paper Corporation');`<br />  

Whoops, looks like you misspelled WayBill.” No problem. You can clean that up with an update statement:<br />
    `UPDATE product`<br />
    `SET name = 'WayBill Paper Corporation'`<br />
    `WHERE corp_id = 3;`<br />

- Data Dictionary are also generated for every SQL schema statements. Data dictionary is also known as Metadata and comes handy when you want to
query a database for the first time.
- Most SQL implementations treat any text between the /* and */ tags as comments.
- Whenever you execute an SQL data statement, you will receive feedback from the database engine as to how many rows were affected by your statement.
- It’s a good idea to check this info to make sure your state‐ ment didn’t do something unexpected (like when you forget to put a where clause on your delete statement and delete every row in the table!).
- Two of the most commonly used open source database servers are Post‐ greSQL and MySQL. The MySQL server is available for <a href='https://dev.mysql.com/downloads/'> free</a>, and I have found it to be extremely simple to download and install.
- Even if you are already using another server and never plan to use MySQL, I urge you to install the latest MySQL server, load the sample schema and data, and experiment with the data and examples in this note.

# SQL STATEMENTS 
- It's divided into 2, namely
    - SQL Schema Statements: Deals with structure of the database
        - CREATE, ALTER, DROP, RENAME,TRUNCATE
    - SQL Data Statements: Deals with the data stored in the table of a database
        - SELECT, UPDATE, DELETE, TRUNCATE, INSERT, GRANT, REVOKE, COMMIT, ROLLBACK