# SQL — Complete Reference & Practice

---

## Table of Contents

1. [MySQL Reference](#mysql-reference)
2. [MySQL Interview Tips](#mysql-interview-tips)
3. [SQL Practice Questions](#sql-practice-questions)

---

# MySQL Reference

## Database Creation and Usage

### CREATE DATABASE
```sql
CREATE DATABASE temp;
USE temp;
```

### CREATE TABLE
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(255)
);
```

## Inserting Data

### INSERT INTO
```sql
INSERT INTO student (id, name)
VALUES (1, 'Parit'),
       (2, 'Shruti');

INSERT INTO table_name (col1, col2, col3) 
VALUES (v1, v2, v3),
       (val1, val2, val3);
```

## Data Types

- **CHAR**: Fixed-length data size
- **VARCHAR**: Variable-length data size
- **TEXT**: Large text data
- **INT, SMALLINT, MEDIUMINT, BIGINT**: Integer types
- **FLOAT, DOUBLE**: Floating-point numbers
- **DATE, DATETIME, TIME**: Date and time
- **BOOLEAN**: True/False values
- **ENUM**: One of the preset values
- **SET**: One or many of the preset values

## Signed and Unsigned Integers
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    marks INT UNSIGNED
);
```

## Deleting Databases and Tables

### DROP
```sql
DROP DATABASE db_name;
DROP TABLE table_name;
DROP VIEW view_name;
```

## Displaying Databases and Tables

### SHOW
```sql
SHOW DATABASES;
SHOW TABLES;
```

## Conditional Operations

### IF EXISTS / IF NOT EXISTS
```sql
DROP DATABASE IF EXISTS db_name;
DROP VIEW IF EXISTS view_name;
CREATE DATABASE IF NOT EXISTS db_name;
```

## Keys and Constraints

### PRIMARY KEY and AUTO_INCREMENT
```sql
CREATE TABLE student (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255),
    marks INT UNSIGNED
);
```

### PRIMARY KEY and FOREIGN KEY
```sql
CREATE TABLE student (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    marks INT UNSIGNED,
    course_id INT,
    FOREIGN KEY (course_id) REFERENCES course_table(id)
);
```

### UNIQUE
```sql
CREATE TABLE customer (
    email VARCHAR(1024) UNIQUE
);
```

### CHECK
```sql
CREATE TABLE customer (
    age INT,
    CONSTRAINT age_check CHECK (age > 12)
);
```

### DEFAULT
```sql
CREATE TABLE account (
    saving_rate DOUBLE NOT NULL DEFAULT 4.25
);
```

## Modifying Tables

### ALTER

#### Add Column
```sql
ALTER TABLE table_name
ADD new_col_name datatype,
ADD new_col_name_2 datatype;
```

#### Modify Column
```sql
ALTER TABLE table_name
MODIFY col_name col_datatype;
```

#### Change Column
```sql
ALTER TABLE table_name
CHANGE COLUMN old_col_name new_col_name new_col_datatype;
```

#### Drop Column
```sql
ALTER TABLE table_name
DROP COLUMN col_name;
```

#### Rename Table
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```

## Querying Data

### SELECT
```sql
SELECT * FROM table_name;
```

### WHERE
```sql
SELECT * FROM customer WHERE age > 18;
```

### BETWEEN
```sql
SELECT * FROM customer WHERE age BETWEEN 0 AND 100;
```

### IN
```sql
SELECT * FROM officers WHERE officer_name IN ('Lakshay', 'Maharana Pratap');
```

### AND/OR/NOT
```sql
SELECT * FROM table_name WHERE cond1 AND cond2;
SELECT * FROM table_name WHERE cond1 OR cond2;
SELECT * FROM table_name WHERE col_name NOT IN (1, 2, 3, 4);
```

### IS NULL
```sql
SELECT * FROM customer WHERE prime_status IS NULL;
```

### Pattern Searching / Wildcards ('%', '_')
```sql
SELECT * FROM customer WHERE name LIKE '%p_';
```

### ORDER BY
```sql
SELECT * FROM customer ORDER BY first_name DESC, second_name ASC;
```

### DISTINCT
```sql
SELECT DISTINCT department FROM worker;
```

### LIMIT
```sql
SELECT * FROM table_name ORDER BY AGE DESC LIMIT 5;
SELECT * FROM table_name ORDER BY AGE DESC LIMIT 2, 1;
```

## Updating Data

### UPDATE
```sql
UPDATE table_name SET col1 = 1, col2 = 'abc' WHERE id = 1;
```

### Update Multiple Rows
```sql
UPDATE student SET standard = standard + 1;
```

### Handling SQL_SAFE_UPDATES
```sql
SET SQL_SAFE_UPDATES = 0;
```

## Deleting Data

### DELETE
```sql
DELETE FROM table_name WHERE id = 1;
```

### DELETE with Constraints

#### DELETE CASCADE
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    delivery_date DATE,
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE CASCADE
);
```

#### DELETE SET NULL
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    delivery_date DATE,
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE SET NULL
);
```

## Replacing Data

### REPLACE INTO
```sql
REPLACE INTO student (id, class) VALUES (4, 3);
REPLACE INTO table_name SET id = 4, class = 3;
```

## Joins

### INNER JOIN
```sql
SELECT column_list FROM table1 
INNER JOIN table2 ON condition1
INNER JOIN table3 ON condition2;
```

### LEFT OUTER JOIN
```sql
SELECT columns FROM table1 
LEFT JOIN table2 ON join_condition;
```

### RIGHT OUTER JOIN
```sql
SELECT columns FROM table1 
RIGHT JOIN table2 ON join_condition;
```

### FULL OUTER JOIN
```sql
SELECT columns FROM table1 AS t1 
LEFT JOIN table2 AS t2 ON t1.id = t2.id
UNION
SELECT columns FROM table1 AS t1 
RIGHT JOIN table2 AS t2 ON t1.id = t2.id;
```

### CROSS JOIN
```sql
SELECT column_list FROM table1 
CROSS JOIN table2;
```

### Joins Without Using Join Keywords
```sql
SELECT artist_name, album_name, year_recorded
FROM artist, album
WHERE artist.id = album.artist_id;
```

## Set Operations

### UNION
```sql
SELECT * FROM table1
UNION
SELECT * FROM table2;
```

### INTERSECT
```sql
SELECT DISTINCT column_list 
FROM table1 
INNER JOIN table2 
ON table1.column = table2.column;
```

### MINUS
```sql
SELECT * 
FROM table1
LEFT JOIN table2 
USING (column)
WHERE table2.column IS NULL;
```

## Subqueries

```sql
SELECT * FROM table1 WHERE col1 IN (SELECT col1 FROM table2);
SELECT * FROM table1 WHERE col1 > ANY (SELECT col1 FROM table2);
SELECT * FROM table1 WHERE EXISTS (SubQuery);
SELECT MAX(rating) FROM (SELECT * FROM movie WHERE country = 'India') AS temp;
```

## Co-related Subqueries

### Third Largest Age
```sql
SELECT * 
FROM employee e1
WHERE 3 = (
    SELECT COUNT(e2.age)
    FROM employee e2
    WHERE e2.age >= e1.age
);
```

### Third Smallest Age
```sql
SELECT * 
FROM employee e1
WHERE 3 = (
    SELECT COUNT(e2.age)
    FROM employee e2
    WHERE e2.age <= e1.age
);
```

## Views

### CREATE VIEW
```sql
CREATE VIEW view_name AS 
SELECT sr_no, first_name FROM student;
SELECT * FROM view_name;
```

## String Functions

- **UPPER('parit')** → `'PARIT'`
- **LOWER('PARIT')** → `'parit'`
- **SUBSTRING(str, start, length)** — e.g. `SUBSTRING('Parit', 2, 3)` → `'ari'` (1-indexed)
- **INSTR(str1, str2)** — position of first occurrence; e.g. `INSTR('Parit', 'it')` → `4` (1-indexed)
- **LTRIM(str)** — removes leading spaces
- **RTRIM(str)** — removes trailing spaces
- **LENGTH(str)** — e.g. `LENGTH('Parit')` → `5`
- **REPLACE(str1, str2, str3)** — e.g. `REPLACE('Parit', 'a', 'o')` → `'Porit'`
- **CONCAT(str1, str2, ...)** — e.g. `CONCAT('Pa', 'rit')` → `'Parit'`

---

# MySQL Interview Tips

## LIKE
- `%` — zero, one, or multiple characters
- `_` — exactly one character

## REGEXP
```sql
SELECT user_id, name, mail
FROM Users
WHERE mail REGEXP '^[a-zA-Z]{1}[a-zA-Z0-9\\_\\.\\-]*\\@leetcode\\.com$';
```

## CASE
```sql
SELECT CASE 
    WHEN gender = 'M' THEN 'Male'
    WHEN gender = 'F' THEN 'Female'
    ELSE 'Others'
    END AS gender
FROM employee;
```

## DATE_FORMAT()
```sql
SELECT DATE_FORMAT(<column>, '%d-%m-%Y') AS date_value
```

| Format | Meaning |
|--------|---------|
| `%M` | Month name in full (January to December) |
| `%m` | Month as numeric (00–12) |
| `%Y` | Year as 4-digit numeric |
| `%y` | Year as 2-digit numeric |
| `%d` | Day of month as numeric (01–31) |

## CAST
```sql
CAST(<exp> AS DECIMAL)   -- also FLOAT, CHAR
```

## Window Functions — Ranking

| Function | Ties get same rank? | Skips next rank? | Unique per row? |
|----------|---------------------|------------------|-----------------|
| `ROW_NUMBER()` | No | No | Yes |
| `RANK()` | Yes | Yes | No |
| `DENSE_RANK()` | Yes | No | No |

## Bitwise Aggregate Functions

`BIT_OR()`, `BIT_AND()`, `BIT_XOR()` — apply the bitwise operation across an entire column (like `SUM`) and return a single value.

## WITH Clause (CTE)

```sql
WITH table1 (col1, col2) AS (
    -- query1
),
table2 (col1, col2) AS (
    -- query2
)
SELECT *
FROM table1
JOIN table2 ON table1.col1 = table2.col1;
```

**Wrong** — cannot reference CTE columns with dot notation in WHERE:
```sql
WITH table1 (avg_salary) AS (
    SELECT AVG(salary) FROM employee
)
SELECT * 
FROM employee 
WHERE salary > table1.avg_salary;  -- WRONG
```

**Right** — use a subquery or CROSS JOIN:
```sql
WITH table1 (avg_salary) AS (
    SELECT AVG(salary) FROM employee
)
SELECT * 
FROM employee 
WHERE salary > (SELECT avg_salary FROM table1);
```

```sql
WITH table1 (avg_salary) AS (
    SELECT AVG(salary) FROM employee
)
SELECT e.* 
FROM employee e
CROSS JOIN table1
WHERE e.salary > table1.avg_salary;
```

---

# SQL Practice Questions

## 10-14-2025

---

### Bitwise User Permissions Analysis

**Schema**
```sql
Table: user_permissions
+-------------+------+
| Column Name | Type |
+-------------+------+
| user_id     | INT  |
| permissions | INT  |
+-------------+------+
user_id is the primary key.
```

Each bit in `permissions` represents a specific permission (1 = has it, 0 = does not).

Return `common_perms` (BIT_AND of all permissions) and `any_perms` (BIT_OR of all permissions).

**Example**

| user_id | permissions |
|---------|-------------|
| 1 | 5 (0101) |
| 2 | 12 (1100) |
| 3 | 7 (0111) |
| 4 | 3 (0011) |

Output: `common_perms = 0`, `any_perms = 15`

**Solution**
```sql
SELECT 
  BIT_AND(permissions) AS common_perms,
  BIT_OR(permissions) AS any_perms
FROM user_permissions;
```

---

### Class Performance

**Schema**
```sql
Table: Scores
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | INT     |
| student_name | VARCHAR |
| assignment1  | INT     |
| assignment2  | INT     |
| assignment3  | INT     |
+--------------+---------+
student_id is the primary key.
```

Find the difference between the highest and lowest total score (sum of all 3 assignments) across all students.

**Solution**
```sql
WITH table1 AS (
    SELECT assignment1 + assignment2 + assignment3 AS SCORE
    FROM Scores
)
SELECT MAX(SCORE) - MIN(SCORE) AS difference_in_score
FROM table1;
```

---

### Find the Team Size

**Schema**
```sql
Table: Employee
+-------------+-----+
| Column Name | Type|
+-------------+-----+
| employee_id | int |
| team_id     | int |
+-------------+-----+
employee_id is the primary key.
```

For each employee, return how many members (including themselves) are in their team.

**Solution**
```sql
-- Using CTE + JOIN
WITH table1 AS (
  SELECT team_id, COUNT(employee_id) AS team_size
  FROM Employee
  GROUP BY team_id
)
SELECT employee_id, team_size
FROM Employee
LEFT JOIN table1 ON Employee.team_id = table1.team_id;
```

```sql
-- Using window function
SELECT
  employee_id,
  COUNT(*) OVER (PARTITION BY team_id) AS team_size
FROM Employee;
```

---

### Second Highest Salary II

**Schema**
```sql
Table: Employee
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | INT  |
| salary      | INT  |
+-------------+------+
id is the primary key.
```

Return the second highest **distinct** salary, or `NULL` if none exists.

**Solution**
```sql
WITH table1 AS (
    SELECT DISTINCT salary FROM Employee
),
table2 AS (
    SELECT *, ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank_
    FROM table1
),
table3 AS (
    SELECT * FROM table2 WHERE rank_ = 2
),
table4 AS (
    SELECT 2 AS rank_
)
SELECT salary AS SecondHighestSalary
FROM table4
LEFT JOIN table3 ON table4.rank_ = table3.rank_;
```

---

### Students With Invalid Departments

**Schema**
```sql
Table: Departments        Table: Students
+------------+---------+  +--------------+---------+
| Column Name| Type    |  | Column Name  | Type    |
+------------+---------+  +--------------+---------+
| id         | INT     |  | id           | INT     |
| name       | VARCHAR |  | name         | VARCHAR |
+------------+---------+  | department_id| INT     |
                          +--------------+---------+
```

Find students whose `department_id` does not exist in the `Departments` table.

**Solution**
```sql
SELECT DISTINCT Students.id, Students.name
FROM Students
LEFT JOIN Departments ON Students.department_id = Departments.id
WHERE Departments.name IS NULL;
```

---

## 10-15-2025

---

### Drop Type 1 Orders for Customers With Type 0 Orders

**Schema**
```sql
Table: Orders
+-------------+-----+
| Column Name | Type|
+-------------+-----+
| order_id    | INT |
| customer_id | INT |
| order_type  | INT |  -- 0 or 1
+-------------+-----+
order_id is the primary key.
```

If a customer has any type-0 order, exclude all their type-1 orders. Otherwise return all their orders.

**Solution**
```sql
WITH table1 AS (
  SELECT * FROM Orders WHERE order_type = 0
),
table2 AS (
  SELECT * FROM Orders WHERE order_type = 1
),
table3 AS (
  SELECT table2.order_id, table2.customer_id, table2.order_type
  FROM table2
  LEFT JOIN table1 ON table1.customer_id = table2.customer_id
  WHERE table1.customer_id IS NULL
)
SELECT * FROM table1
UNION
SELECT * FROM table3;
```

---

### First Letter Capitalization II

**Schema**
```sql
Table: user_content
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| content_id  | INT     |
| content_text| VARCHAR |
+-------------+---------+
content_id is the primary key.
```

Capitalize the first letter of every word (including each part of hyphenated words) and lowercase the rest. Return `content_id`, `original_text`, `converted_text`.

**Note:** `REGEXP_REPLACE` with backreferences to `UPPER()` does not work in MySQL — MySQL's `REGEXP_REPLACE` cannot apply functions to capture groups. This problem typically requires a recursive CTE or user-defined function in MySQL.

---

### Running Total for Different Genders

**Schema**
```sql
Table: Scores
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| player_name  | VARCHAR |
| gender       | VARCHAR |
| day          | DATE    |
| score_points | INT     |
+--------------+---------+
Primary key: (gender, day)
```

For each (gender, day), compute the cumulative sum of `score_points` ordered by day within each gender.

**Solution**
```sql
WITH table1 AS (
    SELECT gender, day, SUM(score_points) AS total
    FROM Scores
    GROUP BY day, gender
)
SELECT 
    gender, 
    day,
    SUM(total) OVER (
        PARTITION BY gender 
        ORDER BY day 
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS total
FROM table1
ORDER BY gender, day;
```

---

## 16-10-2025

---

### Apples & Oranges

**Schema**
```sql
Table: Sales
+-------------+------+
| Column Name | Type |
+-------------+------+
| sale_date   | date |
| fruit       | enum |  -- 'apples' or 'oranges'
| sold_num    | int  |
+-------------+------+
(sale_date, fruit) is the primary key.
```

For each day, return `apples sold − oranges sold`.

**Solution**
```sql
WITH table1 AS (SELECT * FROM Sales WHERE fruit = 'oranges'),
table2 AS (SELECT * FROM Sales WHERE fruit = 'apples'),
table3 AS (
  SELECT table2.sale_date, table2.sold_num AS apples, table1.sold_num AS oranges
  FROM table2 LEFT JOIN table1 ON table2.sale_date = table1.sale_date
  UNION
  SELECT table1.sale_date, table2.sold_num AS apples, table1.sold_num AS oranges
  FROM table2 RIGHT JOIN table1 ON table2.sale_date = table1.sale_date
)
SELECT
  sale_date,
  CASE
    WHEN oranges IS NOT NULL AND apples IS NOT NULL THEN apples - oranges
    WHEN oranges IS NULL THEN apples
    WHEN apples IS NULL THEN -oranges
  END AS diff
FROM table3
ORDER BY sale_date;
```

---

## 17-10-2025

---

### All People Report to the Given Manager

**Schema**
```sql
Table: Employees
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
| manager_id  | int     |
+-------------+---------+
employee_id is the primary key.
```

Find all employees who directly or indirectly report to the top-level manager (the one with `manager_id IS NULL`).

**Solution**
```sql
WITH RECURSIVE
table1 AS (
    SELECT employee_id FROM Employees WHERE manager_id IS NULL
),
hierarchy AS (
    SELECT e.employee_id, e.name, e.manager_id
    FROM Employees e
    WHERE e.manager_id IN (SELECT employee_id FROM table1)

    UNION

    SELECT e.employee_id, e.name, h.manager_id
    FROM Employees e
    INNER JOIN hierarchy h ON e.manager_id = h.employee_id
)
SELECT DISTINCT employee_id, name, manager_id
FROM hierarchy
ORDER BY employee_id;
```

---

### Capital Gain/Loss

**Schema**
```sql
Table: Stocks
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| stock_name     | varchar |
| operation      | enum    |  -- 'Buy' or 'Sell'
| operation_day  | int     |
| price          | int     |
+----------------+---------+
Primary key: (stock_name, operation_day)
```

For each stock, sum up net gain/loss: Sell adds price, Buy subtracts price.

**Solution**
```sql
SELECT 
    stock_name,
    SUM(
        CASE
            WHEN operation = 'Buy' THEN -price
            ELSE price
        END
    ) AS capital_gain_loss
FROM Stocks
GROUP BY stock_name;
```

---

### DNA Pattern Recognition

**Schema**
```sql
Table: Samples
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| sample_id    | int     |
| dna_sequence | varchar |
+--------------+---------+
sample_id is the primary key.
```

For each DNA sequence, return flags: `has_start` (starts with "ATG"), `has_stop` (ends with "TAA", "TAG", or "TGA"), `has_atat` (contains "ATAT").

**Solution**
```sql
SELECT *,
    CASE WHEN dna_sequence REGEXP '^ATG' THEN 1 ELSE 0 END AS has_start,
    CASE WHEN dna_sequence REGEXP '(TAA|TAG|TGA)$' THEN 1 ELSE 0 END AS has_stop,
    CASE WHEN dna_sequence REGEXP 'ATAT' THEN 1 ELSE 0 END AS has_atat
FROM Samples
ORDER BY sample_id ASC;
```

---

## 18-10-2025

---

### Calculate the Influence of Each Salesperson

**Schema**
```sql
Salesperson: salesperson_id (PK), name
Customer:    customer_id (PK), salesperson_id, name
Orders:      order_id (PK), customer_id, product_id, order_date, quantity
Product:     product_id (PK), name, price
```

Influence = total `price × quantity` across all orders from all customers assigned to each salesperson. Return 0 if no orders.

**Solution**
```sql
WITH table1 AS (
  SELECT order_id, customer_id, quantity * price AS amount
  FROM Orders
  LEFT JOIN Product ON Orders.product_id = Product.product_id
),
table2 AS (
  SELECT customer_id, SUM(amount) AS Total
  FROM table1
  GROUP BY customer_id
),
table3 AS (
  SELECT Customer.customer_id, salesperson_id, Total
  FROM Customer
  LEFT JOIN table2 ON Customer.customer_id = table2.customer_id
)
SELECT
  Salesperson.salesperson_id,
  Salesperson.name,
  SUM(COALESCE(table3.Total, 0)) AS total_influence
FROM Salesperson
LEFT JOIN table3 ON Salesperson.salesperson_id = table3.salesperson_id
GROUP BY Salesperson.salesperson_id, Salesperson.name;
```

---

## 19-10-2025

---

### Find the Start and End Number of Continuous Ranges

**Schema**
```sql
Table: Logs
+-------------+------+
| Column Name | Type |
+-------------+------+
| log_id      | int  |
+-------------+------+
log_id is the primary key.
```

Find the start and end of each run of consecutive `log_id` values.

**Example:** `{1,2,3,7,8,10}` → `(1,3), (7,8), (10,10)`

---

### Grand Slam Titles

**Schema**
```sql
Players:       player_id (PK), player_name
Championships: year (PK), Wimbledon, Fr_open, US_open, Au_open
               (each column stores the player_id of that year's champion)
```

Count total grand slam titles per player across all years and tournaments.

**Solution**
```sql
WITH table1 AS (
  SELECT year, Wimbledon AS winner FROM Championships
  UNION ALL
  SELECT year, Fr_open FROM Championships
  UNION ALL
  SELECT year, US_open FROM Championships
  UNION ALL
  SELECT year, Au_open FROM Championships
),
table2 AS (
  SELECT winner, COUNT(year) AS slams_count
  FROM table1
  GROUP BY winner
)
SELECT
  p.player_id,
  p.player_name,
  COALESCE(t.slams_count, 0) AS grand_slams_count
FROM Players p
LEFT JOIN table2 t ON p.player_id = t.winner
ORDER BY grand_slams_count DESC, player_name ASC;
```

---

### Maximum Transaction Each Day

**Schema**
```sql
Table: Transactions
+------------------+------+
| Column Name      | Type |
+------------------+------+
| transaction_id   | int  |
| customer_id      | int  |
| transaction_date | date |
| amount           | int  |
+------------------+------+
transaction_id is the primary key.
```

Return the maximum transaction amount for each day.

**Solution**
```sql
SELECT transaction_date, MAX(amount) AS amount
FROM Transactions
GROUP BY transaction_date;
```

---

## 21-10-2025

---

### Account Balance

**Schema**
```sql
Table: Transactions
+----------------+----------------------------+
| Column Name    | Type                       |
+----------------+----------------------------+
| account_id     | int                        |
| transaction_id | int                        |
| type           | ENUM('Deposit','Withdraw') |
| amount         | int                        |
| day            | date                       |
+----------------+----------------------------+
transaction_id is the primary key.
```

Calculate the current balance for each account. Return sorted by `account_id`.

**Solution**
```sql
SELECT account_id,
  SUM(CASE
    WHEN type = 'Deposit' THEN amount
    ELSE -amount
  END) AS balance
FROM Transactions
GROUP BY account_id
ORDER BY account_id;
```

---

### Tasks Count in the Weekend

Count tasks submitted on weekends vs. weekdays.

**Solution**
```sql
SELECT
  SUM(CASE WHEN DAYNAME(submit_date) IN ('Saturday', 'Sunday') THEN 1 ELSE 0 END) AS weekend_cnt,
  SUM(CASE WHEN DAYNAME(submit_date) NOT IN ('Saturday', 'Sunday') THEN 1 ELSE 0 END) AS working_cnt
FROM Tasks;
```

---

## 22-10-2025

---

### Game Play Analysis III

**Schema**
```sql
Table: Activity
+------------------+------+
| Column Name      | Type |
+------------------+------+
| player_id        | int  |
| device_id        | int  |
| event_date       | date |
| games_played     | int  |
+------------------+------+
Primary key: (player_id, event_date)
```

For each player and date, compute the cumulative games played up to and including that date.

**Solution**
```sql
SELECT
  player_id,
  event_date,
  SUM(games_played) OVER (
    PARTITION BY player_id
    ORDER BY event_date
    ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
  ) AS games_played_so_far
FROM Activity
ORDER BY player_id, event_date;
```

---

### Number of Calls Between Two Persons

**Schema**
```sql
Table: Calls
+-------------+------+
| Column Name | Type |
+-------------+------+
| from_id     | int  |
| to_id       | int  |
| duration    | int  |
+-------------+------+
No primary key (multiple calls between the same pair are possible).
```

Calls are bidirectional. For each unique pair, return total call count and total duration. Each pair should appear once.

**Solution**
```sql
WITH table1 AS (
  SELECT 
    duration,
    LEAST(from_id, to_id) AS person1,
    GREATEST(from_id, to_id) AS person2
  FROM Calls
)
SELECT
  person1 AS person1_id,
  person2 AS person2_id,
  COUNT(duration) AS call_count,
  SUM(duration) AS total_duration
FROM table1
GROUP BY person1, person2
ORDER BY person1_id, person2_id;
```
