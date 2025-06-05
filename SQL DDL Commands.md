
# 📘 SQL Commands & Concepts (MySQL)

---

## 🔢 Types of SQL Commands

1. **DDL (Data Definition Language)** – *Defines or alters the structure of the database.*
   - `CREATE`, `ALTER`, `DROP`, `TRUNCATE`

2. **DCL (Data Control Language)** – *Controls access to data.*
   - `GRANT`, `REVOKE`

3. **DML (Data Manipulation Language)** – *Manipulates data inside the tables.*
   - `INSERT`, `UPDATE`, `DELETE`

4. **TCL (Transaction Control Language)** – *Manages transactions.*
   - `COMMIT`, `ROLLBACK`, `SAVEPOINT`

5. **DRL (Data Retrieval Language)** – *Used to fetch data from a database.*
   - `SELECT`

---

## 🏗️ DDL Commands

### 📌 Database Operations

```sql
CREATE DATABASE db_name;
CREATE DATABASE IF NOT EXISTS db_name;

DROP DATABASE db_name;
DROP DATABASE IF EXISTS db_name;
```

### 📌 Table Operations

```sql
-- Create a table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100)
);

-- Drop a table
DROP TABLE users;
DROP TABLE IF EXISTS users;

-- Truncate (remove all rows but keep structure)
TRUNCATE TABLE users;
```

---

## 🔁 ALTER TABLE Statements

```sql
-- Add a column
ALTER TABLE users ADD COLUMN age INT AFTER name;

-- Drop a column
ALTER TABLE users DROP COLUMN age;

-- Modify column datatype
ALTER TABLE users MODIFY COLUMN name VARCHAR(150);

-- Rename a table
ALTER TABLE users RENAME TO customers;
```

---

## 🧱 Constraints in MySQL

Constraints are rules applied to columns to enforce data integrity.

| Constraint      | Description |
|-----------------|-------------|
| `NOT NULL`      | Ensures column can't have NULL value |
| `UNIQUE`        | Ensures all values are unique |
| `PRIMARY KEY`   | Uniquely identifies each row (NOT NULL + UNIQUE) |
| `AUTO_INCREMENT`| Automatically increases integer value |
| `CHECK`         | Validates data against a condition |
| `DEFAULT`       | Sets default value if none is provided |
| `FOREIGN KEY`   | Links one table to another |

---

### ✅ Examples

```sql
-- UNIQUE constraint
CONSTRAINT user_email UNIQUE (email);

-- PRIMARY KEY
id INT PRIMARY KEY

-- FOREIGN KEY
FOREIGN KEY (dept_id) REFERENCES departments(dept_id)

-- CHECK constraint
CHECK (age >= 18)

-- DEFAULT value
status VARCHAR(20) DEFAULT 'active'
```

---

## 🔗 Foreign Key in Detail

```sql
CREATE TABLE departments (
  dept_id INT PRIMARY KEY,
  dept_name VARCHAR(100)
);

CREATE TABLE employees (
  emp_id INT PRIMARY KEY,
  emp_name VARCHAR(100),
  dept_id INT,
  FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

You can also use:

```sql
ON DELETE CASCADE
ON UPDATE CASCADE
```

To propagate changes from parent to child table.

---

## 🧠 Best Practices

- Always define `PRIMARY KEY` in every table.
- Use `IF EXISTS` / `IF NOT EXISTS` to avoid errors on create/drop.
- Normalize tables and use `FOREIGN KEYS` to reduce redundancy.
- Use `TRUNCATE` for quick data deletion without logging individual deletes.

---

## 🔍 Quick Reference

| Command       | Use |
|---------------|-----|
| `CREATE`      | Create new DB/table/column |
| `ALTER`       | Modify table structure |
| `DROP`        | Delete table/database |
| `TRUNCATE`    | Remove all data from a table |
| `INSERT`      | Add data to a table |
| `UPDATE`      | Modify existing data |
| `DELETE`      | Remove specific data |
| `SELECT`      | Retrieve data |
| `GRANT/REVOKE`| Manage permissions |
| `COMMIT`      | Save transaction |
| `ROLLBACK`    | Undo uncommitted changes |
