
# SQL QUERIES AND DATA DEFINATION

 This is an explanation of various SQL QUERIES and DATA DEFINATION


![SERVER!](https://media.istockphoto.com/id/1304450711/photo/database-and-network-technology.jpg?b=1&s=612x612&w=0&k=20&c=SbLUTOBevk1WYvtpYa4_Vqe98sO275RsPWYTLLhv8iw=)


## Data Defination

What is SQL Server?

SQL Server is a relational database management system, or RDBMS, developed and marketed by Microsoft

What is Data Defination?

Refers to the process of defining and describing the structure, organization, and characteristics of the data stored in the database


## Creating Database

Finaly :smiley: lets create our first database using  SQL Server instance using the CREATE DATABASE statement and SQL Server Management Studio.


#### Sytax

```
CREATE DATABASE
```

## Example 

```
CREATE DATABASE directedDB
```

## Droping Database

Incase you want to remove your alredy created database.

#### Sytax

DROP DATABASE

## Example 

```
DROP DATABASE directedDB
```

```
DROP IF EXISTS directedDB
```

The above code checks if the database does exist before deleting this helps to prevent any error occuring after trying to delete noe existing database

## Creating a Database Schema

What is Database Schema?

It is the logic structure of your database example in our case our database we can divide it into 2  logical parts Adminstrative and  Academic parts.Whic will be our schemas

#### Sytax

CREATE SCHEMA schema_name

## Example 

```
CREATE SCHEMA adminstrative
```

```
CREATE SCHEMA academic
```
## Alter Schema


#### Sytax



## Example 

``

``
## Drop Schema

Just as the name suggest it involes removing a schema.

NB

One has to note that while reomoving a schema you have to first remove the tables values attached to the schema before dropping the Schema

#### Sytax

```
DROP SCHEMA schema_name
```


## Example 

```
DROP SCHEMA adminstrative
```

```
DROP SCHEMA academic
```
## Creating a  Table

Basically we use tables to store data in our database

Our tables are part of already created Schemas,you have to always point to specific Schema while creating one.

Inside the table we specify our columns and data types they hold etc ..

#### Sytax

```SQL
CREATE TABLE SCHEMA.table_name(
pk_column data_type PRIMARY KEY,
    column_1 data_type NOT NULL,
    column_2 data_type,
    ...,
    table_constraints
)
```


## Example 

```SQL
CREATE TABLE  adminstrative.students(
    student_id INT PRIMARY KEY IDENTITY (1, 1),
    firstName VARCHAR (20) NOT NULL,
    last_name VARCHAR (20) NOT NULL,
    yearReg DATE,
)
```

```
DROP SCHEMA academic
```
## Server Idenity


#### Sytax



## Example 

``

``
## Server Sequence


#### Sytax



## Example 

``

``
## Dropping Table

Used to remove a table in a database 

#### Sytax

```
DROP TABLE SCHEMA.table_name
```

```
DROP TABLE IF EXISTS SCHEMA.table_name
```

## Example 

```
DROP TABLE adminstrative.students;
```
## Dropping Table

Used to remove a table in a database  just like Dropping does

#### Sytax

```
DROP TABLE SCHEMA.table_name
```

```
DROP TABLE IF EXISTS SCHEMA.table_name
```

## Example 

```
DROP TABLE adminstrative.students;
```
## Rename Table


#### Sytax



## Example 

``

``
## ALTER TABLE ADD COLUMN
It is used to add an extra column from the already created column

#### Sytax

```SQL
ALTER TABLE schema.table_name
ADD COLUMN_NEW  DATA TYPE
```

## Example 

```SQL
ALTER TABLE adminstrative.students
ADD phone VARCHAR(10)
```
## ALTER TABLE ALTER COLUMN
One can do update on a column in atable to example to update the column type

#### Sytax

```SQL
ALTER TABLE  schema.table_name 
ALTER COLUMN column_name new_data_type(size);
```

## Example 

```SQL
ALTER TABLE adminstrative.students
ALTER COLUMN phone INT
```
## ALTER TABLE DROP COLUMN
It is used to remove an extra column from the already created column

#### Sytax

```SQL
ALTER TABLE schema.table_name
DROP COLUMN
```

## Example 

```SQL
ALTER TABLE adminstrative.students
DROP phone
```
## Computed Colums
One can join two colums together and create another coumn

#### Sytax

```SQL
ALTER TABLE  schema.table_name 
ADD new_column AS (column_1 + ' ' + column_2)
```

## Example 

```SQL
ALTER TABLE adminstrative.students
ADD fullNames AS (firstName + ' ' + lastName)
```
## Select Into

Used when we want to create a copy of a table from another schema

#### Sytax

```SQL
SELECT 
    select_list
INTO 
    destination
FROM 
    source
[WHERE condition]
```

## Example 

```SQL
SELECT 
  *
INTO
  academic.students
FROM 
  adminstrative.students
```
## Querying Data

### SELECT

To select data from a table we use the select statement


#### Sytax

```SQL
SELECT 
  SELECT_LIST
FROM
  SCHEMA_NAME.TABLE_NAME
```
You can select specific column by selecting individual column names

## Example 

```SQL
SELECT 
   firstName,
   lastName 
FROM 
   adminstrative.students
```

You can select all column by attaching a star *

```SQL
SELECT 
  *
FROM 
   academic.students
```

Also you can select by condition values by using WHERE property

 Example
```SQL
SELECT 
*
FROM 
adminstrative.students
WHERE
 firstName = 'samuel'
```

Also your can sort the values in a given order by using ORDER BY property

```SQL
SELECT 
*
FROM 
adminstrative.students
ORDER BY
 firstName
```
### The SQL SELECT DISTINCT Statement

The SELECT DISTINCT statement is used to return only distinct (different) values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

### SELECT DISTINCT Syntax
```SQL
SELECT DISTINCT column1, column2, ...
FROM table_name;


```
ID | Name   | Department
---|--------|------------
1  | John   | HR
2  | Mary   | Finance
3  | John   | Sales
4  | Peter  | HR
5  | John   | Finance


### Example
```SQL
SELECT DISTINCT Name
FROM Employees;



```
### The result will be:
```SQL
Name
-----
John
Mary
Peter
```
The SELECT DISTINCT Name statement retrieves the distinct values from the Name column of the Employees table. It eliminates duplicate occurrences of the same name and returns only the unique names present in the table.

It's important to note that SELECT DISTINCT applies to all the selected columns. If you specify multiple columns, the combination of values across those columns will be considered for uniqueness. For example:

```SQL
SELECT DISTINCT Name, Department
FROM Employees;
```

This query will retrieve distinct combinations of Name and Department from the Employees table, eliminating duplicate rows based on both columns.

<span style="color: orange;">In summary, SELECT DISTINCT is used to retrieve unique values from one or more columns in a table, removing duplicates and returning only distinct values.
</span>


### <span style= "color: green">The SQL WHERE Clause</span>
  
   SQL SYNTAX
   ```SQL
   SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
 
Consider a table called Employees with the following columns: ID, Name, Department, and Salary. Here's an example of the table's contents:
ID | Name   | Department | Salary
---|--------|------------|-------
1  | John   | HR         | 50000
2  | Mary   | Finance    | 60000
3  | Peter  | HR         | 55000
4  | Emma   | Marketing  | 45000
5  | James  | Finance    | 65000


```SQL
SELECT Name, Salary
FROM Employees
WHERE Salary > 55000
```
This will select the names and of the people who will meet the condition where salary is greater than 55000.
  
  Name  | Salary
------|--------
Mary  | 60000
James | 65000



Group bY

Filter
