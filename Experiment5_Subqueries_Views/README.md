# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 
```
select o.ord_no,o.ord_date,o.purch_amt,c.cust_name as "Customer Name",c.grade,s.name as "Salesman",s.commission
from orders o
join customer c on o.customer_id=c.customer_id
join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/730d4ffe-f876-43f6-a1c4-a2b8374e6dd3)


**Question 2**
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

```
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/b90a0a79-bef2-4acd-a7a9-4b8ad16cdda1)

**Question 3**
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

![image](https://github.com/user-attachments/assets/3b9f3cbc-565f-4be7-8228-d1320833fbd5)

**Question 4**
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

```
SELECT 
    c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt
from 
    customer c 
left join orders o on c.customer_id=o.customer_id
where c.city="London";
```

**Output:**

![image](https://github.com/user-attachments/assets/06a0c918-5627-4120-9a31-d6304ea83115)


**Question 5**
Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```
select p.first_name as "patient_name",d.first_name as "doctor_name" 
from patients p 
inner join doctors d on p.doctor_id=d.doctor_id
where p.discharge_date is not null;
```

**Output:**

![image](https://github.com/user-attachments/assets/454d40fd-7ee2-45b6-9c60-d12d742aecec)


**Question 6**
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```
SELECT 
    p.first_name AS patient_name
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';

```

**Output:**

![image](https://github.com/user-attachments/assets/f1be90e6-dad5-416e-b651-058404b99405)


**Question 7**
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column.

```
select c.cust_name from customer c
left join orders o on c.customer_id=o.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/9cceefaa-da00-495b-9d4e-fc79af9d499a)


**Question 8**
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```
select c.cust_name,c.city,c.grade,s.name as "Salesman",s.city
from customer c
join salesman s on c.salesman_id=s.salesman_id
where c.grade<300
order by customer_id asc;
```

**Output:**

![image](https://github.com/user-attachments/assets/8fc9d9c5-443e-4cd1-8957-dde1103170ed)


**Question 9**
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31

```
select p.first_name as patient_name,t.result_id,t.patient_id,t.test_name,t.result,t.test_date
from patients p
inner join test_results t on p.patient_id=t.patient_id
where p.admission_date between '2024-01-01' and '2024-01-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/64fcc645-0d3a-440c-a493-1f7e3aada131)


**Question 10**
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```
select s.name as Salesman,c.cust_name,c.city
from salesman s
inner join customer c on s.city=c.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/4343c1da-6888-45c7-84f7-383f9bbd7bf2)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
