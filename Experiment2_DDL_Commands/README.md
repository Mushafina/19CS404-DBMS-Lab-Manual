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
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
create table Members (
MemberID INTEGER ,
MemberName TEXT,
JoinDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/aa0f51de-c8fd-4df9-9dc1-0ee31ec7b632)


**Question 2**
---
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

```sql
alter table customer rename column city to location; 
```

**Output:**
![image](https://github.com/user-attachments/assets/48819121-b7ce-404d-8344-091a639c43cd)

**Question 3**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

```sql
insert into Student_details(RollNo,Name,Gender)
values (204,'Samuel Black','M');
```

**Output:**
![image](https://github.com/user-attachments/assets/36e51993-fe2e-4f1e-8023-4b38943163b4)

**Question 4**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
create table Products (
ProductID integer primary key,
ProductName varchar not null,
Price real check(price>0),
Stock integer check(stock>=0));
```

**Output:**
![image](https://github.com/user-attachments/assets/e54f4d32-dbf7-4fe7-aece-342431c19159)


**Question 5**
---
Insert all students from Archived_students table into the Student_details table.

```sql
insert into Student_details(RollNo,name,Gender,SUbject,MARKS)
select RollNo,name,Gender,SUbject,MARKS from Archived_students;
```

**Output:**

![image](https://github.com/user-attachments/assets/6dce1c0d-b76e-4ee0-b237-bc8819e4e66b)

**Question 6**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
alter table employee rename column id to employee_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/4b044fc0-ecb7-455a-adc9-fdc79e6f39c8)


**Question 7**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
create table Orders(
OrderID integer primary key,
OrderDate date not NULL,
CustomerID integer,
foreign key (CustomerID) references Customers(CustomerID));
```

**Output:**
![image](https://github.com/user-attachments/assets/0559839e-a52f-4d73-9fb4-881346b8e2ab)


**Question 8**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Shipments(
ShipmentID integer primary key,
ShipmentDate date,
SupplierID integer,
OrderID integer,
foreign key(SupplierID) references Suppliers(SupplierID),
foreign key(OrderID) references Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/98c11c71-66e2-4959-b8f2-7e56f58a8ba4)


**Question 9**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values(5,'George Clark','Consultant',null,null)
,(7,'Noah Davis','Manager','HR',60000),
(8,'Ava Miller','Consultant','IT',null);
```

**Output:**

![image](https://github.com/user-attachments/assets/ffd871ff-9c79-49ce-af46-2cf21fe8f68a)


**Question 10**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs(
job_id integer primary key,
job_title varchar default '',
min_salary integer default 8000,
max_salary integer default null);
```

**Output:**

![image](https://github.com/user-attachments/assets/cad772ad-8719-4e98-813b-704beda58dc8)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
