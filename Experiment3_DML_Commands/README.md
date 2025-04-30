# Experiment 3: DML Commands
Name: Vasanthabalan K

Reg.No.:212224230296

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
-- Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
For example:

Test	Result
select changes();
changes()
-----------------
2


```sql
--UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh';
```

**Output:**



![Screenshot 2025-04-30 211557](https://github.com/user-attachments/assets/bf1b987a-2dd6-4400-8e14-1f9d9a6fdaa4)



**Question 2**
---
-- Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
For example:

Test	Result
select changes();
changes()
----------
4


```sql
-- UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 1.3 AS INT)
WHERE category = 'Food'
  AND quantity < 0.5 * reorder_lvl;
```

**Output:**



![Screenshot 2025-04-30 211604](https://github.com/user-attachments/assets/ac05869c-a8b1-4942-90e8-2046886fd4ed)


**Question 3**
---
-- Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

For example:

Test	Result
select changes();
changes()
----------
3


```sql
-- UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**


![Screenshot 2025-04-30 211614](https://github.com/user-attachments/assets/5419dab4-2f4f-4a6a-b4ad-2895a5dacfa0)



**Question 4**
---
-- Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
-- UPDATE customer
SET grade = 5
WHERE city = 'Chennai';
```

**Output:**


![Screenshot 2025-04-30 211648](https://github.com/user-attachments/assets/ec4ff696-c0a6-441f-b42b-635ce46745ea)



**Question 5**
---
-- Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
For example:

Test	Result
select changes();
changes()
----------
4


```sql
--UPDATE products
SET sell_price = ROUND(sell_price * 1.10, 2)
WHERE supplier_id = 6;

```

**Output:**



![Screenshot 2025-04-30 211659](https://github.com/user-attachments/assets/2861c2cf-858d-4889-b251-1aa9b9ff12ce)



**Question 6**
---
-- Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
4


```sql
-- DELETE FROM Customer
WHERE CUST_COUNTRY = 'UK'
  AND WORKING_AREA = 'London'
  AND GRADE < 3;
```

**Output:**


![Screenshot 2025-04-30 211707](https://github.com/user-attachments/assets/a2ee0838-6272-4a15-ac0d-6317955f09a2)



**Question 7**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(grade)from customer;
GRADE
----------
2
3
1
0
GRADE
----------
2
3


```sql
-- DELETE FROM customer
WHERE grade < 2;
```

**Output:**



![Screenshot 2025-04-30 211717](https://github.com/user-attachments/assets/ab1eda78-a134-44e6-8a8d-f0579d9cfdb7)



**Question 8**
---
-- Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
12


```sql
-- DELETE FROM customer
WHERE (grade > 2 AND payment_amt < (SELECT AVG(payment_amt) FROM customer))
   OR outstanding_amt > 8000;
```

**Output:**



![Screenshot 2025-04-30 211730](https://github.com/user-attachments/assets/077cfc52-b57b-459b-97ce-778061c83b22)



**Question 9**
---
-- Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin       Jones
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics


```sql
-- DELETE FROM doctors
WHERE specialization IS NULL;
```

**Output:**


![Screenshot 2025-04-30 211740](https://github.com/user-attachments/assets/6fb7d977-08f6-45be-8541-40ec3e21d4b3)


**Question 10**
---
-- Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology


```sql
-- DELETE FROM doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

**Output:**

![Screenshot 2025-04-30 211749](https://github.com/user-attachments/assets/6a062747-5c13-4acd-ba4e-797cb4257f84)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
