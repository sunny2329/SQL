
# 🪟 SQL Window Functions - Detailed Notes

## 🔍 What Are Window Functions in SQL?
**Window functions** perform calculations across a set of table rows related to the current row. Unlike aggregate functions, they do not collapse rows — they add additional computed columns while preserving the original rows.

> Syntax:
```sql
function_name([expression]) OVER (
    [PARTITION BY partition_expression]
    [ORDER BY order_expression]
    [ROWS/RANGE frame_spec]
)
```

---

## 📘 Why Use Window Functions?
- To calculate **running totals**, **ranks**, **moving averages**, **row comparisons**, etc.
- They **retain individual rows** unlike `GROUP BY`.

---

## 📚 Key Concepts

### 1. OVER() Clause
Defines the window of rows to operate on.

### 2. PARTITION BY
Splits data into logical groups ("windows"). Like `GROUP BY`, but only applies to the window function.

### 3. ORDER BY (within OVER)
Specifies the order of rows within each partition.

---

## 🔑 Common SQL Window Functions

### 1. ROW_NUMBER()
Gives a unique sequential number to rows in a partition.

```sql
SELECT employee_id, department_id, salary,
  ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS row_num
FROM employees;
```
**Explanation:** Ranks employees in each department by salary. No ties — strictly sequential.

### Edge Case:
If two employees have the same salary, they get different row numbers.

---

### 2. RANK() vs DENSE_RANK()

```sql
SELECT employee_id, department_id, salary,
  RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rank,
  DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dense_rank
FROM employees;
```
**Explanation:**
- `RANK()` skips ranks after ties.
- `DENSE_RANK()` does not skip.

### Example:
If salaries are [1000, 1000, 900], ranks will be:
- `RANK()`: 1, 1, 3
- `DENSE_RANK()`: 1, 1, 2

---

### 3. LAG() and LEAD()
Used to fetch values from previous/next rows.

#### LAG():
```sql
SELECT employee_id, salary,
  LAG(salary, 1) OVER (ORDER BY employee_id) AS prev_salary
FROM employees;
```
**Use Case:** Compare current salary to previous one.

#### LEAD():
```sql
SELECT employee_id, salary,
  LEAD(salary, 1) OVER (ORDER BY employee_id) AS next_salary
FROM employees;
```
**Use Case:** Predict future values.

### Edge Case:
Returns NULL if there is no previous or next row.

---

### 4. NTILE(n)
Divides the result set into n equal buckets.

```sql
SELECT employee_id, salary,
  NTILE(4) OVER (ORDER BY salary DESC) AS quartile
FROM employees;
```
**Use Case:** Segment users/salaries into percentiles.

### Edge Case:
Rows may not be evenly distributed if total rows % n != 0.

---

### 5. Aggregate Functions with OVER()

#### Running Total:
```sql
SELECT employee_id, salary,
  SUM(salary) OVER (ORDER BY employee_id) AS running_total
FROM employees;
```

#### Average by Department:
```sql
SELECT employee_id, department_id, salary,
  AVG(salary) OVER (PARTITION BY department_id) AS avg_salary
FROM employees;
```

### Edge Case:
No `GROUP BY` needed, and all rows are preserved.

---

### 6. FIRST_VALUE() and LAST_VALUE()

```sql
SELECT employee_id, department_id, salary,
  FIRST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary DESC) AS highest,
  LAST_VALUE(salary) OVER (PARTITION BY department_id ORDER BY salary DESC 
    ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS lowest
FROM employees;
```

**Note:** LAST_VALUE() can give wrong results if frame is not defined.

---

## 🎯 Frame Specifications (ROWS vs RANGE)

```sql
ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
```

### Example:
```sql
SELECT employee_id, salary,
  SUM(salary) OVER (ORDER BY employee_id ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS moving_sum
FROM employees;
```

**Explanation:** Calculates sum of current and previous 2 rows.

---

## 🧪 Full Use Case Example

**Table: sales**

| id | salesman | region | amount | sale_date  |
|----|----------|--------|--------|------------|
| 1  | Alice    | East   | 500    | 2023-01-01 |
| 2  | Bob      | East   | 700    | 2023-01-02 |
| 3  | Alice    | East   | 400    | 2023-01-03 |
| 4  | Charlie  | West   | 600    | 2023-01-01 |
| 5  | Alice    | East   | 900    | 2023-01-04 |

#### 1. Cumulative Sales:
```sql
SELECT salesman, amount, sale_date,
  SUM(amount) OVER (PARTITION BY salesman ORDER BY sale_date) AS cumulative_sales
FROM sales;
```

#### 2. Previous Sale:
```sql
SELECT salesman, amount, sale_date,
  LAG(amount, 1) OVER (PARTITION BY salesman ORDER BY sale_date) AS previous_sale
FROM sales;
```

#### 3. Regional Rank:
```sql
SELECT salesman, region, amount,
  RANK() OVER (PARTITION BY region ORDER BY amount DESC) AS region_rank
FROM sales;
```

---

## 🧠 Common Interview Questions

1. What's the difference between `RANK()` and `DENSE_RANK()`?
2. How is `LAG()` different from `LEAD()`?
3. Can you explain `PARTITION BY` and its role?
4. What’s the difference between `ROWS` and `RANGE`?
5. How does `FIRST_VALUE()` behave without frame clause?
6. Write a query to find salary difference between two consecutive months for each employee.

---

## ✅ Summary Table

| Function         | Description                                 |
|------------------|---------------------------------------------|
| `ROW_NUMBER()`    | Unique number per partition/order           |
| `RANK()`          | Ranks with gaps                             |
| `DENSE_RANK()`    | Ranks without gaps                          |
| `LAG()`           | Previous row’s value                        |
| `LEAD()`          | Next row’s value                            |
| `NTILE(n)`        | Divides into n buckets                      |
| `SUM(), AVG()`    | Aggregates over window                      |
| `FIRST_VALUE()`   | First value in partition                    |
| `LAST_VALUE()`    | Last value (define frame!)                  |
