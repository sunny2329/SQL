# SQL Subqueries

## Overview

A **subquery** (also called an inner query or nested query) is a query nested inside another SQL query. Subqueries can be used with `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statements and are often used to perform operations that require multiple steps.

---

## 1. Types of Subqueries

### 1.1 Scalar Subquery
Returns a single value (one row, one column).

#### Example:
```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
➡️ Retrieves employees whose salary is above average.

---

### 1.2 Column Subquery
Returns a single column of values.

#### Example:
```sql
SELECT name
FROM employees
WHERE department_id IN (SELECT id FROM departments WHERE location = 'New York');
```
➡️ Retrieves names of employees working in departments located in New York.

---

### 1.3 Row Subquery
Returns a single row of multiple columns.

#### Example:
```sql
SELECT name
FROM employees
WHERE (department_id, job_id) = (SELECT department_id, job_id FROM employees WHERE id = 101);
```
➡️ Retrieves employees with the same department and job as employee 101.

---

### 1.4 Table Subquery
Returns a full result set that can be used as a table.

#### Example:
```sql
SELECT name FROM (
    SELECT * FROM employees WHERE salary > 50000
) AS high_earners;
```
➡️ Subquery acts as a temporary table of high earners.

---

## 2. Subqueries in Different Clauses

### 2.1 Subquery in SELECT Clause
```sql
SELECT name, (SELECT COUNT(*) FROM tasks WHERE tasks.employee_id = employees.id) AS task_count
FROM employees;
```
➡️ Retrieves each employee's name along with the number of tasks assigned.

---

### 2.2 Subquery in FROM Clause
```sql
SELECT department_id, AVG(salary) AS avg_salary
FROM (SELECT * FROM employees WHERE active = true) AS active_emps
GROUP BY department_id;
```
➡️ Calculates average salary of active employees by department.

---

### 2.3 Subquery in WHERE Clause
```sql
SELECT name FROM employees
WHERE department_id = (SELECT id FROM departments WHERE department_name = 'IT');
```
➡️ Finds all employees in the IT department.

---

### 2.4 Subquery in HAVING Clause
```sql
SELECT department_id, COUNT(*) AS emp_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > (SELECT AVG(emp_count) FROM (
    SELECT department_id, COUNT(*) AS emp_count
    FROM employees
    GROUP BY department_id
) AS dept_counts);
```
➡️ Finds departments having more employees than the average number of employees per department.

---

## 3. Correlated Subqueries

A correlated subquery uses values from the outer query and is evaluated once per row.

### Example:
```sql
SELECT name, salary
FROM employees e
WHERE salary > (
    SELECT AVG(salary) FROM employees WHERE department_id = e.department_id
);
```
➡️ Retrieves employees earning more than the average salary of their own department.

---

## 4. Subquery vs JOIN

- Subqueries can be more readable for nested logic.
- Joins can often be more efficient.
- Use subqueries when filtering or computing based on derived results.

---

## Conclusion

Subqueries are powerful tools for solving complex problems in SQL. They let you modularize logic, compare results dynamically, and perform intermediate calculations within a single query.
