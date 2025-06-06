
# 📘 DML Commands in SQL with Operators

## 🔹 What is DML?
DML (Data Manipulation Language) is used to manage data within database tables — including retrieving, inserting, updating, and deleting records.

---

## ✅ DML Commands

### 🔸 INSERT – Add Records
**Syntax:**
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```
**Example:**
```sql
INSERT INTO users (password, name)
VALUES ('1234', 'Sobhit');
```

---

### 🔸 SELECT – Retrieve Records
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Examples:**
```sql
SELECT * FROM users;
SELECT DISTINCT c_name FROM customers;
SELECT DISTINCT c_name, b_name FROM sales;
```

---

### 🔸 UPDATE – Modify Records
**Syntax:**
```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```
**Example:**
```sql
UPDATE customers
SET c_name = 'Random'
WHERE b_name = 'Okay';
```

---

### 🔸 DELETE – Remove Records
**Syntax:**
```sql
DELETE FROM table_name
WHERE condition;
```
**Example:**
```sql
DELETE FROM products
WHERE price > 10000;
```

> ⚠️ Always use `WHERE` with UPDATE and DELETE to avoid affecting all rows.

---

## 🔹 SQL Operators (Used in WHERE Clauses)

### 🔸 Comparison Operators
| Operator | Description              | Example                        |
|----------|--------------------------|--------------------------------|
| =        | Equal                    | `WHERE age = 25`               |
| != or <> | Not equal                | `WHERE status != 'active'`     |
| >        | Greater than             | `WHERE price > 10000`          |
| <        | Less than                | `WHERE age < 18`               |
| >=       | Greater than or equal to | `WHERE score >= 80`            |
| <=       | Less than or equal to    | `WHERE age <= 60`              |

---

### 🔸 Logical Operators
| Operator | Description                       | Example                                      |
|----------|-----------------------------------|----------------------------------------------|
| AND      | Both conditions must be true      | `WHERE age > 18 AND city = 'Delhi'`          |
| OR       | At least one condition is true    | `WHERE city = 'Delhi' OR city = 'Mumbai'`    |
| NOT      | Condition must be false           | `WHERE NOT status = 'inactive'`              |

---

### 🔸 BETWEEN, IN, LIKE, IS NULL
| Operator  | Description                       | Example                                     |
|-----------|-----------------------------------|---------------------------------------------|
| BETWEEN   | Range check                       | `WHERE price BETWEEN 1000 AND 5000`         |
| IN        | Match any value in a list         | `WHERE city IN ('Delhi', 'Mumbai')`         |
| LIKE      | Pattern matching                  | `WHERE name LIKE 'S%'`                      |
| IS NULL   | Null value check                  | `WHERE phone IS NULL`                       |

**LIKE Wildcards:**
- `%` → Any number of characters  
- `_` → Single character

---

## 🧠 Combined Example
```sql
SELECT * FROM users
WHERE age BETWEEN 18 AND 30
  AND city IN ('Delhi', 'Bangalore')
  AND name LIKE 'S%';
```

---

## 🔐 Best Practices
- Always use `WHERE` with `UPDATE` and `DELETE`.
- Use `DISTINCT` to avoid duplicates in SELECT.
- Backup before mass data operations.
- Use transactions for critical changes (`BEGIN`, `COMMIT`, `ROLLBACK`).
