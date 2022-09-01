# SQL Note
 My reading note for beginner to Advance SQL

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
To create a new database, you would use the SQL schema statement create database database_name and set it as a default database to work with.
CREATE DATABASE COMPANY_DATA;<br />
USE COMPANY_DATA;<br />

Likewise, to create a new table in your database, you would use the SQL schema statement create table, whereas the process of populating your new table with data would require the SQL data statement insert.

## Step 2: Create a table
Here’s an SQL schema statement that creates a table called corporation:
    CREATE TABLE corporation<br/>
     (corp_id SMALLINT,<br />
      name VARCHAR(30),<br />
      CONSTRAINT pk_corporation PRIMARY KEY (corp_id)<br />
     ); <br />
The reason for `pk_corporation` is for deletion purpose of the primary key constraint on the corp_id column.
<br>
This statement creates a table with two columns, corp_id and name, with the corp_id column identified as the primary key for the table.

## Step 3: Insert data into the table
Next, here’s an SQL data statement that inserts a row into the corporation table for Acme Paper Corporation:<br />
    INSERT INTO corporation (corp_id, name)<br />
    VALUES (27, 'Acme Paper Corporation');<br />

This statement adds a row to the corporation table with a value of 27 for the corp_id column and a value of Acme Paper Corporation for the name column.

## Step 4: Query the table and print out the results.
Finally, here’s a simple select statement to retrieve the data that was just created:<br />
    SELECT name<br />
    FROM corporation<br />
    WHERE corp_id = 27;<br />
    +------------------------+
    | name                   |
    +------------------------+
    | Acme Paper Corporation |
    +------------------------+