# PostgreSQL SDK

> Reusable PostgreSQL reference for backend development, APIs, Flask/FastAPI projects, and SQL practice.

---

# 1. PostgreSQL Basics

## Connect to PostgreSQL

```bash
psql -U postgres
```

Connect to a specific database:

```bash
psql -U postgres -d mydb
```

Connect using host and port:

```bash
psql -h localhost -p 5432 -U postgres -d mydb
```

---

# 2. PostgreSQL Important `psql` Commands

List databases:

```sql
\l
```

Connect to database:

```sql
\c mydb
```

List tables:

```sql
\dt
```

Describe table:

```sql
\d users
```

Detailed table information:

```sql
\d+ users
```

List schemas:

```sql
\dn
```

List functions:

```sql
\df
```

List roles/users:

```sql
\du
```

Quit:

```sql
\q
```

---

# 3. Create Database

```sql
CREATE DATABASE mydb;
```

Create database with owner:

```sql
CREATE DATABASE mydb
OWNER postgres;
```

Drop database:

```sql
DROP DATABASE mydb;
```

> Never drop a production database accidentally.

---

# 4. Create User / Role

Create user:

```sql
CREATE USER app_user
WITH PASSWORD 'strong_password';
```

Create role:

```sql
CREATE ROLE app_user
LOGIN
PASSWORD 'strong_password';
```

Change password:

```sql
ALTER USER app_user
WITH PASSWORD 'new_password';
```

Drop user:

```sql
DROP USER app_user;
```

---

# 5. Database Privileges

Give database access:

```sql
GRANT CONNECT ON DATABASE mydb
TO app_user;
```

Connect to database:

```sql
\c mydb
```

Give schema access:

```sql
GRANT USAGE ON SCHEMA public
TO app_user;
```

Give table privileges:

```sql
GRANT SELECT, INSERT, UPDATE, DELETE
ON users
TO app_user;
```

Give all privileges:

```sql
GRANT ALL PRIVILEGES
ON TABLE users
TO app_user;
```

---

# 6. Create Table

Basic:

```sql
CREATE TABLE users (
    id INTEGER,
    name VARCHAR(100),
    email VARCHAR(150)
);
```

Better production-style table:

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

# 7. PostgreSQL Data Types

## Numbers

```sql
SMALLINT
INTEGER
BIGINT
DECIMAL
NUMERIC
REAL
DOUBLE PRECISION
```

Example:

```sql
price NUMERIC(10,2)
```

---

## Strings

```sql
CHAR(n)
VARCHAR(n)
TEXT
```

Usually:

```sql
name TEXT
```

is enough when no length constraint is required.

---

## Boolean

```sql
is_active BOOLEAN DEFAULT TRUE
```

Values:

```sql
TRUE
FALSE
```

---

## Date and Time

```sql
DATE
TIME
TIMESTAMP
TIMESTAMPTZ
INTERVAL
```

Example:

```sql
created_at TIMESTAMPTZ DEFAULT NOW()
```

Prefer `TIMESTAMPTZ` for many backend applications where timezone-aware timestamps matter.

---

## UUID

```sql
CREATE EXTENSION IF NOT EXISTS pgcrypto;
```

```sql
id UUID PRIMARY KEY DEFAULT gen_random_uuid()
```

---

## JSON

```sql
JSON
JSONB
```

Prefer `JSONB` for most application-side querying/indexing.

---

# 8. INSERT

Insert one row:

```sql
INSERT INTO users (name, email)
VALUES ('Adnan', 'adnan@example.com');
```

Insert multiple rows:

```sql
INSERT INTO users (name, email)
VALUES
('Adnan', 'adnan@example.com'),
('Rahul', 'rahul@example.com'),
('Aman', 'aman@example.com');
```

---

# 9. SELECT

All columns:

```sql
SELECT *
FROM users;
```

Specific columns:

```sql
SELECT name, email
FROM users;
```

---

# 10. WHERE

```sql
SELECT *
FROM users
WHERE id = 1;
```

Multiple conditions:

```sql
SELECT *
FROM users
WHERE id > 10
AND is_active = TRUE;
```

OR:

```sql
SELECT *
FROM users
WHERE role = 'admin'
OR role = 'manager';
```

---

# 11. Comparison Operators

```text
=       Equal
<>      Not equal
!=      Not equal
>       Greater
<       Less
>=      Greater or equal
<=      Less or equal
```

Example:

```sql
SELECT *
FROM products
WHERE price >= 1000;
```

---

# 12. IN

```sql
SELECT *
FROM users
WHERE id IN (1, 2, 3);
```

With strings:

```sql
SELECT *
FROM users
WHERE role IN ('admin', 'manager');
```

---

# 13. NOT IN

```sql
SELECT *
FROM users
WHERE role NOT IN ('admin', 'manager');
```

> Be careful with `NULL` and `NOT IN`.

---

# 14. BETWEEN

```sql
SELECT *
FROM products
WHERE price BETWEEN 500 AND 2000;
```

---

# 15. LIKE

Starts with:

```sql
SELECT *
FROM users
WHERE name LIKE 'A%';
```

Ends with:

```sql
SELECT *
FROM users
WHERE name LIKE '%n';
```

Contains:

```sql
SELECT *
FROM users
WHERE name LIKE '%ad%';
```

---

# 16. ILIKE

PostgreSQL-specific case-insensitive search:

```sql
SELECT *
FROM users
WHERE name ILIKE '%adnan%';
```

---

# 17. NULL

Check NULL:

```sql
SELECT *
FROM users
WHERE phone IS NULL;
```

Not NULL:

```sql
SELECT *
FROM users
WHERE phone IS NOT NULL;
```

Wrong:

```sql
WHERE phone = NULL
```

Correct:

```sql
WHERE phone IS NULL
```

---

# 18. ORDER BY

Ascending:

```sql
SELECT *
FROM products
ORDER BY price ASC;
```

Descending:

```sql
SELECT *
FROM products
ORDER BY price DESC;
```

Multiple columns:

```sql
SELECT *
FROM users
ORDER BY name ASC, created_at DESC;
```

---

# 19. LIMIT

```sql
SELECT *
FROM users
LIMIT 10;
```

---

# 20. OFFSET

```sql
SELECT *
FROM users
LIMIT 10 OFFSET 20;
```

Useful for basic pagination.

---

# 21. DISTINCT

```sql
SELECT DISTINCT city
FROM users;
```

Multiple columns:

```sql
SELECT DISTINCT city, state
FROM users;
```

---

# 22. UPDATE

```sql
UPDATE users
SET name = 'Md Adnan'
WHERE id = 1;
```

Multiple columns:

```sql
UPDATE users
SET
    name = 'Md Adnan',
    email = 'new@example.com'
WHERE id = 1;
```

> Always be careful with UPDATE without WHERE.

---

# 23. DELETE

```sql
DELETE FROM users
WHERE id = 1;
```

Delete all rows:

```sql
DELETE FROM users;
```

---

# 24. TRUNCATE

```sql
TRUNCATE TABLE users;
```

Reset identity:

```sql
TRUNCATE TABLE users
RESTART IDENTITY;
```

Multiple tables:

```sql
TRUNCATE TABLE users, orders
RESTART IDENTITY
CASCADE;
```

---

# 25. ALTER TABLE

Add column:

```sql
ALTER TABLE users
ADD COLUMN phone TEXT;
```

Rename column:

```sql
ALTER TABLE users
RENAME COLUMN name TO full_name;
```

Change data type:

```sql
ALTER TABLE users
ALTER COLUMN phone TYPE VARCHAR(20);
```

Drop column:

```sql
ALTER TABLE users
DROP COLUMN phone;
```

Rename table:

```sql
ALTER TABLE users
RENAME TO customers;
```

---

# 26. Constraints

## PRIMARY KEY

```sql
id BIGSERIAL PRIMARY KEY
```

---

## UNIQUE

```sql
email TEXT UNIQUE
```

---

## NOT NULL

```sql
name TEXT NOT NULL
```

---

## DEFAULT

```sql
is_active BOOLEAN DEFAULT TRUE
```

---

## CHECK

```sql
age INTEGER CHECK (age >= 18)
```

---

# 27. Foreign Key

Users:

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL
);
```

Orders:

```sql
CREATE TABLE orders (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT NOT NULL,
    amount NUMERIC(10,2),

    FOREIGN KEY (user_id)
    REFERENCES users(id)
);
```

---

# 28. Foreign Key Actions

```sql
FOREIGN KEY (user_id)
REFERENCES users(id)
ON DELETE CASCADE
```

Other options:

```sql
ON DELETE CASCADE
ON DELETE SET NULL
ON DELETE RESTRICT
ON DELETE NO ACTION
```

---

# 29. One-to-Many Relationship

Example:

```text
User
 |
 +---- Order
 |
 +---- Order
 |
 +---- Order
```

Database:

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL
);
```

```sql
CREATE TABLE orders (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT REFERENCES users(id),
    amount NUMERIC(10,2)
);
```

---

# 30. JOIN

## INNER JOIN

```sql
SELECT
    users.name,
    orders.amount
FROM users
INNER JOIN orders
ON users.id = orders.user_id;
```

Only matching records.

---

# 31. LEFT JOIN

```sql
SELECT
    users.name,
    orders.amount
FROM users
LEFT JOIN orders
ON users.id = orders.user_id;
```

Returns all users, even users without orders.

---

# 32. RIGHT JOIN

```sql
SELECT
    users.name,
    orders.amount
FROM users
RIGHT JOIN orders
ON users.id = orders.user_id;
```

---

# 33. FULL OUTER JOIN

```sql
SELECT
    users.name,
    orders.amount
FROM users
FULL OUTER JOIN orders
ON users.id = orders.user_id;
```

---

# 34. CROSS JOIN

```sql
SELECT *
FROM users
CROSS JOIN products;
```

Produces Cartesian product.

---

# 35. Table Aliases

```sql
SELECT
    u.name,
    o.amount
FROM users AS u
JOIN orders AS o
ON u.id = o.user_id;
```

Shorter:

```sql
FROM users u
JOIN orders o
```

---

# 36. Aggregate Functions

COUNT:

```sql
SELECT COUNT(*)
FROM users;
```

SUM:

```sql
SELECT SUM(amount)
FROM orders;
```

AVG:

```sql
SELECT AVG(amount)
FROM orders;
```

MIN:

```sql
SELECT MIN(amount)
FROM orders;
```

MAX:

```sql
SELECT MAX(amount)
FROM orders;
```

---

# 37. GROUP BY

```sql
SELECT
    user_id,
    COUNT(*) AS total_orders
FROM orders
GROUP BY user_id;
```

---

# 38. HAVING

```sql
SELECT
    user_id,
    COUNT(*) AS total_orders
FROM orders
GROUP BY user_id
HAVING COUNT(*) > 5;
```

Difference:

```text
WHERE  → filters rows
HAVING → filters groups
```

---

# 39. CASE

```sql
SELECT
    name,
    age,
    CASE
        WHEN age >= 18 THEN 'Adult'
        ELSE 'Minor'
    END AS category
FROM users;
```

---

# 40. COALESCE

Return first non-NULL value:

```sql
SELECT
    name,
    COALESCE(phone, 'Not Available')
FROM users;
```

---

# 41. NULLIF

```sql
SELECT NULLIF(10, 10);
```

Result:

```text
NULL
```

Useful for avoiding division by zero:

```sql
SELECT
    total / NULLIF(count, 0)
FROM statistics;
```

---

# 42. String Functions

Uppercase:

```sql
SELECT UPPER(name)
FROM users;
```

Lowercase:

```sql
SELECT LOWER(name)
FROM users;
```

Length:

```sql
SELECT LENGTH(name)
FROM users;
```

Concatenate:

```sql
SELECT CONCAT(first_name, ' ', last_name)
FROM users;
```

Substring:

```sql
SELECT SUBSTRING(name FROM 1 FOR 3)
FROM users;
```

Trim:

```sql
SELECT TRIM(name)
FROM users;
```

---

# 43. Date Functions

Current date:

```sql
SELECT CURRENT_DATE;
```

Current timestamp:

```sql
SELECT CURRENT_TIMESTAMP;
```

or:

```sql
SELECT NOW();
```

Extract year:

```sql
SELECT EXTRACT(YEAR FROM created_at)
FROM users;
```

Extract month:

```sql
SELECT EXTRACT(MONTH FROM created_at)
FROM users;
```

---

# 44. Date Formatting

```sql
SELECT TO_CHAR(
    created_at,
    'DD/Mon/YYYY'
)
FROM users;
```

Example:

```text
12/Apr/2023
```

Only year:

```sql
SELECT TO_CHAR(
    created_at,
    'YYYY'
)
FROM users;
```

---

# 45. INTERVAL

```sql
SELECT NOW() + INTERVAL '7 days';
```

```sql
SELECT NOW() - INTERVAL '1 month';
```

---

# 46. Subquery

```sql
SELECT *
FROM users
WHERE id IN (
    SELECT user_id
    FROM orders
    WHERE amount > 5000
);
```

---

# 47. EXISTS

```sql
SELECT *
FROM users u
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.user_id = u.id
);
```

Meaning:

```text
Does at least one matching order exist?
```

---

# 48. Common Table Expression (CTE)

```sql
WITH high_value_orders AS (
    SELECT *
    FROM orders
    WHERE amount > 5000
)
SELECT *
FROM high_value_orders;
```

Multiple CTEs:

```sql
WITH users_count AS (
    SELECT COUNT(*) AS total
    FROM users
),
orders_count AS (
    SELECT COUNT(*) AS total
    FROM orders
)
SELECT *
FROM users_count, orders_count;
```

---

# 49. Recursive CTE

Useful for trees/hierarchies.

```sql
WITH RECURSIVE employee_tree AS (
    SELECT
        id,
        name,
        manager_id
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT
        e.id,
        e.name,
        e.manager_id
    FROM employees e
    JOIN employee_tree t
    ON e.manager_id = t.id
)
SELECT *
FROM employee_tree;
```

---

# 50. UNION

```sql
SELECT email
FROM users

UNION

SELECT email
FROM customers;
```

Removes duplicates.

---

# 51. UNION ALL

```sql
SELECT email
FROM users

UNION ALL

SELECT email
FROM customers;
```

Keeps duplicates.

---

# 52. INTERSECT

```sql
SELECT email
FROM users

INTERSECT

SELECT email
FROM customers;
```

Returns common rows.

---

# 53. EXCEPT

```sql
SELECT email
FROM users

EXCEPT

SELECT email
FROM customers;
```

Returns rows present in first query but not second.

---

# 54. RETURNING

PostgreSQL feature.

```sql
INSERT INTO users (name, email)
VALUES ('Adnan', 'adnan@example.com')
RETURNING id;
```

Update:

```sql
UPDATE users
SET name = 'New Name'
WHERE id = 1
RETURNING *;
```

Delete:

```sql
DELETE FROM users
WHERE id = 1
RETURNING *;
```

Very useful in APIs.

---

# 55. UPSERT

Insert or update:

```sql
INSERT INTO users (email, name)
VALUES ('adnan@example.com', 'Adnan')
ON CONFLICT (email)
DO UPDATE
SET name = EXCLUDED.name;
```

Ignore conflict:

```sql
INSERT INTO users (email, name)
VALUES ('adnan@example.com', 'Adnan')
ON CONFLICT (email)
DO NOTHING;
```

---

# 56. Transactions

Start:

```sql
BEGIN;
```

Queries:

```sql
UPDATE accounts
SET balance = balance - 1000
WHERE id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE id = 2;
```

Commit:

```sql
COMMIT;
```

Rollback:

```sql
ROLLBACK;
```

---

# 57. Transaction Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE id = 2;

COMMIT;
```

If something fails:

```sql
ROLLBACK;
```

---

# 58. SAVEPOINT

```sql
BEGIN;

UPDATE users
SET name = 'A'
WHERE id = 1;

SAVEPOINT before_second_update;

UPDATE users
SET name = 'B'
WHERE id = 2;

ROLLBACK TO SAVEPOINT before_second_update;

COMMIT;
```

---

# 59. Isolation Levels

PostgreSQL supports:

```text
READ COMMITTED
REPEATABLE READ
SERIALIZABLE
```

Default:

```text
READ COMMITTED
```

Set isolation level:

```sql
BEGIN TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

---

# 60. Row Locking

```sql
SELECT *
FROM accounts
WHERE id = 1
FOR UPDATE;
```

Useful when modifying a row safely inside a transaction.

---

# 61. SKIP LOCKED

Useful for job queues.

```sql
SELECT *
FROM jobs
WHERE status = 'pending'
ORDER BY id
FOR UPDATE SKIP LOCKED
LIMIT 1;
```

---

# 62. Index

Create index:

```sql
CREATE INDEX idx_users_email
ON users(email);
```

Unique index:

```sql
CREATE UNIQUE INDEX idx_users_email_unique
ON users(email);
```

Drop:

```sql
DROP INDEX idx_users_email;
```

---

# 63. Composite Index

```sql
CREATE INDEX idx_users_city_status
ON users(city, status);
```

Important:

```text
(city, status)
```

is different from:

```text
(status, city)
```

Column order matters.

---

# 64. Partial Index

Index only specific rows:

```sql
CREATE INDEX idx_active_users
ON users(email)
WHERE is_active = TRUE;
```

Useful when only a subset of rows is frequently queried.

---

# 65. Expression Index

```sql
CREATE INDEX idx_lower_email
ON users(LOWER(email));
```

Then:

```sql
SELECT *
FROM users
WHERE LOWER(email) = 'adnan@example.com';
```

---

# 66. GIN Index

Commonly used for:

```text
JSONB
Arrays
Full-text search
```

Example:

```sql
CREATE INDEX idx_users_metadata
ON users
USING GIN(metadata);
```

---

# 67. BRIN Index

Useful for very large tables where values have natural physical correlation.

```sql
CREATE INDEX idx_logs_created_at
ON logs
USING BRIN(created_at);
```

---

# 68. EXPLAIN

```sql
EXPLAIN
SELECT *
FROM users
WHERE email = 'adnan@example.com';
```

---

# 69. EXPLAIN ANALYZE

Actually executes the query:

```sql
EXPLAIN ANALYZE
SELECT *
FROM users
WHERE email = 'adnan@example.com';
```

Useful for performance debugging.

---

# 70. Query Performance

Check:

```sql
EXPLAIN ANALYZE
SELECT *
FROM orders
WHERE user_id = 10;
```

If frequently used, consider:

```sql
CREATE INDEX idx_orders_user_id
ON orders(user_id);
```

---

# 71. VACUUM

```sql
VACUUM;
```

Specific table:

```sql
VACUUM users;
```

Analyze:

```sql
VACUUM ANALYZE users;
```

---

# 72. ANALYZE

Update planner statistics:

```sql
ANALYZE users;
```

---

# 73. JSONB

Create table:

```sql
CREATE TABLE products (
    id BIGSERIAL PRIMARY KEY,
    name TEXT,
    metadata JSONB
);
```

Insert:

```sql
INSERT INTO products (name, metadata)
VALUES (
    'Laptop',
    '{"brand": "Lenovo", "ram": 16, "ssd": 512}'
);
```

---

# 74. Read JSONB

```sql
SELECT metadata
FROM products;
```

Get text value:

```sql
SELECT metadata->>'brand'
FROM products;
```

Get JSON value:

```sql
SELECT metadata->'ram'
FROM products;
```

---

# 75. JSONB Filtering

```sql
SELECT *
FROM products
WHERE metadata->>'brand' = 'Lenovo';
```

Numeric comparison:

```sql
SELECT *
FROM products
WHERE (metadata->>'ram')::INTEGER >= 16;
```

---

# 76. JSONB Containment

```sql
SELECT *
FROM products
WHERE metadata @> '{"brand": "Lenovo"}';
```

Create GIN index:

```sql
CREATE INDEX idx_products_metadata
ON products
USING GIN(metadata);
```

---

# 77. Arrays

Create:

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT,
    skills TEXT[]
);
```

Insert:

```sql
INSERT INTO users (name, skills)
VALUES (
    'Adnan',
    ARRAY['Python', 'Flask', 'PostgreSQL']
);
```

Search:

```sql
SELECT *
FROM users
WHERE 'Python' = ANY(skills);
```

---

# 78. UUID Primary Key

Enable extension:

```sql
CREATE EXTENSION IF NOT EXISTS pgcrypto;
```

Table:

```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL
);
```

---

# 79. ENUM

Create enum:

```sql
CREATE TYPE user_role AS ENUM (
    'user',
    'admin',
    'manager'
);
```

Use:

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    role user_role NOT NULL DEFAULT 'user'
);
```

---

# 80. Generated Columns

```sql
CREATE TABLE products (
    price NUMERIC,
    quantity INTEGER,
    total NUMERIC
    GENERATED ALWAYS AS (price * quantity) STORED
);
```

---

# 81. Views

Create:

```sql
CREATE VIEW active_users AS
SELECT *
FROM users
WHERE is_active = TRUE;
```

Use:

```sql
SELECT *
FROM active_users;
```

Drop:

```sql
DROP VIEW active_users;
```

---

# 82. Materialized View

Create:

```sql
CREATE MATERIALIZED VIEW monthly_sales AS
SELECT
    DATE_TRUNC('month', created_at) AS month,
    SUM(amount) AS total
FROM orders
GROUP BY 1;
```

Refresh:

```sql
REFRESH MATERIALIZED VIEW monthly_sales;
```

---

# 83. Schema

Create:

```sql
CREATE SCHEMA app;
```

Create table inside schema:

```sql
CREATE TABLE app.users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT
);
```

Query:

```sql
SELECT *
FROM app.users;
```

---

# 84. Functions

Simple function:

```sql
CREATE FUNCTION add_numbers(
    a INTEGER,
    b INTEGER
)
RETURNS INTEGER
LANGUAGE SQL
AS $$
    SELECT a + b;
$$;
```

Call:

```sql
SELECT add_numbers(10, 20);
```

---

# 85. PL/pgSQL Function

```sql
CREATE FUNCTION get_user_count()
RETURNS INTEGER
LANGUAGE plpgsql
AS $$
DECLARE
    total INTEGER;
BEGIN
    SELECT COUNT(*)
    INTO total
    FROM users;

    RETURN total;
END;
$$;
```

---

# 86. Trigger

Create function:

```sql
CREATE FUNCTION update_timestamp()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
BEGIN
    NEW.updated_at = NOW();
    RETURN NEW;
END;
$$;
```

Create trigger:

```sql
CREATE TRIGGER users_updated_at
BEFORE UPDATE ON users
FOR EACH ROW
EXECUTE FUNCTION update_timestamp();
```

---

# 87. Common Timestamp Pattern

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);
```

---

# 88. Pagination

Basic:

```sql
SELECT *
FROM users
ORDER BY id
LIMIT 20
OFFSET 40;
```

Page calculation:

```text
offset = (page - 1) * limit
```

Example:

```text
page = 3
limit = 20

offset = (3 - 1) * 20
       = 40
```

---

# 89. Cursor Pagination

Instead of:

```sql
LIMIT 20 OFFSET 100000;
```

Use:

```sql
SELECT *
FROM users
WHERE id > 1000
ORDER BY id
LIMIT 20;
```

Better for large datasets.

---

# 90. Full Text Search

Add `tsvector`:

```sql
ALTER TABLE products
ADD COLUMN search_vector TSVECTOR;
```

Update:

```sql
UPDATE products
SET search_vector =
    to_tsvector('english', name);
```

Search:

```sql
SELECT *
FROM products
WHERE search_vector @@
      plainto_tsquery('english', 'gaming laptop');
```

GIN index:

```sql
CREATE INDEX idx_products_search
ON products
USING GIN(search_vector);
```

---

# 91. PostgreSQL UPSERT Example

```sql
INSERT INTO products (
    sku,
    name,
    price
)
VALUES (
    'LAP001',
    'Laptop',
    50000
)
ON CONFLICT (sku)
DO UPDATE SET
    name = EXCLUDED.name,
    price = EXCLUDED.price
RETURNING *;
```

---

# 92. COPY

Import CSV:

```sql
COPY users(name, email)
FROM '/path/users.csv'
WITH (
    FORMAT csv,
    HEADER true
);
```

Export:

```sql
COPY users
TO '/path/users.csv'
WITH (
    FORMAT csv,
    HEADER true
);
```

---

# 93. `\copy` in psql

Client-side CSV import:

```bash
\copy users(name, email) FROM 'users.csv' CSV HEADER;
```

Export:

```bash
\copy users TO 'users.csv' CSV HEADER;
```

---

# 94. Backup

Using `pg_dump`:

```bash
pg_dump -U postgres mydb > backup.sql
```

Restore:

```bash
psql -U postgres mydb < backup.sql
```

Custom format:

```bash
pg_dump -U postgres -Fc mydb > backup.dump
```

Restore:

```bash
pg_restore -U postgres -d mydb backup.dump
```

---

# 95. Database Size

```sql
SELECT pg_size_pretty(
    pg_database_size(current_database())
);
```

Table size:

```sql
SELECT pg_size_pretty(
    pg_total_relation_size('users')
);
```

---

# 96. List Tables and Sizes

```sql
SELECT
    relname AS table_name,
    pg_size_pretty(
        pg_total_relation_size(relid)
    ) AS size
FROM pg_catalog.pg_statio_user_tables
ORDER BY pg_total_relation_size(relid) DESC;
```

---

# 97. Active Connections

```sql
SELECT
    pid,
    usename,
    datname,
    client_addr,
    state
FROM pg_stat_activity;
```

---

# 98. Kill a Query

```sql
SELECT pg_cancel_backend(pid);
```

Terminate connection:

```sql
SELECT pg_terminate_backend(pid);
```

Use carefully in production.

---

# 99. PostgreSQL + Python

Install driver:

```bash
pip install psycopg
```

Connection:

```python
import psycopg

conn = psycopg.connect(
    "dbname=mydb user=postgres password=password host=localhost"
)

cur = conn.cursor()

cur.execute(
    "SELECT * FROM users"
)

rows = cur.fetchall()

for row in rows:
    print(row)

cur.close()
conn.close()
```

---

# 100. Parameterized Query

Never do:

```python
email = input()

query = f"""
SELECT *
FROM users
WHERE email = '{email}'
"""
```

Use parameters:

```python
cur.execute(
    """
    SELECT *
    FROM users
    WHERE email = %s
    """,
    (email,)
)
```

This helps prevent SQL injection.

---

# 101. INSERT from Python

```python
cur.execute(
    """
    INSERT INTO users (name, email)
    VALUES (%s, %s)
    RETURNING id
    """,
    ("Adnan", "adnan@example.com")
)

user_id = cur.fetchone()[0]

conn.commit()
```

---

# 102. PostgreSQL + Flask

Install:

```bash
pip install flask psycopg
```

Basic:

```python
from flask import Flask, jsonify
import psycopg

app = Flask(__name__)


def get_db():
    return psycopg.connect(
        "dbname=mydb user=postgres password=password host=localhost"
    )


@app.get("/users")
def get_users():

    with get_db() as conn:
        with conn.cursor() as cur:

            cur.execute(
                "SELECT id, name, email FROM users"
            )

            rows = cur.fetchall()

    return jsonify(rows)
```

---

# 103. PostgreSQL + SQLAlchemy

Install:

```bash
pip install sqlalchemy psycopg
```

Connection:

```python
from sqlalchemy import create_engine

DATABASE_URL = (
    "postgresql+psycopg://"
    "postgres:password@localhost:5432/mydb"
)

engine = create_engine(DATABASE_URL)
```

---

# 104. SQLAlchemy Model

```python
from sqlalchemy.orm import DeclarativeBase
from sqlalchemy import String
from sqlalchemy.orm import Mapped
from sqlalchemy.orm import mapped_column


class Base(DeclarativeBase):
    pass


class User(Base):

    __tablename__ = "users"

    id: Mapped[int] = mapped_column(
        primary_key=True
    )

    name: Mapped[str] = mapped_column(
        String(100)
    )

    email: Mapped[str] = mapped_column(
        String(150),
        unique=True
    )
```

---

# 105. SQLAlchemy Session

```python
from sqlalchemy.orm import sessionmaker

SessionLocal = sessionmaker(
    bind=engine,
    autoflush=False,
    autocommit=False
)
```

Usage:

```python
db = SessionLocal()

try:
    users = db.query(User).all()
finally:
    db.close()
```

---

# 106. SQLAlchemy Insert

```python
user = User(
    name="Adnan",
    email="adnan@example.com"
)

db.add(user)
db.commit()
db.refresh(user)
```

---

# 107. SQLAlchemy Query

```python
users = (
    db.query(User)
    .filter(User.name == "Adnan")
    .all()
)
```

---

# 108. SQLAlchemy 2.x Style

```python
from sqlalchemy import select

stmt = select(User).where(
    User.name == "Adnan"
)

users = db.scalars(stmt).all()
```

---

# 109. Environment Variables

`.env`

```env
DATABASE_URL=postgresql+psycopg://postgres:password@localhost:5432/mydb
```

Python:

```python
import os

DATABASE_URL = os.getenv(
    "DATABASE_URL"
)
```

---

# 110. PostgreSQL Connection URL

Format:

```text
postgresql://USERNAME:PASSWORD@HOST:PORT/DATABASE
```

Example:

```text
postgresql://postgres:password@localhost:5432/mydb
```

SQLAlchemy with psycopg:

```text
postgresql+psycopg://postgres:password@localhost:5432/mydb
```

---

# 111. FastAPI + PostgreSQL Architecture

```text
Client
  |
  v
FastAPI
  |
  v
Router
  |
  v
Service
  |
  v
Repository / SQLAlchemy
  |
  v
PostgreSQL
```

---

# 112. Recommended Backend Structure

```text
project/
│
├── app/
│   ├── main.py
│   │
│   ├── core/
│   │   ├── config.py
│   │   └── security.py
│   │
│   ├── db/
│   │   ├── database.py
│   │   └── models.py
│   │
│   ├── models/
│   │   └── user.py
│   │
│   ├── schemas/
│   │   └── user.py
│   │
│   ├── routers/
│   │   └── users.py
│   │
│   ├── services/
│   │   └── user_service.py
│   │
│   └── repositories/
│       └── user_repository.py
│
├── migrations/
│
├── .env
├── .env.example
├── requirements.txt
└── README.md
```

---

# 113. PostgreSQL Security Checklist

```text
✓ Never hardcode passwords
✓ Use environment variables
✓ Use parameterized queries
✓ Use least-privilege database users
✓ Don't expose PostgreSQL publicly unnecessarily
✓ Use SSL/TLS for remote connections
✓ Keep PostgreSQL updated
✓ Use backups
✓ Test restore procedures
✓ Don't give application users superuser privileges
✓ Validate user input
✓ Use transactions for multi-step operations
✓ Add indexes based on actual query patterns
```

---

# 114. SQL Injection

Dangerous:

```python
query = f"""
SELECT *
FROM users
WHERE email = '{email}'
"""
```

Safe:

```python
cur.execute(
    """
    SELECT *
    FROM users
    WHERE email = %s
    """,
    (email,)
)
```

Rule:

```text
NEVER concatenate untrusted input into SQL.
```

---

# 115. Common PostgreSQL Commands Cheat Sheet

```sql
CREATE DATABASE db;
DROP DATABASE db;

CREATE TABLE users (...);
DROP TABLE users;

INSERT INTO users (...) VALUES (...);

SELECT * FROM users;

UPDATE users
SET name = 'Adnan'
WHERE id = 1;

DELETE FROM users
WHERE id = 1;

ALTER TABLE users ADD COLUMN phone TEXT;

CREATE INDEX idx_name
ON users(name);

DROP INDEX idx_name;

BEGIN;
COMMIT;
ROLLBACK;

CREATE VIEW ...
DROP VIEW ...

CREATE SCHEMA app;

GRANT ...
REVOKE ...
```

---

# 116. `psql` Cheat Sheet

```text
\l          → databases
\c db       → connect database
\dt         → tables
\d table    → table structure
\dn         → schemas
\du         → users/roles
\df         → functions
\q          → quit
```

---

# 117. SQL Execution Order

Remember:

```text
FROM
  ↓
JOIN
  ↓
WHERE
  ↓
GROUP BY
  ↓
HAVING
  ↓
SELECT
  ↓
DISTINCT
  ↓
ORDER BY
  ↓
LIMIT
```

Example:

```sql
SELECT
    city,
    COUNT(*) AS total
FROM users
WHERE is_active = TRUE
GROUP BY city
HAVING COUNT(*) > 10
ORDER BY total DESC
LIMIT 5;
```

---

# 118. PostgreSQL CRUD Mental Model

```text
CREATE → INSERT
READ   → SELECT
UPDATE → UPDATE
DELETE → DELETE
```

Example:

```text
POST   → INSERT
GET    → SELECT
PUT    → UPDATE
PATCH  → UPDATE
DELETE → DELETE
```

---

# 119. Real-World E-Commerce Database

```text
users
  |
  +---- orders
          |
          +---- order_items
                    |
                    +---- products
```

Tables:

```sql
users
-----
id
name
email


products
--------
id
name
price
stock


orders
------
id
user_id
total
status
created_at


order_items
-----------
id
order_id
product_id
quantity
price
```

---

# 120. Example E-Commerce Schema

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL,
    created_at TIMESTAMPTZ DEFAULT NOW()
);
```

```sql
CREATE TABLE products (
    id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    price NUMERIC(10,2) NOT NULL,
    stock INTEGER NOT NULL DEFAULT 0
);
```

```sql
CREATE TABLE orders (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT NOT NULL
        REFERENCES users(id),
    total NUMERIC(10,2) NOT NULL,
    status TEXT NOT NULL DEFAULT 'pending',
    created_at TIMESTAMPTZ DEFAULT NOW()
);
```

```sql
CREATE TABLE order_items (
    id BIGSERIAL PRIMARY KEY,

    order_id BIGINT NOT NULL
        REFERENCES orders(id)
        ON DELETE CASCADE,

    product_id BIGINT NOT NULL
        REFERENCES products(id),

    quantity INTEGER NOT NULL
        CHECK (quantity > 0),

    price NUMERIC(10,2) NOT NULL
);
```

---

# 121. Order Creation Transaction

```sql
BEGIN;

INSERT INTO orders (
    user_id,
    total
)
VALUES (
    1,
    5000
)
RETURNING id;
```

Suppose returned ID:

```text
101
```

Then:

```sql
INSERT INTO order_items (
    order_id,
    product_id,
    quantity,
    price
)
VALUES (
    101,
    5,
    2,
    2500
);
```

Finally:

```sql
COMMIT;
```

---

# 122. Database Normalization Reminder

```text
1NF
↓
Atomic values

2NF
↓
1NF + no partial dependency

3NF
↓
2NF + no transitive dependency

BCNF
↓
Every determinant is a candidate key
```

---

# 123. Primary Key vs Foreign Key

```text
PRIMARY KEY
→ uniquely identifies row

FOREIGN KEY
→ connects one table to another
```

Example:

```sql
users.id
     ↑
     |
orders.user_id
```

---

# 124. Index Mental Model

Without index:

```text
Database
   ↓
Scan many rows
   ↓
Find target
```

With index:

```text
Query
  ↓
Index
  ↓
Find location
  ↓
Fetch row
```

But:

```text
More indexes
    ↓
Faster reads
    +
Slower INSERT/UPDATE/DELETE
    +
More storage
```

---

# 125. PostgreSQL Production Flow

```text
Frontend
   |
   v
REST API
   |
   v
Backend
   |
   v
Connection Pool
   |
   v
PostgreSQL
   |
   +---- Indexes
   |
   +---- Transactions
   |
   +---- Constraints
   |
   +---- Backups
```

---

# 126. Recommended Learning Order

```text
1. CREATE DATABASE
2. CREATE TABLE
3. Data Types
4. INSERT
5. SELECT
6. WHERE
7. ORDER BY
8. LIMIT/OFFSET
9. UPDATE
10. DELETE
11. Constraints
12. Primary Key
13. Foreign Key
14. JOIN
15. GROUP BY
16. HAVING
17. Subqueries
18. CTE
19. Transactions
20. Indexes
21. EXPLAIN ANALYZE
22. JSONB
23. Views
24. Functions
25. Triggers
26. Roles/Privileges
27. Backup/Restore
28. PostgreSQL + Python
29. PostgreSQL + Flask
30. PostgreSQL + FastAPI
31. Production deployment
```

---

# 127. Most Important Commands

```sql
SELECT
INSERT
UPDATE
DELETE

CREATE TABLE
ALTER TABLE
DROP TABLE

CREATE DATABASE
DROP DATABASE

CREATE INDEX
DROP INDEX

JOIN
GROUP BY
HAVING

BEGIN
COMMIT
ROLLBACK

GRANT
REVOKE

CREATE VIEW
CREATE FUNCTION
CREATE TRIGGER

EXPLAIN
EXPLAIN ANALYZE

VACUUM
ANALYZE
```

---

# 128. One-Page Mental Model

```text
DATABASE
│
├── SCHEMA
│     │
│     ├── TABLE
│     │     ├── COLUMN
│     │     ├── PRIMARY KEY
│     │     ├── FOREIGN KEY
│     │     ├── CONSTRAINT
│     │     └── INDEX
│     │
│     ├── VIEW
│     ├── FUNCTION
│     └── TRIGGER
│
└── ROLE / USER
```

Backend:

```text
Frontend
   ↓
API
   ↓
Service
   ↓
ORM / SQL
   ↓
PostgreSQL
   ↓
Tables + Indexes + Transactions
```

---

# 129. Golden Rules

```text
1. Use PRIMARY KEY for row identity.

2. Use FOREIGN KEY for relationships.

3. Use NOT NULL when a value is required.

4. Use UNIQUE for values that must be unique.

5. Use CHECK for database-level validation.

6. Use parameterized queries.

7. Use transactions for related operations.

8. Index columns used frequently in filtering,
   joins, and ordering after checking query patterns.

9. Use EXPLAIN ANALYZE for performance debugging.

10. Use JSONB when flexible structured data is actually needed.

11. Use TIMESTAMPTZ when timezone-aware timestamps are important.

12. Keep database credentials in environment variables.

13. Give application users only required privileges.

14. Always maintain tested backups.

15. Never blindly use SELECT * in production APIs.
```

---

# 130. Quick Backend Example

```text
POST /users
     ↓
Validate JSON
     ↓
INSERT INTO users
     ↓
RETURNING id
     ↓
PostgreSQL
     ↓
JSON Response
```

Example SQL:

```sql
INSERT INTO users (
    name,
    email
)
VALUES (
    'Adnan',
    'adnan@example.com'
)
RETURNING id, name, email;
```

Response:

```json
{
    "id": 1,
    "name": "Adnan",
    "email": "adnan@example.com"
}
```

---

# END — PostgreSQL SDK
