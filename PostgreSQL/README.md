# PostgreSQL Commands Reference

## Connection & Authentication

```sql
-- Connect to PostgreSQL server
psql -h hostname -p port -U username -d database_name

-- Connect with password prompt
psql -h hostname -p port -U username -W -d database_name

-- Connect with connection string
psql "postgresql://username:password@hostname:port/database_name"

-- Connect to local server with current OS user
psql

-- Connect to specific database with current OS user
psql database_name

-- Execute SQL from command line
psql -c "SELECT version();"

-- Execute SQL from file
psql -f filename.sql

-- Create user
CREATE USER username WITH PASSWORD 'password';

-- Create user with additional options
CREATE USER username WITH PASSWORD 'password' CREATEDB CREATEROLE;

-- Alter user password
ALTER USER username WITH PASSWORD 'new_password';

-- Grant privileges
GRANT ALL PRIVILEGES ON DATABASE database_name TO username;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO username;
GRANT SELECT, INSERT, UPDATE ON table_name TO username;

-- Revoke privileges
REVOKE ALL PRIVILEGES ON DATABASE database_name FROM username;
REVOKE ALL PRIVILEGES ON ALL TABLES IN SCHEMA public FROM username;

-- Show grants
\du
\du username

-- Delete user
DROP USER username;
```

## Database Operations

```sql
-- List all databases
\l
\list
SELECT datname FROM pg_database;

-- Create database
CREATE DATABASE database_name;

-- Create database with options
CREATE DATABASE database_name
    WITH OWNER = username
    ENCODING = 'UTF8'
    LC_COLLATE = 'en_US.UTF-8'
    LC_CTYPE = 'en_US.UTF-8'
    TEMPLATE = template0
    CONNECTION LIMIT = -1;

-- Connect to database
\c database_name
\connect database_name

-- Show current database
SELECT current_database();

-- Rename database
ALTER DATABASE database_name RENAME TO new_database_name;

-- Drop database
DROP DATABASE database_name;

-- Drop database if exists
DROP DATABASE IF EXISTS database_name;

-- Show database size
SELECT pg_size_pretty(pg_database_size('database_name'));

-- Show all database sizes
SELECT datname, pg_size_pretty(pg_database_size(datname)) FROM pg_database ORDER BY pg_database_size(datname) DESC;
```

## Schema Operations

```sql
-- List schemas
\dn
SELECT schema_name FROM information_schema.schemata;

-- Create schema
CREATE SCHEMA schema_name;

-- Create schema with owner
CREATE SCHEMA schema_name AUTHORIZATION username;

-- Rename schema
ALTER SCHEMA schema_name RENAME TO new_schema_name;

-- Change schema owner
ALTER SCHEMA schema_name OWNER TO new_owner;

-- Drop schema
DROP SCHEMA schema_name;

-- Drop schema with objects
DROP SCHEMA schema_name CASCADE;

-- Show search path
SHOW search_path;

-- Set search path
SET search_path TO schema_name, public;
```

## Table Operations

```sql
-- List tables
\dt
SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';

-- List tables in specific schema
\dt schema_name.*
SELECT table_name FROM information_schema.tables WHERE table_schema = 'schema_name';

-- Create table
CREATE TABLE table_name (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create table with schema
CREATE TABLE schema_name.table_name (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

-- Show table structure
\d table_name
\d+ table_name

-- Rename table
ALTER TABLE table_name RENAME TO new_table_name;

-- Change table schema
ALTER TABLE table_name SET SCHEMA new_schema;

-- Change table owner
ALTER TABLE table_name OWNER TO new_owner;

-- Drop table
DROP TABLE table_name;

-- Drop table if exists
DROP TABLE IF EXISTS table_name;

-- Truncate table
TRUNCATE TABLE table_name;

-- Truncate multiple tables
TRUNCATE TABLE table1, table2, table3;

-- Truncate with cascade
TRUNCATE TABLE table_name CASCADE;

-- Copy table structure
CREATE TABLE new_table (LIKE original_table);

-- Copy table structure and data
CREATE TABLE new_table AS SELECT * FROM original_table;

-- Add column
ALTER TABLE table_name ADD COLUMN column_name data_type;

-- Add column with constraints
ALTER TABLE table_name ADD COLUMN column_name VARCHAR(100) NOT NULL DEFAULT 'default_value';

-- Rename column
ALTER TABLE table_name RENAME COLUMN old_name TO new_name;

-- Change column data type
ALTER TABLE table_name ALTER COLUMN column_name TYPE new_data_type;

-- Change column default
ALTER TABLE table_name ALTER COLUMN column_name SET DEFAULT 'default_value';

-- Remove column default
ALTER TABLE table_name ALTER COLUMN column_name DROP DEFAULT;

-- Make column NOT NULL
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;

-- Make column nullable
ALTER TABLE table_name ALTER COLUMN column_name DROP NOT NULL;

-- Drop column
ALTER TABLE table_name DROP COLUMN column_name;

-- Drop column with cascade
ALTER TABLE table_name DROP COLUMN column_name CASCADE;

-- Add primary key
ALTER TABLE table_name ADD PRIMARY KEY (column_name);

-- Add composite primary key
ALTER TABLE table_name ADD PRIMARY KEY (column1, column2);

-- Drop primary key
ALTER TABLE table_name DROP CONSTRAINT table_name_pkey;

-- Add foreign key
ALTER TABLE table_name ADD CONSTRAINT fk_name FOREIGN KEY (column_name) REFERENCES ref_table(ref_column);

-- Add foreign key with options
ALTER TABLE table_name ADD CONSTRAINT fk_name FOREIGN KEY (column_name) 
    REFERENCES ref_table(ref_column) ON DELETE CASCADE ON UPDATE CASCADE;

-- Drop foreign key
ALTER TABLE table_name DROP CONSTRAINT fk_name;

-- Add unique constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name);

-- Add composite unique constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column1, column2);

-- Drop unique constraint
ALTER TABLE table_name DROP CONSTRAINT constraint_name;

-- Add check constraint
ALTER TABLE table_name ADD CONSTRAINT constraint_name CHECK (condition);

-- Drop check constraint
ALTER TABLE table_name DROP CONSTRAINT constraint_name;

-- Show table size
SELECT pg_size_pretty(pg_total_relation_size('table_name'));

-- Show table, index, and toast sizes
SELECT 
    pg_size_pretty(pg_relation_size('table_name')) AS table_size,
    pg_size_pretty(pg_indexes_size('table_name')) AS index_size,
    pg_size_pretty(pg_total_relation_size('table_name')) AS total_size;
```

## Index Operations

```sql
-- List indexes
\di
\di+
SELECT indexname, indexdef FROM pg_indexes WHERE tablename = 'table_name';

-- Create index
CREATE INDEX index_name ON table_name (column_name);

-- Create index on expression
CREATE INDEX index_name ON table_name (lower(column_name));

-- Create unique index
CREATE UNIQUE INDEX index_name ON table_name (column_name);

-- Create composite index
CREATE INDEX index_name ON table_name (column1, column2);

-- Create partial index
CREATE INDEX index_name ON table_name (column_name) WHERE condition;

-- Create index with specific method
CREATE INDEX index_name ON table_name USING HASH (column_name);
CREATE INDEX index_name ON table_name USING BTREE (column_name);
CREATE INDEX index_name ON table_name USING GIN (column_name);
CREATE INDEX index_name ON table_name USING GIST (column_name);

-- Create index concurrently (doesn't lock table)
CREATE INDEX CONCURRENTLY index_name ON table_name (column_name);

-- Rename index
ALTER INDEX index_name RENAME TO new_index_name;

-- Drop index
DROP INDEX index_name;

-- Drop index concurrently
DROP INDEX CONCURRENTLY index_name;

-- Reindex
REINDEX INDEX index_name;
REINDEX TABLE table_name;
REINDEX SCHEMA schema_name;
REINDEX DATABASE database_name;
```

## Data Manipulation

```sql
-- Insert row
INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2');

-- Insert multiple rows
INSERT INTO table_name (column1, column2) VALUES 
    ('value1', 'value2'),
    ('value3', 'value4');

-- Insert with returning
INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2') RETURNING id, column1;

-- Insert with select
INSERT INTO table_name (column1, column2)
SELECT column1, column2 FROM other_table WHERE condition;

-- Update rows
UPDATE table_name SET column1 = 'value1', column2 = 'value2' WHERE condition;

-- Update with returning
UPDATE table_name SET column1 = 'value1' WHERE condition RETURNING id, column1;

-- Update from another table
UPDATE table_name SET column1 = other_table.column1
FROM other_table
WHERE table_name.id = other_table.id;

-- Delete rows
DELETE FROM table_name WHERE condition;

-- Delete with returning
DELETE FROM table_name WHERE condition RETURNING id, column1;

-- Delete all rows
DELETE FROM table_name;

-- Select data
SELECT * FROM table_name;
SELECT column1, column2 FROM table_name;

-- Select with condition
SELECT * FROM table_name WHERE condition;

-- Select with multiple conditions
SELECT * FROM table_name WHERE condition1 AND condition2;
SELECT * FROM table_name WHERE condition1 OR condition2;

-- Select with sorting
SELECT * FROM table_name ORDER BY column1 ASC, column2 DESC;

-- Select with limit
SELECT * FROM table_name LIMIT 10;

-- Select with offset
SELECT * FROM table_name LIMIT 10 OFFSET 20;

-- Select distinct values
SELECT DISTINCT column1 FROM table_name;

-- Select with grouping
SELECT column1, COUNT(*) FROM table_name GROUP BY column1;

-- Select with having clause
SELECT column1, COUNT(*) FROM table_name GROUP BY column1 HAVING COUNT(*) > 5;

-- Select with joins
SELECT a.column1, b.column2 FROM table_a a INNER JOIN table_b b ON a.id = b.a_id;
SELECT a.column1, b.column2 FROM table_a a LEFT JOIN table_b b ON a.id = b.a_id;
SELECT a.column1, b.column2 FROM table_a a RIGHT JOIN table_b b ON a.id = b.a_id;
SELECT a.column1, b.column2 FROM table_a a FULL OUTER JOIN table_b b ON a.id = b.a_id;
SELECT a.column1, b.column2 FROM table_a a CROSS JOIN table_b b;

-- Select with subquery
SELECT * FROM table_name WHERE column1 IN (SELECT column1 FROM other_table);

-- Select with exists
SELECT * FROM table_a WHERE EXISTS (SELECT 1 FROM table_b WHERE table_b.a_id = table_a.id);

-- Select with case
SELECT column1, 
       CASE 
           WHEN condition1 THEN result1 
           WHEN condition2 THEN result2 
           ELSE result3 
       END AS new_column 
FROM table_name;

-- Select with union
SELECT column1 FROM table_a UNION SELECT column1 FROM table_b;

-- Select with union all (includes duplicates)
SELECT column1 FROM table_a UNION ALL SELECT column1 FROM table_b;

-- Select with intersect
SELECT column1 FROM table_a INTERSECT SELECT column1 FROM table_b;

-- Select with except
SELECT column1 FROM table_a EXCEPT SELECT column1 FROM table_b;

-- Common Table Expressions (CTE)
WITH cte_name AS (
    SELECT column1, column2 FROM table_name WHERE condition
)
SELECT * FROM cte_name;

-- Recursive CTE
WITH RECURSIVE cte_name AS (
    -- Base case
    SELECT id, parent_id, name FROM table_name WHERE parent_id IS NULL
    UNION ALL
    -- Recursive case
    SELECT t.id, t.parent_id, t.name FROM table_name t
    INNER JOIN cte_name c ON t.parent_id = c.id
)
SELECT * FROM cte_name;
```

## Transactions

```sql
-- Start transaction
BEGIN;
BEGIN TRANSACTION;
START TRANSACTION;

-- Commit transaction
COMMIT;
COMMIT TRANSACTION;

-- Rollback transaction
ROLLBACK;
ROLLBACK TRANSACTION;

-- Create savepoint
SAVEPOINT savepoint_name;

-- Rollback to savepoint
ROLLBACK TO SAVEPOINT savepoint_name;

-- Release savepoint
RELEASE SAVEPOINT savepoint_name;

-- Set transaction isolation level
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

## Views

```sql
-- Create view
CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;

-- Create or replace view
CREATE OR REPLACE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;

-- Create materialized view
CREATE MATERIALIZED VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;

-- Refresh materialized view
REFRESH MATERIALIZED VIEW view_name;

-- Refresh materialized view concurrently
REFRESH MATERIALIZED VIEW CONCURRENTLY view_name;

-- List views
\dv
SELECT viewname FROM pg_views WHERE schemaname = 'public';

-- List materialized views
\dm
SELECT matviewname FROM pg_matviews WHERE schemaname = 'public';

-- Show view definition
\d+ view_name

-- Drop view
DROP VIEW view_name;

-- Drop view if exists
DROP VIEW IF EXISTS view_name;

-- Drop materialized view
DROP MATERIALIZED VIEW view_name;
```

## Functions & Procedures

```sql
-- Create function
CREATE OR REPLACE FUNCTION function_name(param1 type, param2 type)
RETURNS return_type AS $$
BEGIN
    -- Function body
    RETURN value;
END;
$$ LANGUAGE plpgsql;

-- Create function with SQL
CREATE OR REPLACE FUNCTION function_name(param1 type, param2 type)
RETURNS return_type AS $$
    SELECT column1 FROM table_name WHERE condition;
$$ LANGUAGE sql;

-- Create procedure (PostgreSQL 11+)
CREATE OR REPLACE PROCEDURE procedure_name(param1 type, param2 type)
AS $$
BEGIN
    -- Procedure body
    INSERT INTO table_name VALUES (param1, param2);
    COMMIT;
END;
$$ LANGUAGE plpgsql;

-- Call procedure
CALL procedure_name(value1, value2);

-- List functions
\df
SELECT routine_name FROM information_schema.routines WHERE routine_type = 'FUNCTION' AND routine_schema = 'public';

-- List procedures
\dP
SELECT routine_name FROM information_schema.routines WHERE routine_type = 'PROCEDURE' AND routine_schema = 'public';

-- Show function definition
\sf function_name

-- Drop function
DROP FUNCTION function_name;
DROP FUNCTION function_name(param1_type, param2_type);

-- Drop procedure
DROP PROCEDURE procedure_name;
DROP PROCEDURE procedure_name(param1_type, param2_type);
```

## Triggers

```sql
-- Create trigger function
CREATE OR REPLACE FUNCTION trigger_function()
RETURNS TRIGGER AS $$
BEGIN
    -- Trigger function body
    NEW.column1 = UPPER(NEW.column1);
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Create trigger
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
EXECUTE FUNCTION trigger_function();

-- Create trigger with condition
CREATE TRIGGER trigger_name
BEFORE UPDATE ON table_name
FOR EACH ROW
WHEN (OLD.column1 IS DISTINCT FROM NEW.column1)
EXECUTE FUNCTION trigger_function();

-- List triggers
\dS
SELECT trigger_name FROM information_schema.triggers WHERE event_object_table = 'table_name';

-- Disable trigger
ALTER TABLE table_name DISABLE TRIGGER trigger_name;

-- Disable all triggers
ALTER TABLE table_name DISABLE TRIGGER ALL;

-- Enable trigger
ALTER TABLE table_name ENABLE TRIGGER trigger_name;

-- Enable all triggers
ALTER TABLE table_name ENABLE TRIGGER ALL;

-- Drop trigger
DROP TRIGGER trigger_name ON table_name;
```

## Sequences

```sql
-- Create sequence
CREATE SEQUENCE sequence_name;

-- Create sequence with options
CREATE SEQUENCE sequence_name
    INCREMENT BY 1
    MINVALUE 1
    MAXVALUE 1000000
    START WITH 1
    CACHE 1
    NO CYCLE;

-- List sequences
\ds
SELECT sequence_name FROM information_schema.sequences WHERE sequence_schema = 'public';

-- Get next value
SELECT nextval('sequence_name');

-- Get current value
SELECT currval('sequence_name');

-- Set sequence value
SELECT setval('sequence_name', 100);

-- Alter sequence
ALTER SEQUENCE sequence_name INCREMENT BY 10;

-- Restart sequence
ALTER SEQUENCE sequence_name RESTART WITH 1;

-- Drop sequence
DROP SEQUENCE sequence_name;
```

## Backup & Restore

```bash
# Backup database
pg_dump -h hostname -p port -U username -F c -b -v -f backup.dump database_name

# Backup specific tables
pg_dump -h hostname -p port -U username -F c -b -v -f backup.dump --table=table_name database_name

# Backup schema only
pg_dump -h hostname -p port -U username -F c -b -v -f backup.dump --schema-only database_name

# Backup data only
pg_dump -h hostname -p port -U username -F c -b -v -f backup.dump --data-only database_name

# Backup as SQL script
pg_dump -h hostname -p port -U username -F p -f backup.sql database_name

# Backup all databases
pg_dumpall -h hostname -p port -U username -f backup.sql

# Restore database
pg_restore -h hostname -p port -U username -d database_name -v backup.dump

# Restore with options
pg_restore -h hostname -p port -U username -d database_name -v --clean --create backup.dump

# Restore SQL script
psql -h hostname -p port -U username -d database_name -f backup.sql
```

## Performance & Monitoring

```sql
-- Show running queries
SELECT pid, age(clock_timestamp(), query_start), usename, query
FROM pg_stat_activity
WHERE query != '<IDLE>' AND query NOT ILIKE '%pg_stat_activity%'
ORDER BY query_start DESC;

-- Kill query
SELECT pg_cancel_backend(pid);

-- Kill connection
SELECT pg_terminate_backend(pid);

-- Table statistics
SELECT * FROM pg_stat_user_tables WHERE relname = 'table_name';

-- Index statistics
SELECT * FROM pg_stat_user_indexes WHERE relname = 'table_name';

-- Database statistics
SELECT * FROM pg_stat_database WHERE datname = 'database_name';

-- Analyze table
ANALYZE table_name;

-- Vacuum table
VACUUM table_name;

-- Vacuum full table
VACUUM FULL table_name;

-- Vacuum analyze table
VACUUM ANALYZE table_name;

-- Explain query plan
EXPLAIN SELECT * FROM table_name WHERE condition;

-- Explain analyze query
EXPLAIN ANALYZE SELECT * FROM table_name WHERE condition;

-- Explain with buffers
EXPLAIN (ANALYZE, BUFFERS) SELECT * FROM table_name WHERE condition;

-- Explain with format
EXPLAIN (ANALYZE, FORMAT JSON) SELECT * FROM table_name WHERE condition;

-- Show table bloat
SELECT
    schemaname,
    tablename,
    pg_size_pretty(pg_total_relation_size(schemaname || '.' || tablename)) as total_size,
    pg_size_pretty(pg_relation_size(schemaname || '.' || tablename)) as table_size,
    pg_size_pretty(pg_total_relation_size(schemaname || '.' || tablename) - pg_relation_size(schemaname || '.' || tablename)) as index_size
FROM pg_tables
WHERE schemaname = 'public'
ORDER BY pg_total_relation_size(schemaname || '.' || tablename) DESC;

-- Show index usage
SELECT
    indexrelname,
    relname,
    idx_scan,
    idx_tup_read,
    idx_tup_fetch
FROM pg_stat_user_indexes
JOIN pg_stat_user_tables ON pg_stat_user_indexes.relid = pg_stat_user_tables.relid
ORDER BY idx_scan DESC;

-- Show cache hit ratio
SELECT
    sum(heap_blks_read) as heap_read,
    sum(heap_blks_hit) as heap_hit,
    sum(heap_blks_hit) / (sum(heap_blks_hit) + sum(heap_blks_read)) as ratio
FROM pg_statio_user_tables;
```

## Roles & Privileges

```sql
-- List roles
\du
SELECT rolname FROM pg_roles;

-- Create role
CREATE ROLE role_name;

-- Create role with login
CREATE ROLE role_name WITH LOGIN PASSWORD 'password';

-- Create role with options
CREATE ROLE role_name WITH
    LOGIN
    PASSWORD 'password'
    SUPERUSER
    CREATEDB
    CREATEROLE
    REPLICATION
    CONNECTION LIMIT 10;

-- Alter role
ALTER ROLE role_name WITH PASSWORD 'new_password';

-- Grant role to user
GRANT role_name TO username;

-- Revoke role from user
REVOKE role_name FROM username;

-- Drop role
DROP ROLE role_name;

-- Show grants
\z table_name
SELECT grantee, privilege_type
FROM information_schema.role_table_grants
WHERE table_name = 'table_name';
```

## Extensions

```sql
-- List available extensions
SELECT name FROM pg_available_extensions;

-- List installed extensions
\dx
SELECT extname FROM pg_extension;

-- Install extension
CREATE EXTENSION extension_name;

-- Install extension with schema
CREATE EXTENSION extension_name SCHEMA schema_name;

-- Update extension
ALTER EXTENSION extension_name UPDATE TO 'new_version';

-- Drop extension
DROP EXTENSION extension_name;

-- Common extensions
CREATE EXTENSION postgis;         -- GIS support
CREATE EXTENSION pg_stat_statements; -- Query statistics
CREATE EXTENSION pgcrypto;        -- Cryptographic functions
CREATE EXTENSION uuid-ossp;       -- UUID generation
CREATE EXTENSION hstore;          -- Key-value store
CREATE EXTENSION ltree;           -- Hierarchical tree structure
CREATE EXTENSION pg_trgm;         -- Trigram matching for text search
CREATE EXTENSION tablefunc;       -- Table functions
CREATE EXTENSION intarray;        -- Integer array functions
CREATE EXTENSION postgres_fdw;    -- Foreign data wrapper
```

## Miscellaneous

```sql
-- Show PostgreSQL version
SELECT version();

-- Show current user
SELECT current_user;

-- Show current database
SELECT current_database();

-- Show current schema
SELECT current_schema();

-- Show search path
SHOW search_path;

-- Show server encoding
SHOW server_encoding;

-- Show timezone
SHOW timezone;

-- Show data directory
SHOW data_directory;

-- Show configuration file
SHOW config_file;

-- Show parameter settings
SHOW ALL;

-- Show specific parameter
SHOW parameter_name;

-- Set parameter
SET parameter_name = value;

-- Reset parameter
RESET parameter_name;

-- Get current timestamp
SELECT now();
SELECT current_timestamp;

-- Format date/time
SELECT to_char(current_timestamp, 'YYYY-MM-DD HH24:MI:SS');

-- Generate series
SELECT * FROM generate_series(1, 10);
SELECT * FROM generate_series('2023-01-01'::date, '2023-01-10'::date, '1 day');

-- Random number
SELECT random();

-- UUID generation
SELECT gen_random_uuid();

-- JSON operations
SELECT '{ "name": "John", "age": 30 }'::jsonb -> 'name';
SELECT '{ "name": "John", "age": 30 }'::jsonb ->> 'name';
SELECT jsonb_set('{ "name": "John" }'::jsonb, '{age}', '30');

-- Array operations
SELECT ARRAY[1, 2, 3] || ARRAY[4, 5, 6];
SELECT array_agg(column_name) FROM table_name;
SELECT unnest(ARRAY[1, 2, 3]);

-- Regular expressions
SELECT regexp_matches('abc123', '\d+');
SELECT regexp_replace('abc123', '\d+', 'XYZ');

-- String operations
SELECT concat('Hello', ' ', 'World');
SELECT substring('Hello World' from 1 for 5);
SELECT position('World' in 'Hello World');
SELECT trim(' Hello World ');

-- Window functions
SELECT column1, column2, 
       row_number() OVER (PARTITION BY column1 ORDER BY column2) as row_num,
       rank() OVER (PARTITION BY column1 ORDER BY column2) as rank,
       dense_rank() OVER (PARTITION BY column1 ORDER BY column2) as dense_rank,
       lag(column2) OVER (PARTITION BY column1 ORDER BY column2) as prev_value,
       lead(column2) OVER (PARTITION BY column1 ORDER BY column2) as next_value
FROM table_name;
```