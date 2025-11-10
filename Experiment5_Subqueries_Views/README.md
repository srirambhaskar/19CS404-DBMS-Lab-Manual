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
--
-- From the following tables, write a SQL query to find all the orders issued by the salesman 'Paul Adam'. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

salesman table

```sql
--
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM Orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM Salesman
    WHERE name = 'Paul Adam'
);

```

**Output:**

![image](https://github.com/user-attachments/assets/509162b1-2ecc-4e89-ad17-496bd4607a38)


**Question 2**
---
-- 
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30
```sql
--
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

![image](https://github.com/user-attachments/assets/7e313fb0-07e5-46b3-a239-0ee13bb2649b)


**Question 3**
---
--
Write a SQL query to List departments with names longer than the average length
```sql
--
SELECT 
    department_id AS depar, 
    department_name
FROM 
    Departments
WHERE 
    LENGTH(department_name) > (
        SELECT AVG(LENGTH(department_name)) FROM Departments
    );

```

**Output:**

![image](https://github.com/user-attachments/assets/ee83ff18-13e8-4bf6-84c4-af8285fb94c9)


**Question 4**
---
--
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.
```sql
--
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

![image](https://github.com/user-attachments/assets/ed9615a8-b1f8-4a0f-bee6-2c196c5860ea)


**Question 5**
---
-- From the following tables write a SQL query to count the number of customers with grades above the average in New York City. Return grade and count

```sql
--
SELECT grade, COUNT(*)
FROM customer
GROUP BY grade
HAVING grade >
    (SELECT AVG(grade)
     FROM customer
     WHERE city = 'New York');
```

**Output:**

![image](https://github.com/user-attachments/assets/9fe8c8cc-bc45-4fd9-9fab-8d0995a687ba)


**Question 6**
---
--
From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.
```sql
--
SELECT commission 
FROM salesman 
WHERE salesman_id IN 
(SELECT salesman_id FROM customer WHERE city = 'Paris');

```

**Output:**

![image](https://github.com/user-attachments/assets/c78010d6-7580-4068-91b6-df2feef9341a)


**Question 7**
---
-- 
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.
```sql
--
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);
```

**Output:**
![image](https://github.com/user-attachments/assets/20560466-dbe5-453f-8d51-61be13b7fef9)


**Question 8**
---
-- 
Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.
```sql
--
SELECT name
FROM customer c
WHERE phone IN (
    SELECT phone
    FROM customer
    GROUP BY phone
    HAVING COUNT(phone) = 1
);

```

**Output:**

![image](https://github.com/user-attachments/assets/50d5755d-73b4-458e-8815-255010084c50)


**Question 9**
---
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the maximum grade achieved in each subject.

```sql
--
SELECT 
    student_name, 
    grade
FROM 
    GRADES g
WHERE 
    grade = (
        SELECT MAX(grade)
        FROM GRADES
        WHERE subject = g.subject
    );

```

**Output:**

![image](https://github.com/user-attachments/assets/8da84011-e4a8-40bc-9898-61d85e033617)


**Question 10**
---
--
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.
```sql
--
select ID,NAME,AGE,ADDRESS,SALARY
from CUSTOMERS
where salary>4500;
```

**Output:**

![image](https://github.com/user-attachments/assets/d09513eb-723b-4adc-be66-fe65b8acddab)


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
