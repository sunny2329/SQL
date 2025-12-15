# 📚 World-Class DB, DBMS & SQL Learning Roadmap

This roadmap is designed to take you from **zero → industry → architect-level mastery**
of **Databases, DBMS internals, and SQL**.

---

## 0. DBMS Fundamentals & Internals
- [ ] What is a DBMS? Roles & responsibilities
- [ ] Types of DBMS — Hierarchical, Network, Relational, Object-Oriented
- [ ] Data Models — Relational, ER, Object, Semi-Structured
- [ ] Database Architecture — Single-tier, Two-tier, Three-tier
- [ ] Storage & File Organization
  - Pages, extents, blocks
  - Heap files vs sorted files
  - Slotted page structure & record formats
- [ ] Buffer Management
  - Buffer pool
  - Page replacement (LRU, CLOCK)
  - Dirty pages & flushing
- [ ] Indexing Internals
  - B-Trees & B+ Trees
  - Hash indexes
  - Index-only scans
- [ ] Concurrency Control
  - Lock-based vs timestamp-based protocols
  - Lock granularity (row/page/table)
  - Shared, Exclusive & Intention locks
  - Lock escalation
- [ ] Deadlock Handling
  - Detection
  - Prevention
  - Avoidance
- [ ] Isolation Levels
  - Read Uncommitted, Read Committed
  - Repeatable Read, Serializable
  - Read phenomena (dirty, non-repeatable, phantom reads)
- [ ] MVCC (Multi-Version Concurrency Control)
  - Snapshot isolation
  - Versioning & visibility rules
- [ ] Transaction Management
  - ACID properties (deep dive)
  - Write-Ahead Logging (WAL)
- [ ] Recovery Management
  - Log-Based Recovery
  - Checkpointing
  - Crash & failure recovery
- [ ] Query Processing & Optimization
  - Parsing, rewriting, execution
  - Logical vs physical query plans
  - Cost-based optimization
  - Join algorithms (Nested Loop, Hash Join, Merge Join)
  - Predicate & projection pushdown

---

## 1. Introduction & SQL Basics
- [ ] Introduction to SQL & Relational Databases
- [ ] RDBMS vs NoSQL (use cases & tradeoffs)
- [ ] Client–Server DB model
- [ ] SQL Data Types
  - Numeric, Text
  - Date & Time
  - Boolean
  - JSON / XML
  - Binary
- [ ] SQL Constraints
  - PRIMARY KEY, FOREIGN KEY
  - UNIQUE, CHECK, DEFAULT, NOT NULL
  - ON DELETE / ON UPDATE rules
  - DEFERRABLE constraints
- [ ] NULL Semantics
  - Three-valued logic (TRUE/FALSE/UNKNOWN)
  - NULL in WHERE, JOIN, GROUP BY
  - COUNT(*) vs COUNT(column)

---

## 2. Core SQL Operations
- [ ] DDL — CREATE, ALTER, DROP
- [ ] DML — INSERT, UPDATE, DELETE
- [ ] DQL — SELECT basics
- [ ] Filtering Data
  - WHERE clause
  - Comparison & logical operators
- [ ] Sorting & Limiting
  - ORDER BY
  - LIMIT / OFFSET
  - DISTINCT

---

## 3. Functions & Aggregations
- [ ] SQL Functions overview
- [ ] Aggregate Functions
  - COUNT, SUM, AVG, MIN, MAX
- [ ] Scalar Functions
  - CONCAT, LENGTH
  - ROUND
  - UPPER / LOWER
  - Date & Time functions
- [ ] GROUP BY & HAVING

---

## 4. Joins & Advanced Queries
- [ ] JOIN types
  - INNER
  - LEFT / RIGHT
  - FULL OUTER
  - CROSS
  - SELF
- [ ] Subqueries
  - Single-row
  - Multi-row
  - Correlated subqueries
- [ ] Set Operations
  - UNION / UNION ALL
  - INTERSECT
  - EXCEPT (MINUS)
- [ ] CASE Statements & Conditional Logic

---

## 5. Views, Indexing & Performance
- [ ] Views
  - Creating & using views
  - Updatable vs non-updatable views
- [ ] Indexes
  - Clustered vs non-clustered
  - Composite indexes
  - Partial indexes
  - Covering indexes
- [ ] Query Performance Tuning
  - EXPLAIN & EXPLAIN ANALYZE
  - Execution plans
  - Index selection strategy
  - SQL anti-patterns
    - SELECT *
    - Functions on indexed columns
    - Excessive OR conditions

---

## 6. Transactions, Security & Control
- [ ] Transactions & ACID (practical examples)
- [ ] TCL — COMMIT, ROLLBACK, SAVEPOINT
- [ ] DCL — GRANT, REVOKE
- [ ] Roles & permissions
- [ ] SQL Injection prevention
  - Parameterized queries
  - Least privilege principle

---

## 7. CTEs, Window Functions & Programmability
- [ ] Common Table Expressions (CTEs)
  - Non-recursive
  - Recursive (hierarchical queries)
- [ ] Window Functions
  - ROW_NUMBER
  - RANK, DENSE_RANK
  - LAG, LEAD
  - Window frames
- [ ] Stored Procedures
  - Parameters
  - Returning results
- [ ] Triggers
  - BEFORE
  - AFTER
  - INSTEAD OF

---

## 8. Database Design & Optimization
- [ ] Database Normalization
  - 1NF, 2NF, 3NF, BCNF
- [ ] Relationships
  - One-to-One
  - One-to-Many
  - Many-to-Many
- [ ] Schema Design Best Practices
- [ ] When to denormalize
- [ ] Advanced Indexing
- [ ] Partitioning
  - Range
  - List
  - Hash
- [ ] Sharding basics

---

## 9. Data Management & Analytics
- [ ] Data Import & Export
  - CSV
  - JSON
- [ ] Backup & Restore
  - Full, incremental, differential backups
  - Hot vs cold backups
  - Point-in-Time Recovery (PITR)
- [ ] Working with JSON & XML in SQL
- [ ] Temporal & Time-Series Data
- [ ] Analytical Queries
  - Percentiles
  - Running totals
  - Cumulative sums

---

## 10. Distributed Databases & Industry Practices
- [ ] OLTP vs OLAP workloads
- [ ] Star & Snowflake schemas
- [ ] Fact & Dimension tables
- [ ] Replication
  - Leader–Follower
  - Multi-leader
- [ ] CAP Theorem
- [ ] Consistency models
  - Strong
  - Eventual
- [ ] Database Observability
  - Slow query logs
  - Monitoring & metrics
  - Connection pooling
- [ ] Common DB Anti-Patterns
  - N+1 query problem
  - Over/Under indexing
  - Fat tables
- [ ] Schema migrations & versioning
- [ ] Zero-downtime deployments

---

## 🎯 Outcome
By completing this roadmap, you will be:
- Strong in **DBMS internals**
- Excellent in **SQL (hands-on + optimization)**
- Confident in **real-world database design**
- Ready for **interviews & production systems**
