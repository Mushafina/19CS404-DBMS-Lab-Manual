# Experiment 3: DML Commands

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
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```sql
update suppliers 
set supplier_name=upper(supplier_name)
where contact_person like '%SINGH%';
```

**Output:**
![image](https://github.com/user-attachments/assets/41f6e757-ce4c-4842-b1b9-61323bc47dcc)


**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
update products 
set product_name='Premium Bread'
where product_id=5;
```

**Output:**
![image](https://github.com/user-attachments/assets/06a8e324-32c0-44bd-a3df-2c365b24c927)


**Question 3**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT    

```sql
update products 
set sell_price=sell_price*1.15
where quantity<50 and supplier_id=10;
```

**Output:**

![image](https://github.com/user-attachments/assets/e15161b0-0e6f-4258-baf6-4c6516013e90)

**Question 4**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```sql
update employees 
set salary=salary+500,email='updated'
where job_id='SA_REP' and commission_pct>0.15;
```

**Output:**

![image](https://github.com/user-attachments/assets/311c33d6-30f0-4fd2-95fe-3b2787789e03)

**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
delete from doctors where last_name is null;
```

**Output:**

![image](https://github.com/user-attachments/assets/4aaae89c-bea6-445d-8a6c-4ed3a6bc0b86)


**Question 6**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

```sql
delete from customer 
where upper(cust_country) ='UK' 
and upper(working_area)='LONDON' 
and grade<3;
```

**Output:**
![image](https://github.com/user-attachments/assets/5fbd67c3-c529-4fe8-a7b9-264669945757)


**Question 7**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

```sql
delete from customer 
where grade=2 and upper(cust_name) like '%M%' and payment_amt<3000;
```

**Output:**

![image](https://github.com/user-attachments/assets/b05bb3d0-d809-45ac-a867-a9bad070b38c)


**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
delete from doctors 
where specialization is null;
```

**Output:**

![image](https://github.com/user-attachments/assets/cde3788e-53ea-4149-97fd-3374704f9f30)


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
delete from customer 
where (cust_country) not in ('India','USA');
```

**Output:**

![image](https://github.com/user-attachments/assets/bf44666c-a2ce-4385-9b35-fc9ab94f38b4)


**Question 10**
---
Write a query to fetch 5 to 9 records from EmployeeInfo table.

```sql
select * from employeeinfo 
where EmpID between 5 and 9;
```

**Output:**

![image](https://github.com/user-attachments/assets/9888b1f4-3e7b-46b3-8915-6d0502fdb24f)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
