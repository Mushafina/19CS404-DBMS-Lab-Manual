# Experiment 4: Aggregate Functions, Group By and Having Clause
## Name: R.Mushafina
## Reg.No : 212224220067
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
Write a SQL query to  find the average salary of all employees?
~~~

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
~~~
~~~
SELECT AVG(income) AS Average_Salary
FROM employee;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/fed8cfc8-41ca-4580-9e56-6997f450eaa5)


**Question 2**
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1
![image](https://github.com/user-attachments/assets/8670e8dc-537c-4836-b33f-fbfe31675d9d)
~~~
SELECT SUM(workhour) AS 'Total working hours'
FROM  employee1;
~~~


**Output:**

![image](https://github.com/user-attachments/assets/b4340e8f-832f-4fe7-951a-cc2a87aea425)


**Question 3**
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer
~~~

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
~~~
~~~
SELECT COUNT(customer_id) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
~~~

**Output:**
![image](https://github.com/user-attachments/assets/85c50c99-0953-4c04-815d-412ab6d079a3)



**Question 4**

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.
Sample table: employee1

~~~
SELECT jdate,MIN(workhour) AS  'MIN(workhour)'
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/03b60ef7-4969-4337-abf5-34b06025e263)

**Question 5**
Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee

![image](https://github.com/user-attachments/assets/15eaa93f-2263-40b6-bd81-7488b1f2a65c)
~~~
SELECT age, MAX(income) AS 'MAX(income)'
FROM employee
GROUP BY age
HAVING MAX(income) > 2000000;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/f37a3da9-6e90-419f-befc-d0eeeb1fa312)


**Question 6**
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

Sample table: products

![image](https://github.com/user-attachments/assets/042e49b9-6623-459e-b953-57088965246d)

~~~
SELECT category_id, COUNT(*) AS COUNT
FROM products
WHERE category_id > 2
GROUP BY category_id;
~~~

**Output:**
![image](https://github.com/user-attachments/assets/8c58d744-9066-432c-9f73-1eda446f66df)



**Question 7**
Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

![image](https://github.com/user-attachments/assets/271b0f32-9d6b-4026-a0bc-79ff2b2a9b72)
~~~
SELECT PatientID,COUNT(medications) AS AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/a2a7478f-ab2e-4af6-be6d-959084185afb)

**Question 8**
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?
Sample tablePrescriptions Table
![image](https://github.com/user-attachments/assets/63e13b53-4879-4a1e-ad4c-4057ba1ef7c1)
~~~
SELECT Frequency,COUNT(Frequency) AS  TotalPrescriptions
FROM Prescriptions 
GROUP BY Frequency;
~~~

**Output:**

![image](https://github.com/user-attachments/assets/f01920a5-ee06-4a9c-8864-aa5d6f8700ad)


**Question 9**
What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table
![image](https://github.com/user-attachments/assets/e1c0ca74-ec1a-4d65-8081-36ae3dc39099)
~~~
SELECT DoctorID,COUNT(*) AS TotalAppointments
FROM Appointments 
GROUP BY DoctorID;
~~~

**Output:**
![image](https://github.com/user-attachments/assets/e24bca3c-0a16-4ca7-9e86-674bb675844a)



**Question 10**
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.
Sample table: customer
![image](https://github.com/user-attachments/assets/dbb27646-4b8d-4c18-8827-5659cfae35fe)
~~~
select count(city)as COUNT
from customer
where city='Noida';
~~~


**Output:**
![image](https://github.com/user-attachments/assets/04e98da2-e773-4544-8c2b-6bdca5090687)





## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
