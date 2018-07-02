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

### OPERATORS WHERE clause

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

The WHERE clause can be combined with AND, OR and NOT operators.

The AND and OR operators are used to filter records based on MORE THAN ONE condition.

AND - displays a record if all the conditions separated by the AND operator is true.

OR - displays a record if all the conditions separated by the OR operator is TRUE

NOT - displays records if the condition(s) is NOT TRUE.

```
SELECT column1, column2
FROM table_name
WHERE condition1 AND condition2 AND condition3;

SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;

SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```

```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;

SELECT * FROM Customers
WHERE NOT Country='Germany';
```

You can also combine the AND, OR and NOT operators.

The following SQL statement selects all fields from "Customers" where country is "Germany" AND city must be "Berlin" OR "München" (use parenthesis to form complex expressions):

Example

```
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

The following SQL statement selects all fields from "Customers" where country is NOT "Germany" and NOT "USA":

Example

```
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```

---

### ORDER BY

The following SQL statement selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column:

Example

```
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

---

### INSERT INTO statement

It is possible to write the INSERT INTO statement in two ways.

The first way specifies both the column names and the values to be inserted:

```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query. However, make sure the order of the values is in the same order as the columns in the table. The INSERT INTO syntax would be as follows:

```
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

Insert Data Only in Specified Columns
It is also possible to only insert data in specific columns.

The following SQL statement will insert a new record, but only insert data in the "CustomerName", "City", and "Country" columns (CustomerID will be updated automatically):

Example

```
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
```

---

### NULL Value

A field with a NULL value is a field with no value.

If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

**NOTE:** It is very important to understand that a NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record creation!

Test for NULL Values?
It is not possible to test for NULL values with comparison operators, such as =, <, or <>.

We will have to use the IS NULL and IS NOT NULL operators instead.

```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

---

### SQL UPDATE and DELETE Statement

The UPDATE statement is used to modify the existing records in a table.

UPDATE and DELETE Syntax

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**NOTE:** Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!

```
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;
```

---

### TOP, LIMIT

The following SQL statement selects the first three records from the "Customers" table: (can also use PERCENT)

Example

```
SELECT TOP 3 * FROM Customers;
```

The following SQL statement shows the equivalent example using the LIMIT clause:

Example

```
SELECT * FROM Customers
LIMIT 3;
```

---

### SQL MIN() and MAX() Functions

The MIN() function returns the smallest value of the selected column.

The MAX() function returns the largest value of the selected column.

```
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

The COUNT() function returns the number of rows that matches a specified criteria.

The AVG() function returns the average value of a numeric column.

The SUM() function returns the total sum of a numeric column.

---

### WILDCARD

A wildcard character is used to substitute any other character(s) in a string.

Wildcard characters are used with the SQL LIKE operator. The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards used in conjunction with the LIKE operator:

% - The percent sign represents zero, one, or multiple characters
\_ - The underscore represents a single character

### LIKE Operator Description

WHERE CustomerName LIKE 'a%' - Finds any values that start with "a"
WHERE CustomerName LIKE '%a' - Finds any values that end with "a"
WHERE CustomerName LIKE '%or%' - Finds any values that have "or" in any position
WHERE CustomerName LIKE '_r%' - Finds any values that have "r" in the second position
WHERE CustomerName LIKE 'a_%\_%' - Finds any values that start with "a" and are at least 3 characters in length
WHERE ContactName LIKE 'a%o' - Finds any values that start with "a" and ends with "o"

---

### SQL IN Operator

The IN operator allows you to specify multiple values in a WHERE clause.

The IN operator is a shorthand for multiple OR conditions.

---
