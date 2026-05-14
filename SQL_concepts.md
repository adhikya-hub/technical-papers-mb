# SQL Concepts

## Table of Contents

1. Introduction
2. ACID Properties
3. CAP Theorem
4. Joins
5. Aggregations and Filters
6. Normalization
7. Indexes
8. Transactions
9. Locking Mechanism
10. Database Isolation Levels
11. Triggers
12. Conclusion

---

## 1. Introduction

Databases are used to store, organize, and manage data efficiently.

Examples:

- Banking systems
- E-commerce websites
- Social media platforms
- Hospital management systems
- School portals

SQL (Structured Query Language) is used to interact with relational databases like:

- PostgreSQL
- MySQL
- Oracle
- SQL Server

Understanding database concepts is important for designing scalable and reliable systems.

---

## 2. ACID Properties

ACID properties ensure reliable transaction processing.

ACID stands for:

- Atomicity
- Consistency
- Isolation
- Durability

These are especially important in banking and financial systems.

---

### 2.1 Atomicity

Atomicity means:

> A transaction is treated as one unit. Either all operations succeed or none happen.

### Example

Money transfer:

1. Deduct ₹1000 from Account A
2. Add ₹1000 to Account B

If the system crashes after step 1, the whole transaction should rollback.

### SQL Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE id = 2;

COMMIT;
```

Rollback example:

```sql
ROLLBACK;
```

---

### 2.2 Consistency

Consistency ensures:

> The database always remains valid.

Rules and constraints should never break.

Example

```sql
CHECK (balance >= 0)
```

Negative balances are prevented.

---

### 2.3 Isolation

Isolation ensures:

> Multiple transactions do not interfere with each other.

Example

Two users trying to book the same movie seat should not both succeed.

---

### 2.4 Durability

Durability means:

> Once committed, data is permanently saved.

Even after power failure or server crash, committed data remains safe.

Techniques used:

- Write Ahead Logging (WAL)
- Disk persistence
- Backups

---

## 3. CAP Theorem

CAP theorem applies to distributed systems.

A distributed database can guarantee only two of these three:

- Consistency
- Availability
- Partition Tolerance

---

### 3.1 Consistency

All users see the latest data.

Example

If one user updates a profile name, everyone sees the updated value immediately.

---

### 3.2 Availability

The system always responds to requests.

Even during failures, users get a response.

---

### 3.3 Partition Tolerance

The system continues working even when communication between servers fails.

---

### CAP Trade-offs

#### CP System

Consistency + Partition Tolerance

- Prioritizes correct data
- May reject requests during failures

Example:

- Banking systems

---

#### AP System

Availability + Partition Tolerance

- Prioritizes availability
- Temporary stale data possible

Example:

- Social media feeds

---

#### CA System

Possible only when no network partition exists.

Not practical in large distributed systems.

---

## 4. Joins

Joins combine rows from multiple tables.

---

### Example Tables

### customers

| customer_id | name |
| --- | --- |
| 1 | Ravi |
| 2 | Priya |

### orders

| order_id | customer_id | amount |
| --- | --- | --- |
| 101 | 1 | 500 |
| 102 | 2 | 800 |

---

### 4.1 INNER JOIN

Returns matching rows from both tables.

```sql
SELECT customers.name, orders.amount
FROM customers
INNER JOIN orders
ON customers.customer_id = orders.customer_id;
```

Output

| name | amount |
| --- | --- |
| Ravi | 500 |
| Priya | 800 |

---

### 4.2 LEFT JOIN

Returns all rows from the left table.

```sql
SELECT customers.name, orders.amount
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;
```

If no match exists, values become `NULL`.

---

### 4.3 RIGHT JOIN

Returns all rows from the right table.

```sql
SELECT customers.name, orders.amount
FROM customers
RIGHT JOIN orders
ON customers.customer_id = orders.customer_id;
```

---

### 4.4 FULL OUTER JOIN

Returns all rows from both tables.

```sql
SELECT customers.name, orders.amount
FROM customers
FULL OUTER JOIN orders
ON customers.customer_id = orders.customer_id;
```

---

### 4.5 SELF JOIN

A table joins with itself.

Example

Employee-manager relationship.

```sql
SELECT e.name AS employee,
       m.name AS manager
FROM employees e
JOIN employees m
ON e.manager_id = m.employee_id;
```

---

## 5. Aggregations and Filters

Aggregate functions perform calculations on rows.

---

### Common Aggregate Functions

| Function | Purpose |
| --- | --- |
| COUNT() | Counts rows |
| SUM() | Adds values |
| AVG() | Finds average |
| MAX() | Finds maximum |
| MIN() | Finds minimum |

---

### Example Table

### sales

| product | amount |
| --- | --- |
| Phone | 1000 |
| Laptop | 5000 |
| Phone | 1500 |

---

### COUNT()

```sql
SELECT COUNT(*) FROM sales;
```

---

### SUM()

```sql
SELECT SUM(amount) FROM sales;
```

---

### AVG()

```sql
SELECT AVG(amount) FROM sales;
```

---

### GROUP BY

Groups rows with the same values.

```sql
SELECT product, SUM(amount)
FROM sales
GROUP BY product;
```

Output

| product | sum |
| --- | --- |
| Phone | 2500 |
| Laptop | 5000 |

---

### WHERE Clause

Filters rows before aggregation.

```sql
SELECT *
FROM sales
WHERE amount > 1000;
```

---

### HAVING Clause

Filters groups after aggregation.

```sql
SELECT product, SUM(amount)
FROM sales
GROUP BY product
HAVING SUM(amount) > 2000;
```

---

## 6. Normalization

Normalization organizes tables to reduce redundancy.

---

## Problems Without Normalization

- Duplicate data
- Update anomalies
- Inconsistent records
- More storage usage

---

## Normal Forms

---

### 6.1 First Normal Form (1NF)

Rules:

- No repeating groups
- Atomic values only

#### Bad Example

| student | subjects |
| --- | --- |
| Ravi | Math, Science |

#### Good Example

| student | subject |
| --- | --- |
| Ravi | Math |
| Ravi | Science |

---

### 6.2 Second Normal Form (2NF)

Rules:

- Must be in 1NF
- No partial dependency

All non-key columns must depend on the full primary key.

---

### 6.3 Third Normal Form (3NF)

Rules:

- Must be in 2NF
- No transitive dependency

Bad Example

| emp_id | dept_id | dept_name |
| --- | --- | --- |
| 1 | 10 | HR |

`dept_name` depends on `dept_id`, not `emp_id`.

### Better Design

### employees

| emp_id | dept_id |
| --- | --- |
| 1 | 10 |

### departments

| dept_id | dept_name |
| --- | --- |
| 10 | HR |

---

## Benefits of Normalization

- Reduces redundancy
- Improves consistency
- Saves storage
- Easier maintenance

---

## 7. Indexes

Indexes improve query performance.

They work like a book index.

Without indexes, databases perform full table scans.

---

### Creating an Index

```sql
CREATE INDEX idx_customer_name
ON customers(name);
```

---

### Benefits

- Faster searching
- Faster sorting
- Faster joins

---

### Drawbacks

Indexes:

- Consume storage
- Slow down INSERT, UPDATE, DELETE

Because indexes also need updates.

---

### Types of Indexes

#### Primary Index

Automatically created on primary keys.

```sql
PRIMARY KEY(id)
```

---

#### Unique Index

Prevents duplicates.

```sql
CREATE UNIQUE INDEX idx_email
ON users(email);
```

---

#### Composite Index

Uses multiple columns.

```sql
CREATE INDEX idx_name_city
ON users(name, city);
```

---

## 8. Transactions

A transaction is a group of SQL operations executed together.

---

## Transaction Commands

| Command | Purpose |
| --- | --- |
| BEGIN | Starts transaction |
| COMMIT | Saves changes |
| ROLLBACK | Cancels changes |
| SAVEPOINT | Partial rollback point |

---

Example

```sql
BEGIN;

UPDATE products
SET stock = stock - 1
WHERE id = 10;

UPDATE orders
SET status = 'confirmed'
WHERE id = 101;

COMMIT;
```

---

### SAVEPOINT Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE id = 1;

SAVEPOINT deduct_done;

UPDATE accounts
SET balance = balance + 500
WHERE id = 2;

ROLLBACK TO deduct_done;

COMMIT;
```

---

## 9. Locking Mechanism

Locks prevent simultaneous conflicting operations.

---

## Why Locking is Needed

Without locking:

- Data corruption may happen
- Lost updates may occur
- Dirty reads become possible

---

## Types of Locks

---

## Shared Lock

- Multiple users can read
- No modification allowed

---

## Exclusive Lock

- Only one transaction can modify
- Others must wait

---

Example

Transaction A:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE id = 1;
```

The row becomes locked.

Transaction B updating the same row waits until:

- COMMIT
- or ROLLBACK

---

## 10. Database Isolation Levels

Isolation levels control interaction between transactions.

---

### Common Problems

---

### Dirty Read

Reading uncommitted data.

---

### Non-Repeatable Read

Reading different values in the same transaction.

---

### Phantom Read

New rows appear during the same transaction.

---

## Isolation Levels

---

## 10.1 Read Uncommitted

Lowest isolation.

- Dirty reads possible
- Fastest performance

---

## 10.2 Read Committed

Only committed data is visible.

- Prevents dirty reads
- Commonly used

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

---

## 10.3 Repeatable Read

Ensures rows remain unchanged during transaction.

- Prevents non-repeatable reads

---

## 10.4 Serializable

Highest isolation level.

Transactions behave sequentially.

- Safest
- Slowest

```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

---

### Isolation Level Comparison

| Isolation Level | Dirty Read | Non-Repeatable Read | Phantom Read |
| --- | --- | --- | --- |
| Read Uncommitted | Yes | Yes | Yes |
| Read Committed | No | Yes | Yes |
| Repeatable Read | No | No | Yes |
| Serializable | No | No | No |

---

## 11. Triggers

Triggers are automatic actions executed on database events.

---

### Trigger Events

- INSERT
- UPDATE
- DELETE

---

### Uses of Triggers

- Audit logging
- Validation
- Automatic updates
- History tracking

---

### Example Trigger

#### Employee Table

```sql
CREATE TABLE employees (
    id INT,
    name VARCHAR(50),
    salary INT
);
```

---

#### Audit Table

```sql
CREATE TABLE salary_log (
    emp_id INT,
    old_salary INT,
    new_salary INT,
    updated_at TIMESTAMP
);
```

---

### Trigger Function (PostgreSQL)

```sql
CREATE OR REPLACE FUNCTION log_salary_change()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO salary_log(
        emp_id,
        old_salary,
        new_salary,
        updated_at
    )
    VALUES(
        OLD.id,
        OLD.salary,
        NEW.salary,
        NOW()
    );

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

---

### Create Trigger

```sql
CREATE TRIGGER salary_update_trigger
AFTER UPDATE ON employees
FOR EACH ROW
EXECUTE FUNCTION log_salary_change();
```

Now every salary update is automatically logged.

---

### Advantages of Triggers

- Automation
- Data integrity
- Audit tracking

---

### Disadvantages of Triggers

- Harder debugging
- Hidden logic
- Performance overhead

---

## 12. Conclusion

Database concepts are essential for building reliable and scalable applications.

Key points:

- ACID ensures reliable transactions
- CAP theorem explains distributed system trade-offs
- Joins combine data from tables
- Aggregations help analyze data
- Normalization reduces redundancy
- Indexes improve performance
- Transactions maintain consistency
- Locking prevents conflicts
- Isolation levels manage concurrency
- Triggers automate actions
