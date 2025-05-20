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
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```
select student_name,grade
from grades g
where grade=(
select max(grade)
from grades
where subject=g.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/c7c06899-ccb0-4d86-bb12-998aa16a1fe5)



**Question 2**
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

```
select * from customers 
where address='Delhi';

```

**Output:**

![image](https://github.com/user-attachments/assets/1533f256-bcd1-4862-a634-a90f45ef269b)

**Question 3**
Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer 

```
select name from customer 
where phone in (
select phone from customer 
group by phone
having count(*)=1);

```

**Output:**

![image](https://github.com/user-attachments/assets/3b9f3cbc-565f-4be7-8228-d1320833fbd5)

**Question 4**
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.


```
select student_name,grade from grades g 
where grade=(
select min(grade)
from grades
where subject=g.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/a33c5abe-1d46-4191-85b9-00adb8acebcd)


**Question 5**
From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count.

```
SELECT grade, COUNT(*)
FROM customer
WHERE grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York')
group by grade;

```

**Output:**

![image](https://github.com/user-attachments/assets/5fd8a955-e5ba-498b-8916-319e15d88aa9)


**Question 6**
Write a SQL query to List departments with names longer than the average length

```
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

![image](https://github.com/user-attachments/assets/97396ef1-227f-4595-9c98-3df0671b22d3)



**Question 7**
From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```
SELECT ord_no, purch_amt, ord_date, customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';

```

**Output:**

![image](https://github.com/user-attachments/assets/e96774d8-7d68-4623-b263-f676b3c9b7f9)



**Question 8**
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

```
select * from employee 
where age<(
select avg(age)
from employee
where income>1000000);
```

**Output:**
![image](https://github.com/user-attachments/assets/e6ab7e70-a088-47eb-8597-83ee1e5d5584)


**Question 9**
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

```
select * from grades g
where grade=(
select max(grade)
from grades
where subject=g.subject);
```

**Output:**

![image](https://github.com/user-attachments/assets/21879361-1994-4c93-8cf4-15ae87d1d407)



**Question 10**
From the following tables write a SQL query to find salespeople who had more than one customer. Return salesman_id and name.

```
SELECT s.salesman_id, s.name
FROM salesman s
JOIN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
) c ON s.salesman_id = c.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/f9f04aa5-8aaa-4649-933a-ff0a0c235487)




## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
