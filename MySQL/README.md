# MySQL Commands Reference

## Connection & Authentication

```sql
-- Connect to MySQL server
mysql -h hostname -u username -p

-- Connect to specific database
mysql -h hostname -u username -p database_name

-- Connect with specific port
mysql -h hostname -P port -u username -p

-- Connect using socket
mysql -S /path/to/socket -u username -p

-- Execute SQL from command line
mysql -u username -p -e "SELECT VERSION();"

-- Connect using config file
mysql --defaults-file=/path/to/my.cnf

-- Change user password
ALTER USER 'username'@'hostname' IDENTIFIED BY 'new_password';

-- Create new user
CREATE USER 'username'@'hostname' IDENTIFIED BY 'password';

-- Grant privileges
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'hostname';
GRANT SELECT, INSERT, UPDATE ON database_name.* TO 'username'@'hostname';

-- Revoke privileges
REVOKE ALL PRIVILEGES ON database_name.* FROM 'username'@'hostname';

-- Reload privileges
FLUSH PRIVILEGES;

-- Show grants for user
SHOW GRANTS FOR 'username'@'hostname';

-- Delete user
DROP USER 'username'@'hostname';
```

## Database Operations

```sql
-- Show all databases
SHOW DATABASES;

-- Create database
CREATE DATABASE database_name;

-- Create database with specific character set and collation
CREATE DATABASE database_name CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Select database
USE database_name;

-- Show current database
SELECT DATABASE();

-- Drop database
DROP DATABASE database_name;

-- Rename database (MySQL doesn't support direct renaming)
-- Method 1: Create new database and move tables
CREATE DATABASE new_database_name;
-- Then use mysqldump or CREATE TABLE ... SELECT to move data

-- Show database creation statement
SHOW CREATE DATABASE database_name;

-- Check database size
SELECT table_schema AS "Database", 
       ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Size (MB)" 
FROM information_schema.TABLES 
GROUP BY table_schema;
```

## Table Operations

```sql
-- Show all tables
SHOW TABLES;

-- Show tables with filter
SHOW TABLES LIKE 'pattern%';

-- Create table
CREATE TABLE table_name (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Show table structure
DESCRIBE table_name;
SHOW COLUMNS FROM table_name;

-- Show create table statement
SHOW CREATE TABLE table_name;

-- Rename table
RENAME TABLE old_table_name TO new_table_name;

-- Drop table
DROP TABLE table_name;

-- Drop table if exists
DROP TABLE IF EXISTS table_name;

-- Truncate table (remove all rows)
TRUNCATE TABLE table_name;

-- Copy table structure
CREATE TABLE new_table LIKE original_table;

-- Copy table structure and data
CREATE TABLE new_table AS SELECT * FROM original_table;

-- Add column
ALTER TABLE table_name ADD COLUMN column_name VARCHAR(100);

-- Add column with position
ALTER TABLE table_name ADD COLUMN column_name VARCHAR(100) AFTER existing_column;
ALTER TABLE table_name ADD COLUMN column_name VARCHAR(100) FIRST;

-- Modify column
ALTER TABLE table_name MODIFY COLUMN column_name VARCHAR(200) NOT NULL;

-- Rename column
ALTER TABLE table_name CHANGE COLUMN old_name new_name VARCHAR(100);

-- Drop column
ALTER TABLE table_name DROP COLUMN column_name;

-- Add primary key
ALTER TABLE table_name ADD PRIMARY KEY (column_name);

-- Add foreign key
ALTER TABLE table_name ADD CONSTRAINT fk_name FOREIGN KEY (column_name) REFERENCES ref_table(ref_column);

-- Drop foreign key
ALTER TABLE table_name DROP FOREIGN KEY fk_name;

-- Add index
CREATE INDEX index_name ON table_name (column_name);
ALTER TABLE table_name ADD INDEX index_name (column_name);

-- Add unique index
CREATE UNIQUE INDEX index_name ON table_name (column_name);
ALTER TABLE table_name ADD UNIQUE INDEX index_name (column_name);

-- Drop index
DROP INDEX index_name ON table_name;
ALTER TABLE table_name DROP INDEX index_name;

-- Show indexes
SHOW INDEX FROM table_name;
```

## Data Manipulation

```sql
-- Insert row
INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2');

-- Insert multiple rows
INSERT INTO table_name (column1, column2) VALUES 
    ('value1', 'value2'),
    ('value3', 'value4');

-- Insert with select
INSERT INTO table_name (column1, column2)
SELECT column1, column2 FROM other_table WHERE condition;

-- Update rows
UPDATE table_name SET column1 = 'value1', column2 = 'value2' WHERE condition;

-- Delete rows
DELETE FROM table_name WHERE condition;

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

-- Select with pagination
SELECT * FROM table_name LIMIT 10, 20; -- Skip 10, take 20

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
```

## Transactions

```sql
-- Start transaction
START TRANSACTION;

-- Commit transaction
COMMIT;

-- Rollback transaction
ROLLBACK;

-- Set autocommit
SET autocommit = 0; -- Disable autocommit
SET autocommit = 1; -- Enable autocommit

-- Create savepoint
SAVEPOINT savepoint_name;

-- Rollback to savepoint
ROLLBACK TO SAVEPOINT savepoint_name;

-- Release savepoint
RELEASE SAVEPOINT savepoint_name;
```

## Views

```sql
-- Create view
CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;

-- Create or replace view
CREATE OR REPLACE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;

-- Show views
SHOW FULL TABLES WHERE table_type = 'VIEW';

-- Show view definition
SHOW CREATE VIEW view_name;

-- Drop view
DROP VIEW view_name;

-- Drop view if exists
DROP VIEW IF EXISTS view_name;
```

## Stored Procedures & Functions

```sql
-- Create stored procedure
DELIMITER //
CREATE PROCEDURE procedure_name(IN param1 INT, OUT param2 VARCHAR(100))
BEGIN
    -- Procedure body
    SELECT column1 INTO param2 FROM table_name WHERE id = param1;
END //
DELIMITER ;

-- Call stored procedure
CALL procedure_name(1, @result);
SELECT @result;

-- Create function
DELIMITER //
CREATE FUNCTION function_name(param1 INT) RETURNS INT
DETERMINISTIC
BEGIN
    DECLARE result INT;
    -- Function body
    SET result = param1 * 2;
    RETURN result;
END //
DELIMITER ;

-- Call function
SELECT function_name(10);

-- Show procedures
SHOW PROCEDURE STATUS WHERE Db = 'database_name';

-- Show functions
SHOW FUNCTION STATUS WHERE Db = 'database_name';

-- Show procedure definition
SHOW CREATE PROCEDURE procedure_name;

-- Show function definition
SHOW CREATE FUNCTION function_name;

-- Drop procedure
DROP PROCEDURE procedure_name;

-- Drop function
DROP FUNCTION function_name;
```

## Triggers

```sql
-- Create trigger
DELIMITER //
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
BEGIN
    -- Trigger body
    SET NEW.column1 = UPPER(NEW.column1);
END //
DELIMITER ;

-- Show triggers
SHOW TRIGGERS;

-- Show triggers for specific table
SHOW TRIGGERS LIKE 'table_name';

-- Drop trigger
DROP TRIGGER trigger_name;
```

## Events

```sql
-- Enable event scheduler
SET GLOBAL event_scheduler = ON;

-- Create event
DELIMITER //
CREATE EVENT event_name
ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 HOUR
DO
BEGIN
    -- Event body
    DELETE FROM table_name WHERE created_at < NOW() - INTERVAL 7 DAY;
END //
DELIMITER ;

-- Create recurring event
DELIMITER //
CREATE EVENT event_name
ON SCHEDULE EVERY 1 DAY STARTS '2023-01-01 00:00:00'
DO
BEGIN
    -- Event body
    DELETE FROM table_name WHERE created_at < NOW() - INTERVAL 7 DAY;
END //
DELIMITER ;

-- Show events
SHOW EVENTS;

-- Show events from specific schema
SHOW EVENTS FROM database_name;

-- Drop event
DROP EVENT event_name;

-- Enable/disable event
ALTER EVENT event_name ENABLE;
ALTER EVENT event_name DISABLE;
```

## Information Schema

```sql
-- List all tables in a database
SELECT table_name FROM information_schema.tables WHERE table_schema = 'database_name';

-- List all columns in a table
SELECT column_name, data_type, is_nullable FROM information_schema.columns 
WHERE table_schema = 'database_name' AND table_name = 'table_name';

-- List all indexes
SELECT * FROM information_schema.statistics WHERE table_schema = 'database_name';

-- List all foreign keys
SELECT * FROM information_schema.key_column_usage 
WHERE referenced_table_schema = 'database_name';

-- List all procedures
SELECT * FROM information_schema.routines 
WHERE routine_schema = 'database_name' AND routine_type = 'PROCEDURE';

-- List all functions
SELECT * FROM information_schema.routines 
WHERE routine_schema = 'database_name' AND routine_type = 'FUNCTION';

-- List all triggers
SELECT * FROM information_schema.triggers WHERE trigger_schema = 'database_name';

-- List all views
SELECT * FROM information_schema.views WHERE table_schema = 'database_name';

-- List all events
SELECT * FROM information_schema.events WHERE event_schema = 'database_name';
```

## Backup & Restore

```bash
# Backup database
mysqldump -u username -p database_name > backup.sql

# Backup specific tables
mysqldump -u username -p database_name table1 table2 > backup.sql

# Backup multiple databases
mysqldump -u username -p --databases db1 db2 > backup.sql

# Backup all databases
mysqldump -u username -p --all-databases > backup.sql

# Backup with options
mysqldump -u username -p --opt --events --routines --triggers database_name > backup.sql

# Backup structure only (no data)
mysqldump -u username -p --no-data database_name > schema.sql

# Backup data only (no structure)
mysqldump -u username -p --no-create-info database_name > data.sql

# Compress backup
mysqldump -u username -p database_name | gzip > backup.sql.gz

# Restore database
mysql -u username -p database_name < backup.sql

# Restore compressed backup
gunzip < backup.sql.gz | mysql -u username -p database_name

# Restore with progress bar (using pv)
pv backup.sql | mysql -u username -p database_name
```

## Performance & Optimization

```sql
-- Show running processes
SHOW PROCESSLIST;

-- Kill a process
KILL process_id;

-- Show table status
SHOW TABLE STATUS LIKE 'table_name';

-- Analyze table
ANALYZE TABLE table_name;

-- Optimize table
OPTIMIZE TABLE table_name;

-- Check table
CHECK TABLE table_name;

-- Repair table
REPAIR TABLE table_name;

-- Show status
SHOW STATUS;

-- Show status with filter
SHOW STATUS LIKE 'Threads%';

-- Show variables
SHOW VARIABLES;

-- Show variables with filter
SHOW VARIABLES LIKE 'max_connections';

-- Set variable
SET GLOBAL max_connections = 200;
SET SESSION sort_buffer_size = 1048576;

-- Show engine status
SHOW ENGINE INNODB STATUS;

-- Show open tables
SHOW OPEN TABLES;

-- Explain query plan
EXPLAIN SELECT * FROM table_name WHERE condition;

-- Explain with extended info
EXPLAIN EXTENDED SELECT * FROM table_name WHERE condition;

-- Explain with JSON format
EXPLAIN FORMAT=JSON SELECT * FROM table_name WHERE condition;

-- Show profile
SET profiling = 1;
SELECT * FROM table_name WHERE condition;
SHOW PROFILES;
SHOW PROFILE FOR QUERY 1;
```

## Replication

```sql
-- Show master status
SHOW MASTER STATUS;

-- Show slave status
SHOW SLAVE STATUS\G

-- Start slave
START SLAVE;

-- Stop slave
STOP SLAVE;

-- Reset slave
RESET SLAVE;

-- Change master
CHANGE MASTER TO MASTER_HOST='host', MASTER_USER='user', MASTER_PASSWORD='password', MASTER_LOG_FILE='file', MASTER_LOG_POS=position;
```

## Miscellaneous

```sql
-- Show MySQL version
SELECT VERSION();

-- Show current date and time
SELECT NOW();

-- Show current user
SELECT USER();

-- Show current database
SELECT DATABASE();

-- Show MySQL status
STATUS;

-- Show warnings
SHOW WARNINGS;

-- Show errors
SHOW ERRORS;

-- Show character set
SHOW CHARACTER SET;

-- Show collation
SHOW COLLATION;

-- Set character set
SET NAMES 'utf8mb4';

-- Set SQL mode
SET sql_mode = 'STRICT_TRANS_TABLES,NO_ENGINE_SUBSTITUTION';

-- Show SQL mode
SELECT @@sql_mode;

-- Show create database statement
SHOW CREATE DATABASE database_name;

-- Show create table statement
SHOW CREATE TABLE table_name;

-- Show table size
SELECT 
    table_name AS 'Table', 
    ROUND(((data_length + index_length) / 1024 / 1024), 2) AS 'Size (MB)'
FROM information_schema.TABLES
WHERE table_schema = 'database_name'
ORDER BY (data_length + index_length) DESC;
```