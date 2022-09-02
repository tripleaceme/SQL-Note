## SQL Note

# PART 1
<a href='https://drill.apache.org/'><img src="Screenshot%202022-09-01%20at%2018.24.55.png" alt="Query NoSQL Databases" /></a>

- Since organizations frequently store data using multiple technologies, there is a need to unplug SQL from a particular database server and provide a service that can span multiple databases. For example, a report may need to bring together data stored in Oracle, Hadoop, JSON files, CSV files, and Unix log files. 

- A new generation of tools have been built to meet this type of challenge, and one of the most promising is <a href='https://drill.apache.org/'>Apache Drill</a>, which is an open source query engine that allows users to write queries that can access data stored in most any database or filesystem.

 However, this is my Note on SQL (Relational Databases) from beginner to Advance (MySQL)

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
        - SELECT, UPDATE, DELETE AND INSERT



- Download the database used in the note<a href='https://dev.mysql.com/doc/index-other.html'> here</a>

#### I hope that when you finish this note and worked through all of the examples, you will be well on your way to becoming a seasoned SQL practitioner.

- For languages that use the Latin alphabet, such as English, there is a sufficiently small number of characters such that only a single byte is needed to store each character. Other languages, such as Japanese and Korean, contain large numbers of characters, thus requiring multiple bytes of storage for each character. Such character sets are therefore called multibyte character sets.

# Data Types
## Character Data
Character data can be stored as either fixed-length or variable-length strings; the dif‐ ference is that fixed-length strings are right-padded with spaces and always consume the same number of bytes, and variable-length strings are not right-padded with spaces and don’t always consume the same number of bytes.

`char(20)    /* fixed-length */`
`varchar(20) /* variable-length */`

- The maximum length for char columns is currently `255 bytes`, whereas varchar col‐ umns can be up to `65,535 bytes`. If you need to store longer strings (such as emails, XML documents, etc.), then you will want to use one of the text types `(mediumtext and longtext)`

## Character sets
For languages that use the Latin alphabet, such as English, there is a sufficiently small number of characters such that only a single byte is needed to store each character. Other languages, such as Japanese and Korean, contain large numbers of characters, thus requiring multiple bytes of storage for each character. Such character sets are therefore called multibyte character sets.

To view the supported character sets in your server, you can use the show command, as shown in the following example:
`SHOW CHARACTER SET;`

- MySQL can store data using various character sets, both single- and multibyte. 
- If the value in the fourth column, maxlen, is greater than 1, then the character set is a multibyte character set.

## Text data
If you need to store data that might exceed the 64 KB limit for varchar columns, you will need to use one of the text types.

| Text type | Maximum number of bytes |
|------------|------------|
| tinytext | 255|
| text | 65,535 |
| mediumtext | 16,777,215 |
| longtext  | 4,294,967,295 |

When choosing to use one of the text types, you should be aware of the following:
- If the data being loaded into a text column exceeds the maximum size for that type, the data will be truncated.
- Trailing spaces will not be removed when data is loaded into the column.
- When using text columns for sorting or grouping, only the first 1,024 bytes are used, although this limit may be increased if necessary.
- The different text types are unique to MySQL. SQL Server has a single text type for large character data, whereas DB2 and Oracle use a data type called clob, for Character Large Object.
- MySQL allows up to 65,535 bytes for varchar columns (it was limited to 255 bytes in version 4), there isn’t any particular need to use the tinytext or text type.

`If you are creating a column for free-form data entry, such as a notes column to hold data about customer interactions with your company’s customer service department, then varchar will probably be adequate. If you are storing documents, however, you should choose either the mediumtext or longtext type.`

## Numeric Data
| Type | Signed range | Unsigned range| 
| -------| --------| ------------| 
| tinyint | −128 to 127 | 0to255| 
| smallint | −32,768 to 32,767| 0 to 65,535  |
| mediumint | −8,388,608 to 8,388,607 | 0 to 16,777,215| 
| int | −2,147,483,648 to 2,147,483,647| 0 to 4,294,967,295  | 
| bigint | −2^63 to 2^63 - 1| 0 to 2^64 - 1| 
| float(p,s) | −3.402823466E+38 to −1.175494351E-38 | 1.175494351E-38 to 3.402823466E+38 |
| double(p,s) | −1.7976931348623157E+308 to −2.2250738585072014E-308 | 2.2250738585072014E-308 to 1.7976931348623157E+308 |

## Temporal Data
Along with strings and numbers, you will almost certainly be working with informa‐ tion about dates and/or times. This type of data is referred to as temporal, and some examples of temporal data in a database include:
- The future date that a particular event is expected to happen, such as shipping a customer’s order
- The date that a customer’s order was shipped
- The date and time that a user modified a particular row in a table
- An employee’s birth date
- The year corresponding to a row in a yearly_sales fact table in a data warehouse
- The elapsed time needed to complete a wiring harness on an automobile assembly line

| Type | Default format | Allowable values |
|------|-------------|-------------|
| date | YYYY-MM-DD | 1000-01-01 to 9999-12-31 |
| datetime | YYYY-MM-DD HH:MI:SS | 1000-01-01 00:00:00.000000 to 9999-12-31 23:59:59.999999 |
| timestamp | YYYY-MM-DD HH:MI:SS | 1970-01-01 00:00:00.000000 to 2038-01-18 22:14:07.999999  |
| year | YYYY | 1901 to 2155 |
|time | HHH:MI:SS | −838:59:59.000000 to 838:59:59.000000 |

- The datetime, timestamp, and time types also allow fractional seconds of up to 6 decimal places (microseconds).

### Date format components
|Component | Definition | Range |
|------|----------|------|
| YYYY |Year, including century |1000 to 9999 |
| MM | Month | 01(January) to 12(December) |
| DD | Day | 01 to 31|
| HH | Hour | 00 to 23|
| HHH | Hours (elapsed) | −838 to 838 |
| MI | Minute | 00 to 59 |
| SS | Second | 00 to 59 |


Here’s how the various temporal types would be used to implement the examples shown earlier:
- Columns to hold the expected future shipping date of a customer order and an employee’s birth date would use the date type, since it is unrealistic to schedule a future shipment down to the second and unnecessary to know at what time a person was born.
- A column to hold information about when a customer order was actually shipped would use the datetime type, since it is important to track not only the date that the shipment occurred but the time as well.
- A column that tracks when a user last modified a particular row in a table would use the timestamp type. The timestamp type holds the same information as the datetime type (year, month, day, hour, minute, second), but a timestamp column will automatically be populated with the current date/time by the MySQL server when a row is added to a table or when a row is later modified.
- A column holding just year data would use the year type.
- Columns that hold data regarding the length of time needed to complete a task would use the time type. For this type of data, it would be unnecessary and con‐ fusing to store a date component, since you are interested only in the number of hours/minutes/seconds needed to complete the task. This information could be derived using two datetime columns (one for the task start date/time and the other for the task completion date/time) and subtracting one from the other, but it is simpler to use a single time column.

# Exercise 1
### Creating a Table
Now that you have a firm grasp on what data types may be stored in a MySQL database, start by defining a table to hold information about a person.
`A good way to start designing a table is to do a bit of brainstorming to see what kind of information would be helpful to include.`

<details> <summary> Solution </summary>
<p>

Here is the statement to create the person table:<br />
    `CREATE TABLE person`<br />
     `(person_id SMALLINT UNSIGNED,`<br />
      `fname VARCHAR(20),`<br />
      `lname VARCHAR(20),`<br />
      `age SMALLINT UNSIGNED,`<br />
      `eye_color CHAR(2) CHECK (eye_color IN ('BR','BL','GR')),`<br /> #ensure that `eye_color` value is either `'GR'` or `'BL'` or `'GR'`
      `birth_date DATE,`<br />
      `street VARCHAR(30),`<br />
      `city VARCHAR(20),`<br />
      `state VARCHAR(20),`<br />
      `phone_number CHAR(11),`<br />
      `country VARCHAR(20),`<br />
      `postal_code VARCHAR(20),`<br />
      `CONSTRAINT pk_person PRIMARY KEY (person_id) AUTO_INCREMENT ); # Unique identifier for the person`<br />

Another way to declare the eye_color column would be `eye_color ENUM('BR','BL','GR')`. <br />

Run the following command to see the person table structure:<br />
`Describe person`;<br />

#### Quick Explanation
- Columns 1 and 2 of the describe output are self-explanatory. 
- Column 3 shows whether a particular column can be omitted when data is inserted into the table. 
- The fourth column shows whether a column takes part in any keys (primary or foreign); in this case, the person_id column is marked as the primary key.
- Column 5 shows whether a particular column will be populated with a default value if you omit the column when inserting data into the table. 
- The sixth column (called “Extra”) shows any other pertinent infor‐ mation that might apply to a column.
</p>
</details>

# Populating the table

With the person table in place, you can now begin to explore the four SQL data statements mentioned earlier: `insert, update, delete, and select.`<br />
- Insert data into the table you've created.

<details> <summary> Solution </summary>
<p>

`INSERT INTO person:`<br />
        `VALUES (1, 'Sean','Turner',42, 'BR', '1972-05-27', '10 Marcre Str., Mishin','Lagos','234812019102', 'Nigeria','100121'),`
        `(2, 'Susan','Smith', 32,'BL', '1975-11-02','23 Maple St., Arlington', 'VA', 'USA', '20220');`<br />

</p>
</details>

# Updating Data
When the data for William Turner was initially added to the table, data for the various address columns was not included in the insert statement. 
- Update one of the information you inserted into the table to reflect changes in the data.

<details> <summary> Solution </summary>
<p>

`UPDATE person`<br />
    `SET street = '1225 Tremont St.',`<br />
    `city = 'Boston',`<br />
    `state = 'MA',`<br />
    `country = 'USA',`<br />
    `postal_code = '02138'`<br />
    `WHERE person_id = 1;`<br />
</p>
</details>

# Deleting Data
It seems that Sean and Susan aren’t getting along very well together, so one of them has got to go.  I will delete one person at random, so Sean get the booted out by delete statement.
-  Delete one of the information you inserted into the table to reflect changes in the data.

<details> <summary> Solution </summary>
<p>

`DELETE FROM person`<br />
        `WHERE person_id = 1;`
</p>
</details>

# Bad Practices To Avoid
- Nonunique Primary Key
- Nonexistent Foreign Key
- Column Value Violations
- Invalid Data Type Insetion e.g `'DEC-21-1980' instead of '1980-12-21'` | Can be rectified using `str_to_date('DEC-21-1980' , '%b-%d-%Y')`

<details> <summary>  A few more formatters that you might need when converting strings to datetimes in MySQL: </summary>
<p>

- %a The short weekday name, such as Sun, Mon, ...
- %b The short month name, such as Jan, Feb, ...
- %c The numeric month (0..12)
- %d The numeric day of the month (00..31)
- %f The number of microseconds (000000..999999)
- %H The hour of the day, in 24-hour format (00..23)
- %h The hour of the day, in 12-hour format (01..12)
- %i The minutes within the hour (00..59)
- %j The day of year (001..366)
- %M The full month name (January..December)
- %m The numeric month
- %p AM or PM
- %s The number of seconds (00..59)
- %W The full weekday name (Sunday..Saturday)
- %w The numeric day of the week (0=Sunday..6=Saturday)
- %Y The four-digit year

</p>
</details>

I hope the first part of the note has prepared your mind for the beautiful world of SQL. However, every single thing implemented in the first part of the note can be implemented in any flavor of SQL with little to no changes.

Once you're comfortable with one RDBMS, the others comes easy. It's just like using an iPhone after long years of using Androids or using MacBook after
long usage of Dell Laptop or Lenovo.

# THANK YOU


# PART 2

For this part of the note, the queries will be exploring the Sakila database we downloaded at the beginning of the note. Ensure to download it and load it into your RDBMS.