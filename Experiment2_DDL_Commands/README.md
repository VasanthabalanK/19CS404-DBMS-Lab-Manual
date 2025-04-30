# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
For example:

Test	Result
pragma table_info('Student_details');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      int         0                       1
1           Name        VARCHAR(10  1                       0
2           Gender      TEXT        1                       0
3           Subject     VARCHAR(30  0                       0
4           MARKS       INT (3)     0                       0
5           State       TEXT        0                       0


```sql
-- alter table Student_details add column State TEXT
```

**Output:**

![Screenshot 2025-04-30 204033](https://github.com/user-attachments/assets/e82e75b2-70ed-4254-9ef9-1242a4938039)


**Question 2**
---
--Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700         COM5

```sql
-- create table item(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
foreign key(icom_id)references company(com_id)
on update cascade
on delete cascade);
```

**Output:**

![Screenshot 2025-04-30 204046](https://github.com/user-attachments/assets/dd0e0d58-407d-4b20-a0aa-e7ab3bbdeb03)


**Question 3**
---
-- Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

For example:

Test	Result
SELECT * FROM Employee WHERE EmployeeID = 001;
EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
1           Sarah Parker  Manager     HR          60000


```sql
-- insert into Employee(EmployeeID,Name,Position,Department,Salary)
values('001','Sarah Parker','Manager','HR',60000);
```

**Output:**

![Screenshot 2025-04-30 204056](https://github.com/user-attachments/assets/21008683-695f-480a-b9f5-a473a2943534)


**Question 4**
---
-- Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
For example:

Test	Result
INSERT INTO products (product_id, product_name, list_price) VALUES (2, 'Product B', 50.00);
SELECT * FROM products;
product_id  product_name  list_price  discount
----------  ------------  ----------  ----------
2           Product B     50          0


```sql
--create table products(
product_id integer primary key,
product_name text not null,
list_price decimal(10,2) not null check (list_price>=0),
discount decimal(10,2) not null default 0 check (discount>=0),
check(list_price>=discount));

```

**Output:**

![Screenshot 2025-04-30 204113](https://github.com/user-attachments/assets/e7d98054-45f0-4f36-97e0-ff9327cbb3b0)


**Question 5**
---
-- Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
For example:

Test	Result
INSERT INTO Products
VALUES (1, NULL,0,5);
Error: NOT NULL constraint failed: Products.ProductName


```sql
-- create table Products(
ProductID integer primary key,
ProductName text not null,
Price real check(Price>0),
Stock integer check(Stock>=0));
```

**Output:**

![Screenshot 2025-04-30 204123](https://github.com/user-attachments/assets/0290a417-7354-4653-97aa-88b8f7c86dd7)


**Question 6**
---
-- Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78

 

 

For example:

Test	Result
SELECT * FROM Student_details;
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202         Ella King   F           Chemistry   87
203         James Bond  M           Literature  78

```sql
-- insert into Student_details(RollNo,Name,Gender,Subject,MARKS)
values(202,'Ella King','F','Chemistry',87),
(203,'James Bond','M','Literature',78);
```

**Output:**
![Screenshot 2025-04-30 204559](https://github.com/user-attachments/assets/bdff4c45-1f06-4f02-8be1-7964c6580735)


**Question 7**
---
-- Write a SQL query to Add a new column Country as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
For example:

Test	Result
pragma table_info('Student_details');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      int         0                       1
1           Name        VARCHAR(10  1                       0
2           Gender      TEXT        1                       0
3           Subject     VARCHAR(30  0                       0
4           MARKS       INT (3)     0                       0
5           Country     TEXT        0                       0


```sql
-- alter table Student_details add column Country TEXT
```

**Output:**

![Screenshot 2025-04-30 204607](https://github.com/user-attachments/assets/ff5ae8aa-e20f-4cfd-bb98-c19366e1442b)


**Question 8**
---
-- Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER
For example:

Test	Result
pragma table_info('Products');
cid   name        type        notnull     dflt_value  pk
----  ----------  ----------  ----------  ----------  ----------
0     ProductID   INTEGER     0                       0
1     ProductNam  TEXT        0                       0
2     Price       REAL        0                       0
3     Stock       INTEGER     0                       0


```sql
-- create table Products(
ProductID INTEGER ,
ProductName TEXT ,
Price REAL check(Price>=0),
Stock INTEGER check(stock>=0));
```

**Output:**

![Screenshot 2025-04-30 204615](https://github.com/user-attachments/assets/86e4a9f7-2526-49e7-ae4b-6ad2d2e2df78)



**Question 9**
---
-- Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
For example:

Test	Result
select * from student_details;
RollNo      Name           Gender      Subject     MARKS
----------  -------------  ----------  ----------  ----------
1           Alice Johnson  Female      Math        85
2           Bob Smith      Male        Science     90
3           Charlie Brown  Male        English     78

```sql
-- insert into Student_details(RollNo,Name,Gender,Subject,MARKS)
select RollNo,Name,Gender,Subject,MARKS from Archived_students;
```

**Output:**

![Screenshot 2025-04-30 204624](https://github.com/user-attachments/assets/2da7b5ae-86c1-4185-8ceb-f87a62e97b6f)


**Question 10**
---
-- Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT
For example:

Test	Result
pragma table_info('Reviews');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           ReviewID    INTEGER     0                       0
1           ProductID   INTEGER     0                       0
2           Rating      REAL        0                       0
3           ReviewText  TEXT        0                       0

```sql
-- create table Reviews(
ReviewID  INTEGER,
ProductID  INTEGER,
Rating  REAL,
ReviewText  TEXT);
```

**Output:**


![Screenshot 2025-04-30 204818](https://github.com/user-attachments/assets/47ae8b31-4b34-4ba9-af68-ed3999e50be8)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
