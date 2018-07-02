# SQL Structured Query Language

## Overview

RDBMS - Relational Database Management System (basis for all modern database systems, mySQL, Oracle, etc. )

The data in RDBMS is stored in database objects called **tables**. A table is a collection of related data entries and it consists of columns and rows. Database Tables, a database more often contains one or more tables. Each table is identified by a name.

Every **table** is broken up into smaller entities called fields. A **field** is a **column** in a table that is designed to maintain specific information about every record in the table.

A **record**, also called a **row**, is each individual entry that exists for a table. A record is a horizontal entity in a table.

Tables
ROW/horizontal--> record
COLUMN/vertical --> field

---

## SQL Syntax & Statements

**NOTE:** SQL keywords are **NOT** case sensitive, select is the same as SELECT.

Semicolon usage--> Some database systems require a semicolon at the end of each statement. Semicolon is the standard way to separate each SQL statement in database systems that allow more that one SQL statement to be executed in the **same** call to the server.

**NOTE:** The data returned is stored in a result table, called the result-set.

---

SELECT - extracts data from a database
UPDATE - updates data in a database
DELETE - deleted data from a database
INSERT INTO - inserts new data into a database
CREATE DATABASE - creates a new database
ALTER DATABASE - modifies a database
CREATE TABLE - creates a new table
ALTER TABLE - modifies a table
DROP TABLE - deletes a table
CREATE INDEX - created an index (search key)
DROP INDEX - deletes an index

---

SELECT DISTINCT - this statement is used to return only distinct (different) values. Inside a table, a column often contains many duplicate values; and sometimes you only want to list out the different (distinct) values.
**NOTE**: The example above will not work in Firefox and Microsoft Edge!

SQL WHERE clause:
The WHERE clause is used to filter records, and used to extract records that only fulfill a specified condition.

**NOTE:** the WHERE clause is not only used in the SELECT statement, but also used in UPDATE, DELETE, etc.

```
SELECT * FROM Customers
WHERE Country='Canada';
```

**NOTE:** single quotes are REQUIRED around text values (most database systems will allow double quotes). However numeric values should not be enclosed in quotes.

```
SELECT * FROM Customers;
WHERE CustomerID=8;
```

Operators in the WHERE clause

```
= // equal
<> and ! = //not equal sometimes written as !=
> // greater than
< // less than
>= // greater than or equal
<= // less than or equal
BETWEEN // between an inclusive range
LIKE // search for a pattern
IN // to specify multiple values for a column.
```
