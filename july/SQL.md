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
