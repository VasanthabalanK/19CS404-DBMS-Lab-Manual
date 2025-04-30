# Experiment 4: Aggregate Functions, Group By and Having Clause
Name:Vasanthabalan K

Reg.No.:212224230296

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



For example:

Result
Frequency      TotalPrescriptions
-------------  ------------------
Every 3 weeks  1
Every 6 hours  1
Once           1
Once daily     4
Once daily at  1
Pending        1
Twice daily    1


```sql
-- SELECT 
  Frequency, 
  COUNT(*) AS TotalPrescriptions
FROM 
  Prescriptions
GROUP BY 
  Frequency;
```

**Output:**

![Screenshot 2025-04-30 215904](https://github.com/user-attachments/assets/98ea1ff5-8f5b-495b-a46c-adf147467158)


**Question 2**
---
--How many doctors specialize in each medical specialty?

Sample table:Doctors Table



For example:

Result
Specialty          TotalDocto
-----------------  ----------
Gastroenterology   1
Neurology          1
Obstetrics         3
Ophthalmology      1
Orthopedics        1
Pediatrics         2
Urology            1



```sql
-- SELECT 
  Specialty, 
  COUNT(*) AS TotalDocto
FROM 
  Doctors
GROUP BY 
  Specialty;
```

**Output:**

![Screenshot 2025-04-30 215913](https://github.com/user-attachments/assets/d586ce20-589c-4f01-b2fd-54e4863e939a)


**Question 3**
---
-- Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
fruit_name  lowest_quantity
----------  ---------------
Watermelon  15

```sql
-- SELECT 
  name AS fruit_name, 
  inventory AS lowest_quantity
FROM 
  fruits
ORDER BY 
  inventory ASC
LIMIT 1;
```

**Output:**
![Screenshot 2025-04-30 215919](https://github.com/user-attachments/assets/2984a3c6-805b-436f-85d2-e7d6b6687323)


**Question 4**
---
-- Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
-- SELECT 
  AVG(income) AS Average_Salary
FROM 
  employee;
```

**Output:**

![Screenshot 2025-04-30 215927](https://github.com/user-attachments/assets/304682ec-5b95-488f-8f34-7ae40c003c3c)


**Question 5**
---
-- Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
employees_count
---------------
8


```sql
-- SELECT 
  COUNT(*) AS employees_count
FROM 
  employee
WHERE 
  income > 50000;
```

**Output:**
![Screenshot 2025-04-30 215934](https://github.com/user-attachments/assets/845f9d3c-18b3-4022-8874-71d765900912)


**Question 6**
---
-- Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
total
----------
225


```sql
-- SELECT 
  SUM(inventory) AS total
FROM 
  fruits
WHERE 
  unit = 'LB';
```

**Output:**
![Screenshot 2025-04-30 215943](https://github.com/user-attachments/assets/8ec4b974-dac7-4164-b379-f52dd48d3a8f)


**Question 7**
---
-- Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1



For example:

Result
occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27


```sql
-- SELECT 
  occupation,
  SUM(workhour)
FROM 
  employee1
GROUP BY 
  occupation
HAVING 
  SUM(workhour) > 20;
```

**Output:**
![Screenshot 2025-04-30 215949](https://github.com/user-attachments/assets/8549d977-8cdd-49f9-ace3-1172859641a5)


**Question 8**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

Sample table: employee1



For example:

Result
jdate       AVG(workhour)
----------  -------------
2002.0      9.5


```sql
-- SELECT 
  jdate,
  AVG(workhour) AS "AVG(workhour)"
FROM 
  employee1
GROUP BY 
  jdate
HAVING 
  AVG(workhour) < 10;
```

**Output:**
![Screenshot 2025-04-30 215958](https://github.com/user-attachments/assets/05831ffb-646f-4d5f-86aa-aea29d825c7a)


**Question 9**
---
-- Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

Sample table: products



For example:

Result
category_id  Price
-----------  ----------
3            7.5


```sql
-- SELECT 
  category_id,
  MIN(price) AS Price
FROM 
  products
GROUP BY 
  category_id
HAVING 
  MIN(price) < 10;
```

**Output:**
![Screenshot 2025-04-30 220007](https://github.com/user-attachments/assets/b966282f-d99c-45e4-85f6-10794deb6540)


**Question 10**
---
--Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length
----------------
15.0


```sql
-- select avg(length(email)) as avg_email_length
from customer;
```

**Output:**
![Screenshot 2025-04-30 220205](https://github.com/user-attachments/assets/b8c0220a-1f57-4e5c-b592-00f67128c4f0)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
