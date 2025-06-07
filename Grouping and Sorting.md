# SQL Grouping and Sorting

## Overview

Grouping and Sorting are essential operations in SQL that help you summarize and organize your query results.

---

## 1. GROUP BY Clause

The `GROUP BY` clause is used to arrange identical data into groups.

### Syntax:
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

### Example:
```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```
This groups employees by their department and counts the number of employees in each department.

### Common Aggregate Functions used with `GROUP BY`:
- `COUNT()` - counts rows
- `SUM()` - adds values
- `AVG()` - calculates average
- `MIN()` - gets minimum value
- `MAX()` - gets maximum value

### HAVING Clause
Used to filter groups (like WHERE, but for groups).
```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```
This filters the groups to only those departments with more than 10 employees.

---

## 2. ORDER BY Clause

The `ORDER BY` clause is used to sort the result set in ascending (default) or descending order.

### Syntax:
```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 [ASC|DESC];
```

### Example:
```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC;
```
This sorts employees by salary in descending order.

---

## 3. Combining GROUP BY and ORDER BY

You can use both clauses together to group data and then sort it.

### Example:
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC;
```
This gets the average salary per department and sorts departments by average salary in descending order.

---

## 4. Sorting by Multiple Columns

You can sort by multiple columns.
```sql
SELECT name, department, salary
FROM employees
ORDER BY department ASC, salary DESC;
```
This first sorts by department (A-Z), and within each department, by salary (high to low).

---

## 5. Tips

- `ORDER BY` always comes last in the SQL query.
- Use column aliases in `ORDER BY`.
- `HAVING` filters after `GROUP BY`; `WHERE` filters before `GROUP BY`.

---

## 6. Use Cases

- Grouping sales by region and sorting by total revenue.
- Summarizing website visits per day and ordering by highest traffic.
- Analyzing average grades per subject and sorting by best to worst.

---

## Conclusion

Grouping and Sorting are powerful tools in SQL to summarize, analyze, and present data in meaningful ways.
