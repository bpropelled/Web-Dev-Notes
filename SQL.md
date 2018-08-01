MySQL
===============

Getting started: 
- http://www.sqlteaching.com/
- https://www.codecademy.com/courses/learn-sql

Related tutorials:
- MySQL-CLI: https://www.youtube.com/playlist?list=PLfdtiltiRHWEw4-kRrh1ZZy_3OcQxTn7P
- Analyzing Business Metrics: https://www.codecademy.com/learn/sql-analyzing-business-metrics
- SQL joins infografic: http://cd64.de/sql-joins

Tools:
- DataGrip: https://www.jetbrains.com/datagrip/
- Sequel Pro: http://www.sequelpro.com/

## Types of Fields for MySQL
Column | Data type	 | Note
------------ | ------------- | -------------
id	| INTEGER |	AUTO_INCREMENT, UNSIGNED
uuid |	CHAR(36)	or CHAR(16) | binary
title |	VARCHAR(255)	 
full name | 	VARCHAR(70)	 
gender |	TINYINT	UNSIGNED
description |	TINYTEXT |	often may not be enough, use TEXT instead
post body |	TEXT	 
email |	VARCHAR(255)	 
url |	VARCHAR(2083) |	MySQL version < 5.0.3 - use TEXT
salt |	CHAR(x) |	randomly generated string, usually of fixed length (x)
digest (md5)|	CHAR(32)	 
phone number | VARCHAR(20)	 
US zip code |	CHAR(5) |	Use CHAR(10) if you store extended codes
US/Canada p.code | CHAR(6)	 
file path |VARCHAR(255)	 
5-star rating | DECIMAL(3,2) | UNSIGNED
price | DECIMAL(10,2) | UNSIGNED
date (creation) | DATE/DATETIME | usually displayed as initial date of a post
date (tracking) | TIMESTAMP | can be used for tracking changes in a post
tags, categories | TINYTEXT | comma separated values *
status | TINYINT(1)	1 – published, 0 – unpublished,  | You can also use ENUM for human-readable values
json data | JSON or LONGTEXT


## Types of Fields for Postgresql
Column | Data type	 | Note
------------ | ------------- | -------------
id (autoinc)|SERIAL | or INTEGER for more control
uuid|UUID	 
title|VARCHAR(255)|or TEXT
full name|VARCHAR(70)|or TEXT
gender|ENUM	| ('Male', 'Female', 'Intersex', 'Transgender',
'Unknown')
description|TEXT	 
post body|TEXT	 
email|CITEXT|or VARCHAR(255)
url|VARCHAR(2083)|or TEXT
salt|CHAR(x)|randomly generated string, usually of fixed length (x)
digest (md5)|UUID|ex.: md5('a string')::uuid
phone number|VARCHAR(20)	 
US zip code|CHAR(5)|Use CHAR(10) if you store extended codes
US/Canada p.code|CHAR(6)	 
file path|VARCHAR(254)|or TEXT
5-star rating|NUMERIC(3,2)	 
price|NUMERIC(10,2)	 
date|TIMESTAMP|WITH TIME ZONE
tags, categories|ARRAY	 
status|ENUM|('published', 'unpublished', …)
json|JSON|PostgreSQL >= 9.3



Commands
-----------

Access monitor: `mysql -u [username] -p;` (will prompt for password)

Show all databases: `show databases;`

Access database: `mysql -u [username] -p [database]` (will prompt for password)

Create new database: `create database [database];`

Select database: `use [database];`

Determine what database is in use: `select database();`

Show all tables: `show tables;`

Show table structure: `describe [table];`

List all indexes on a table: `show index from [table];`

Create new table with columns: `CREATE TABLE [table] ([column] VARCHAR(120), [another-column] DATETIME);`

Adding a column: `ALTER TABLE [table] ADD COLUMN [column] VARCHAR(120);`

Adding a column with an unique, auto-incrementing ID: `ALTER TABLE [table] ADD COLUMN [column] int NOT NULL AUTO_INCREMENT PRIMARY KEY;`

Inserting a record: `INSERT INTO [table] ([column], [column]) VALUES ('[value]', [value]');`

MySQL function for datetime input: `NOW()`

Selecting records: `SELECT * FROM [table];`

Explain records: `EXPLAIN SELECT * FROM [table];`

Selecting parts of records: `SELECT [column], [another-column] FROM [table];`

Counting records: `SELECT COUNT([column]) FROM [table];`

Counting and selecting grouped records: `SELECT *, (SELECT COUNT([column]) FROM [table]) AS count FROM [table] GROUP BY [column];`

Selecting specific records: `SELECT * FROM [table] WHERE [column] = [value];` (Selectors: `<`, `>`, `!=`; combine multiple selectors with `AND`, `OR`)

Select records containing `[value]`: `SELECT * FROM [table] WHERE [column] LIKE '%[value]%';`

Select records starting with `[value]`: `SELECT * FROM [table] WHERE [column] LIKE '[value]%';`

Select records starting with `val` and ending with `ue`: `SELECT * FROM [table] WHERE [column] LIKE '[val_ue]';`

Select a range: `SELECT * FROM [table] WHERE [column] BETWEEN [value1] and [value2];`

Select with custom order and only limit: `SELECT * FROM [table] WHERE [column] ORDER BY [column] ASC LIMIT [value];` (Order: `DESC`, `ASC`)

Updating records: `UPDATE [table] SET [column] = '[updated-value]' WHERE [column] = [value];`

Deleting records: `DELETE FROM [table] WHERE [column] = [value];`

Delete *all records* from a table (without dropping the table itself): `DELETE FROM [table];`
(This also resets the incrementing counter for auto generated columns like an id column.)

Delete all records in a table: `truncate table [table];`

Removing table columns: `ALTER TABLE [table] DROP COLUMN [column];`

Deleting tables: `DROP TABLE [table];`

Deleting databases: `DROP DATABASE [database];`

Custom column output names: `SELECT [column] AS [custom-column] FROM [table];`

Export a database dump (more info [here](http://stackoverflow.com/a/21091197/1815847)): `mysqldump -u [username] -p [database] > db_backup.sql`

Use `--lock-tables=false` option for locked tables (more info [here](http://stackoverflow.com/a/104628/1815847)).

Import a database dump (more info [here](http://stackoverflow.com/a/21091197/1815847)): `mysql -u [username] -p -h localhost [database] < db_backup.sql`

Logout: `exit;`


Aggregate functions
-----------

Select but without duplicates: `SELECT distinct name, email, acception FROM owners WHERE acception = 1 AND date >= 2015-01-01 00:00:00`

Calculate total number of records: `SELECT SUM([column]) FROM [table];`

Count total number of `[column]` and group by `[category-column]`: `SELECT [category-column], SUM([column]) FROM [table] GROUP BY [category-column];`

Get largest value in `[column]`: `SELECT MAX([column]) FROM [table];`

Get smallest value: `SELECT MIN([column]) FROM [table];`

Get average value: `SELECT AVG([column]) FROM [table];`

Get rounded average value and group by `[category-column]`: `SELECT [category-column], ROUND(AVG([column]), 2) FROM [table] GROUP BY [category-column];`


Multiple tables
-----------

Select from multiple tables: `SELECT [table1].[column], [table1].[another-column], [table2].[column] FROM [table1], [table2];`

Combine rows from different tables: `SELECT * FROM [table1] INNER JOIN [table2] ON [table1].[column] = [table2].[column];`

Combine rows from different tables but do not require the join condition: `SELECT * FROM [table1] LEFT OUTER JOIN [table2] ON [table1].[column] = [table2].[column];` (The left table is the first table that appears in the statement.)

Rename column or table using an _alias_: `SELECT [table1].[column] AS '[value]', [table2].[column] AS '[value]' FROM [table1], [table2];`


Users functions
-----------

List all users: `SELECT User,Host FROM mysql.user;`

Create new user: `CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';`

Grant `ALL` access to user for `*` tables: `GRANT ALL ON database.* TO 'user'@'localhost';`


Find out the IP Address of the Mysql Host
-----------
`SHOW VARIABLES WHERE Variable_name = 'hostname';` ([source](http://serverfault.com/a/129646))

## Difference between SQL RDMS

[Source](https://www.digitalocean.com/community/tutorials/sqlite-vs-mysql-vs-postgresql-a-comparison-of-relational-database-management-systems "Permalink to SQLite vs MySQL vs PostgreSQL: A Comparison Of Relational Database Management Systems")

# SQLite vs MySQL vs PostgreSQL: A Comparison Of Relational Database Management Systems

### Introduction

* * *

Relational databases have been in use for a long time. They became popular thanks to management systems that implement the relational model extremely well, which has proven to be a great way to work with data [especially for mission-critical applications].

In this DigitalOcean article, we are going to try to understand the core differences of some of the most commonly used and popular relational database management systems (RDBMS). We will explore their fundamental differences in terms of features and functionality, how they work, and when one excels over the other in order to help developers with choosing a RDBMS.

## Glossary

* * *

### 1\. Database Management Systems

* * *

1. Relational Database Management Systems
2. Relations And Data Types
3. Popular And Important Relational Databases

### 2\. SQLite

* * *

1. SQLite's Supported Data Types
2. Advantages of SQLite
3. Disadvantages of SQLite
4. When To Use SQLite
5. When Not To Use SQLite

### 3\. MySQL

* * *

1. MySQL's Supported Data Types
2. Advantages of MySQL
3. Disadvantages of MySQL
4. When To Use MySQL
5. When Not To Use MySQL

### 4\. PostgreSQL

* * *

1. PostgreSQL's Supported Data Types
2. Advantages of PostgreSQL
3. Disadvantages of PostgreSQL
4. When To Use PostgreSQL
5. When Not To Use PostgreSQL

## Database Management Systems

* * *

Databases are logically modelled storage spaces for all kinds of different information (data). Each database, other than schema-less ones, have a model, which provide structure for the data being dealt with. Database management systems are applications (or libraries) which manage databases of various shapes, sizes, and sorts.

**Note:** To learn more about Database Management Systems, check out our article: [Understanding Databases][1].

### Relational Database Management Systems

* * *

Relational Database Systems implement the relational model to work with the data. Relational model shapes whatever information to be stored by defining them as related entities with attributes across tables (i.e. schemas).

These type of database management systems require structures (e.g. a table) to be defined in order to contain and work with the data. With tables, each column (e.g. attribute) holds a different type (e.g. data type) of information. Each record in the database, uniquely identified with _keys_, translates to a row that belongs to a table, with each row's series of attributes being represented as the columns of a table -- all related together, as defined within the relational model.

### Relations And Data Types

* * *

Relations can be considered as mathematical sets that contain series of attributes which collectively represent the database and information being kept. This type of identification and collection method allow relational databases to work the way they do.

When defining a table to insert records, each element forming a record (i.e. attribute) must match the defined _data type_ (e.g. an integer, a date etc.). Different relational database management systems implement different data types -- which are not always directly interchangeable.

Working with and through constraints, like the one we have just explained, is common with relational databases. In fact, constraints form the core of the relations.

**Note:** If you need to work with truly unrelated, randomly represented information (e.g. a document), you might be interested in using a NoSQL (schema-less database). If you would like to learn more about them, check out our article [A Comparison Of NoSQL Database Management Systems][2].

### Popular And Important Relational Databases

* * *

In this article, we are going to introduce three major and important open-source relational database management systems that have helped to shape the world of application development.

A very powerful, embedded relational database management system. 

The most popular and commonly used RDBMS.

The most advanced, SQL-compliant and open-source objective-RDBMS.

**Note:** Open-source applications almost always come with the freedom to use any way desired. Most of the time freedom to fork the project (therefore use the code) to create something new is also permitted. If you are interested in DBMSs, you might want to check out some forked projects, based on these popular ones, such as the [MariaDB][3].

## SQLite

* * *

SQLite is an amazing library that gets embedded inside the application that makes use of. As a self-contained, file-based database, SQLite offers an amazing set of tools to handle all sorts of data with much less constraint and ease compared to hosted, process based (server) relational databases.

When an application uses SQLite, the integration works with functional and direct calls made to a file holding the data (i.e. SQLite database) instead of communicating through an interface of sorts (i.e. ports, sockets). This makes SQLite extremely fast and efficient, and also powerful thanks to the library's underlying technology.

### SQLite's Supported Data Types

* * *

NULL value.

Signed integer, stored in 1, 2, 3, 4, 6, or 8 bytes depending on the magnitude of the value.

Floating point value, stored as an 8-byte IEEE floating point number.

Text string, stored using the database encoding (UTF-8, UTF-16BE or UTF-16LE).

A blob of data, stored exactly as it was input.

**Note:** To learn more about SQLite's data types and SQLite type affinity, check out the [official documentation][4] on the subject.

### Advantages of SQLite

* * *

The entire database consists of a single file on the disk, which makes it extremely portable.

Although it might appear like a "simple" DB implementation, SQLite uses SQL. It has some features omitted (`RIGHT OUTER JOIN` or `FOR EACH STATEMENT`), however, some additional ones are baked in.

* **Great for developing and even testing:**  

During the development phase of most applications, for a majority of people it is extremely likely to need a solution that can scale for concurrency. SQLite, with its rich feature base, can offer more than what is needed for development with the simplicity of working with a single file and a linked C based library.

### Disadvantages of SQLite

* * *

Advanced databases come with the support for users, i.e. managed connections with set access privileges to the database and tables. Given the purpose and nature of SQLite (no higher-levels of multi-client concurrency), this feature does not exist.

* **Lack of possibility to tinker with for additional performance:**  

Again by design, SQLite is not possible to tinker with to obtain a great deal of additional performance. The library is simple to tune and simple to use. Since it is not complicated, it is technically not possible to make it more performant than it already, amazingly is.

### When To Use SQLite

* * *

All applications that need portability, that do not require expansion, e.g. single-user local applications, mobile applications or games.

In many cases, applications that need to read/write files to disk directly can benefit from switching to SQLite for additional functionality and simplicity that comes from using the _Structured Query Language_ (SQL).

It is an overkill for a large portion of applications to use an additional process for testing the business-logic (i.e. the application's main purpose: functionality). 

### When Not To Use SQLite

* * *

If you are working on an application whereby multiple clients need to access and use the same database, a fully-featured RDBM (e.g. MySQL) is probably better to choose over SQLite.

* **Applications requiring high write volumes:**  

One of the limitations of SQLite is the _write_ operations. This DBMS allows only one single write*operating to take place at any given time, hence allowing a limited throughput.

## MySQL

* * *

MySQL is the most popular one of all the large-scale database servers. It is a feature rich, open-source product that powers a lot of web-sites and applications online. Getting started with MySQL is relatively easy and developers have access to a massive array of information regarding the database on the internet.

**Note:** It should be stated that given the popularity of the product, there are a lot of third-party applications, tools and integrated libraries which help greatly with many aspects of working with this RDBMS.

Despite not trying to implement the full SQL standard, MySQL offers a lot of functionality to the users. As a stand-alone database server, applications talk to MySQL daemon process to access the database itself -- unlike SQLite. 

### MySQL's Supported Data Types

* * *

A very small integer.

A small integer.

A medium-size integer.

A normal-size integer.

A large integer.

A small (single-precision) floating-point number. Cannot be unsigned.

* **DOUBLE, DOUBLE PRECISION, REAL:**  

A normal-size (double-precision) floating-point number. Cannot be unsigned.

An unpacked floating-point number. Cannot be unsigned.

A date.

A date and time combination.

A timestamp.

A time.

A year in 2- or 4- digit formats (default is 4-digit).

A fixed-length string that is always right-padded with spaces to the specified length when stored.

A variable-length string.

A BLOB or TEXT column with a maximum length of 255 (2^8 - 1) characters.

A BLOB or TEXT column with a maximum length of 65535 (2^16 - 1) characters.

A BLOB or TEXT column with a maximum length of 16777215 (2^24 - 1) characters.

A BLOB or TEXT column with a maximum length of 4294967295 (2^32 - 1) characters.

An enumeration.

A set.

### Advantages of MySQL

* * *

MySQL can be installed very easily. Third-party tools, including visual ones (i.e. GUIs) make it extremely simple to get started with the database.

MySQL supports a lot of the SQL functionality that is expected from a RDBMS -- either directly or indirectly.

A lot of security features, some rather advanced, are built in MySQL.

MySQL can handle _a lot_ of data and furthermore it can be used "at scale", if needed be.

Giving up some standards allows MySQL to work very efficiently and cut corners, thus providing speed gains.

### Disadvantages of MySQL

* * *

By design, MySQL does not intend to do everything and it comes with functional limitations that some state-of-the-art applications might require.

The way certain functionality gets handled with MySQL (e.g. references, transactions, auditing etc.) renders it a little-less reliable compared to some other RDBMSs.

Although MySQL is still technical an open-source product, there are complaints regarding the development process since its acquisition. However, it should be noted that there are some MySQL-based, fully-integrated databases that add value on top of the standard MySQL installations (e.g. MariaDB).

### When To Use MySQL

* * *

When you need more than what SQLite can offer, including MySQL to your deployment stack, just like any stand-alone database server, brings a lot of operational freedom together with some advanced features.

MySQL's security features provide reliable protection for data-access (and use) in a simple way.

* **Web-sites and web-applications:**  

A great majority of web-sites (and web-applications) can simply work on MySQL despite the constraints. This flexible and somewhat scalable tool is easy to use and easy to manage -- which proves very helpful in the long run.

If you are working on a highly specific and extremely custom solution, MySQL can tag along easily and go by your rules thanks to its rich configuration settings and operation modes.

### When Not To Use MySQL

* * *

Since MySQL does not [try to] implement the full SQL standard, this tool is not completely SQL compliant. If you might need integration with such RDBMSs, switching from MySQL will not be easy.

Even though MySQL and some storage engines perform really well with _read_ operations, concurrent _read-writes_ can be problematic.

Again, depending on the choice of the database-engine, MySQL can lack certain features, such as the full-text search. 

## PostgreSQL

* * *

PostgreSQL is _the_ advanced, open-source [object]-relational database management system which has the main goal of being standards-compliant and extensible. PostgreSQL, or Postgres, tries to adopt the ANSI/ISO SQL standards together with the revisions. 

Compared to other RDBMSs, PostgreSQL differs itself with its support for highly required and integral object-oriented and/or relational database functionality, such as the complete support for reliable transactions, i.e. Atomicity, Consistency, Isolation, Durability (ACID).

Due to the powerful underlying technology, Postgres is extremely capable of handling many tasks very efficiently. Support for concurrency is achieved without read locks thanks to the implementation of Multiversion Concurrency Control (MVCC), which also ensures the ACID compliance.

PostgreSQL is highly programmable, and therefore extendible, with custom procedures that are called "stored procedures". These functions can be created to simplify the execution of repeated, complex and often required database operations.

Although this DBMS does not have the popularity of MySQL, there are many amazing third-party tools and libraries that are designed to make working with PostgreSQL simple, despite this database's powerful nature. Nowadays it is possible to get PostgreSQL as an application package through many operating-system's default package manager with ease.

### PostgreSQL's Supported Data Types

* * *

signed eight-byte integer

autoincrementing eight-byte integer

fixed-length bit string

variable-length bit string

logical Boolean (true/false)

rectangular box on a plane

binary data ("byte array")

variable-length character string

fixed-length character string

IPv4 or IPv6 network address

circle on a plane

calendar date (year, month, day)

double precision floating-point number (8 bytes)

IPv4 or IPv6 host address

signed four-byte integer

time span

infinite line on a plane

line segment on a plane

MAC (Media Access Control) address

currency amount

exact numeric of selectable precision

geometric path on a plane

geometric point on a plane

closed geometric path on a plane

single precision floating-point number (4 bytes)

signed two-byte integer

autoincrementing four-byte integer

variable-length character string

* **time [(p)] [without time zone]:**  

time of day (no time zone)

* **time [(p)] with time zone:**  

time of day, including time zone

* **timestamp [(p)] [without time zone]:**  

date and time (no time zone)

* **timestamp [(p)] with time zone:**  

date and time, including time zone

text search query

text search document

user-level transaction ID snapshot

universally unique identifier

XML data

### Advantages of PostgreSQL

* * *
* **An open-source SQL standard compliant RDBMS:**  

PostgreSQL is open-source and free, yet a very powerful relational database management system.

PostgreSQL is supported by a devoted and experienced community which can be accessed through knowledge-bases and Q&A sites 24/7 for free.

* **Strong third-party support:**  

Regardless of the extremely advanced features, PostgreSQL is adorned with many great and open-source third-party tools for designing, managing and using the management system.

It is possible to extend PostgreSQL programmatically with stored procedures, like an advanced RDBMS should be.

PostgreSQL is not just a relational database management system but an objective one - with support for nesting, and more.

### Disadvantages of PostgreSQL

* * *

For simple _read_-heavy operations, PostgreSQL can be an over-kill and might appear less performant than the counterparts, such as MySQL.

Given the nature of this tool, it lacks behind in terms of popularity, despite the very large amount of deployments - which might affect how easy it might be possible to get support.

Due to above mentioned factors, it is harder to come by hosts or service providers that offer managed PostgreSQL instances. 

### When To Use PostgreSQL

* * *

When reliability and data integrity are an absolute necessity without excuses, PostgreSQL is the better choice.

* **Complex, custom procedures:**  

If you require your database to perform custom procedures, PostgreSQL, being extensible, is the better choice.

In the future, if there is a chance of necessity arising for migrating the entire database system to a propriety (e.g. Oracle) solution, PostgreSQL will be the most compliant and easy to handle base for the switch. 

Compared to other open-source and free RDBMS implementations, for complex database designs, PostgreSQL offers the most in terms of functionality and possibilities without giving up on other valuable assets.

### When Not To Use PostgreSQL

* * *

If all you require is fast _read_ operations, PostgreSQL is not the tool to go for.

Unless you require absolute data integrity, ACID compliance or complex designs, PostgreSQL can be an over-kill for simple set-ups.

Unless you are willing to spend the time, energy and resources, achieving replication with MySQL might be simpler for those who lack the database and system administration experience.

[1]: https://www.digitalocean.com/community/articles/understanding-sql-and-nosql-databases-and-different-database-models
[2]: https://www.digitalocean.com/community/articles/a-comparison-of-nosql-database-management-systems-and-models
[3]: https://mariadb.org/
[4]: http://www.sqlite.org/datatype3.html

  