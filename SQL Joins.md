# SQL Joins and Set Operations

## Overview

SQL joins are used to combine rows from two or more tables based on a related column. This document includes detailed information on all types of joins, set operations like UNION and EXCEPT, and the correct order of writing SQL queries.

---

## 1. Types of Joins

### 1.1 INNER JOIN
Returns records that have matching values in both tables.

#### Syntax:
```sql
SELECT a.*, b.*
FROM table1 a
INNER JOIN table2 b ON a.id = b.id;
```

#### Example:
```sql
-- Get the names of employees and their department names
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

### 1.2 LEFT JOIN (or LEFT OUTER JOIN)
Returns all records from the left table, and the matched records from the right table.

#### Example:
```sql
-- Get all employees and their department names, even if they don’t belong to a department
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.id;
```

### 1.3 RIGHT JOIN (or RIGHT OUTER JOIN)
Returns all records from the right table, and the matched records from the left table.

#### Example:
```sql
-- Get all departments and the names of employees in them, even if no employee is assigned
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.id;
```

### 1.4 FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

#### Example:
```sql
-- Get a full list of employees and departments, including unmatched records
SELECT employees.name, departments.department_name
FROM employees
FULL OUTER JOIN departments ON employees.department_id = departments.id;
```

### 1.5 CROSS JOIN
Returns the Cartesian product of the two tables.

#### Example:
```sql
-- Get all combinations of customers and products
SELECT customers.name, products.product_name
FROM customers
CROSS JOIN products;
```

### 1.6 SELF JOIN
A table is joined with itself.

#### Example:
```sql
-- List employees and their managers
SELECT A.name AS Employee, B.name AS Manager
FROM employees A
JOIN employees B ON A.manager_id = B.id;
```

---

## 2. Joining Three Tables

Join multiple tables by chaining joins together.

#### Example:
```sql
-- Get employees with their department name and the city of the department
SELECT e.name AS Employee, d.department_name, l.city
FROM employees e
JOIN departments d ON e.department_id = d.id
JOIN locations l ON d.location_id = l.id;
```

---

## 3. Set Operators

### 3.1 UNION
Combines the result of two queries and removes duplicates.

#### Example:
```sql
-- Get a distinct list of names from employees and customers
SELECT name FROM employees
UNION
SELECT name FROM customers;
```

### 3.2 UNION ALL
Same as UNION but **includes duplicates**.

#### Example:
```sql
-- Get all names from employees and customers, including duplicates
SELECT name FROM employees
UNION ALL
SELECT name FROM customers;
```

### 3.3 EXCEPT (or MINUS in Oracle)
Returns rows from the first query that are not in the second query.

#### Example:
```sql
-- Get names of employees who are not customers
SELECT name FROM employees
EXCEPT
SELECT name FROM customers;
```

---

## 4. SQL Query Execution Order

Although you write SQL in a specific order, the **logical processing order** is:

1. `FROM` (including `JOIN`)
2. `WHERE`
3. `GROUP BY`
4. `HAVING`
5. `SELECT`
6. `DISTINCT`
7. `ORDER BY`
8. `LIMIT` / `OFFSET`

### Example:
```sql
SELECT department, COUNT(*) as emp_count
FROM employees
WHERE active = true
GROUP BY department
HAVING COUNT(*) > 5
ORDER BY emp_count DESC;
```

- `FROM employees` → Selects the table
- `WHERE active = true` → Filters rows
- `GROUP BY department` → Groups remaining rows
- `HAVING COUNT(*) > 5` → Filters groups
- `SELECT` → Picks required columns
- `ORDER BY` → Sorts results

---

## 5. Tips

- Always specify join conditions to avoid Cartesian products (unless using CROSS JOIN intentionally).
- Use table aliases for clarity when joining multiple tables.
- When using `GROUP BY`, use `HAVING` to filter groups instead of `WHERE`.

---

## 6. Use Cases

- Join `orders`, `customers`, and `products` tables to display complete transaction details.
- Use `UNION` to combine search results from two sources.
- Use `EXCEPT` to identify missing entries between datasets.

---

## Conclusion

Understanding joins and set operations helps you combine and analyze data across multiple tables effectively. Use the correct syntax and execution order to avoid performance issues and logical errors.
