# SQL & MySQL Database — Complete Guide

## Table of Contents
1. What is a Database?
2. What is SQL?
3. MySQL Setup
4. Database Basics
5. Creating Tables
6. Data Types
7. CRUD Operations
8. WHERE Clause
9. ORDER BY and LIMIT
10. Aggregate Functions
11. JOINs
12. Connecting Python to MySQL
13. Best Practices

---

## 1. What is a Database?

A **database** is an organized collection of structured data stored electronically.

**Real-world analogy:**
- File cabinet = Database
- Drawer = Table
- Folder = Row
- Paper contents = Columns

**Why we use databases:**
- Store large amounts of data
- Quick retrieval of data
- Data security
- Data integrity

---

## 2. What is SQL?

**SQL** (Structured Query Language) is a language used to communicate with databases.

**Common SQL statements:**
- `CREATE` — Create tables
- `INSERT` — Add data
- `SELECT` — Retrieve data
- `UPDATE` — Modify data
- `DELETE` — Remove data

---

## 3. MySQL Setup (Overview)

**Installation:**
```bash
# macOS
brew install mysql

# Ubuntu/Debian
sudo apt-get install mysql-server

# Windows
Download from https://dev.mysql.com/downloads/mysql/
```

**Start MySQL:**
```bash
mysql -u root -p
```

**Python Package:**
```bash
pip install mysql-connector-python
```

---

## 4. Database Basics

### Create a database
```sql
CREATE DATABASE school;
```

### Use a database
```sql
USE school;
```

### Show all databases
```sql
SHOW DATABASES;
```

### Delete a database
```sql
DROP DATABASE school;
```

---

## 5. Creating Tables

### Basic Syntax
```sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    ...
);
```

### Example: Students table
```sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT,
    email VARCHAR(100) UNIQUE,
    grade CHAR(1)
);
```

---

## 6. Data Types

| Data Type | Size | Purpose |
|-----------|------|---------|
| `INT` | 4 bytes | Whole numbers |
| `FLOAT` | 4 bytes | Decimal numbers |
| `DECIMAL(10,2)` | Precise | Money values |
| `VARCHAR(100)` | Variable | Text up to 100 chars |
| `CHAR(1)` | Fixed | Single character |
| `TEXT` | Large | Long text |
| `DATE` | 3 bytes | YYYY-MM-DD |
| `DATETIME` | 8 bytes | Date and time |
| `BOOLEAN` | 1 byte | True/False |

---

## 7. CRUD Operations

### CREATE — Insert data
```sql
INSERT INTO students (name, age, email, grade)
VALUES ('Alice', 20, 'alice@email.com', 'A');

-- Insert multiple rows
INSERT INTO students (name, age, email, grade)
VALUES
    ('Bob', 21, 'bob@email.com', 'B'),
    ('Charlie', 19, 'charlie@email.com', 'A');
```

---

### READ — Select data
```sql
-- Select all columns
SELECT * FROM students;

-- Select specific columns
SELECT name, email FROM students;

-- Select with alias
SELECT name AS student_name, age AS student_age FROM students;
```

---

### UPDATE — Modify data
```sql
-- Update one column
UPDATE students SET age = 21 WHERE name = 'Alice';

-- Update multiple columns
UPDATE students SET age = 22, grade = 'A' WHERE id = 1;

-- Update all records (be careful!)
UPDATE students SET grade = 'B';
```

---

### DELETE — Remove data
```sql
-- Delete specific record
DELETE FROM students WHERE id = 1;

-- Delete multiple records
DELETE FROM students WHERE grade = 'F';

-- Delete all records (be careful!)
DELETE FROM students;
```

---

## 8. WHERE Clause

### Basic conditions
```sql
-- Equal
SELECT * FROM students WHERE grade = 'A';

-- Not equal
SELECT * FROM students WHERE grade != 'B';

-- Greater than
SELECT * FROM students WHERE age > 20;

-- Less than
SELECT * FROM students WHERE age < 21;

-- Between
SELECT * FROM students WHERE age BETWEEN 19 AND 21;
```

---

### Logical operators
```sql
-- AND
SELECT * FROM students WHERE age > 20 AND grade = 'A';

-- OR
SELECT * FROM students WHERE grade = 'A' OR grade = 'B';

-- NOT
SELECT * FROM students WHERE NOT grade = 'F';

-- IN
SELECT * FROM students WHERE grade IN ('A', 'B');

-- LIKE (pattern matching)
SELECT * FROM students WHERE name LIKE 'A%';  -- Starts with A
SELECT * FROM students WHERE name LIKE '%e%'; -- Contains e
```

---

## 9. ORDER BY and LIMIT

### ORDER BY (sorting)
```sql
-- Ascending (default)
SELECT * FROM students ORDER BY age;
SELECT * FROM students ORDER BY name ASC;

-- Descending
SELECT * FROM students ORDER BY age DESC;

-- Multiple columns
SELECT * FROM students ORDER BY grade ASC, age DESC;
```

---

### LIMIT (limiting results)
```sql
-- Get first 5 records
SELECT * FROM students LIMIT 5;

-- Get 5 records starting from position 0
SELECT * FROM students LIMIT 0, 5;

-- Get 3 records starting from position 5
SELECT * FROM students LIMIT 5, 3;
```

---

### Combined
```sql
-- Top 3 oldest students
SELECT * FROM students ORDER BY age DESC LIMIT 3;

-- First 5 students sorted by name
SELECT * FROM students ORDER BY name LIMIT 5;
```

---

## 10. Aggregate Functions

### COUNT
```sql
-- Count all records
SELECT COUNT(*) FROM students;

-- Count specific column (ignores NULL)
SELECT COUNT(email) FROM students;
```

---

### SUM
```sql
SELECT SUM(age) FROM students;
```

---

### AVG
```sql
SELECT AVG(age) FROM students;
```

---

### MAX / MIN
```sql
SELECT MAX(age) FROM students;
SELECT MIN(age) FROM students;
```

---

### GROUP BY
```sql
-- Count students by grade
SELECT grade, COUNT(*) FROM students GROUP BY grade;

-- Average age by grade
SELECT grade, AVG(age) FROM students GROUP BY grade;

-- Count with condition
SELECT grade, COUNT(*) FROM students GROUP BY grade HAVING COUNT(*) > 2;
```

---

## 11. JOINs

### Setup (two tables)
```sql
-- Teachers table
CREATE TABLE teachers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    subject VARCHAR(100)
);

-- Classes table
CREATE TABLE classes (
    id INT PRIMARY KEY AUTO_INCREMENT,
    class_name VARCHAR(100),
    teacher_id INT,
    FOREIGN KEY (teacher_id) REFERENCES teachers(id)
);
```

---

### INNER JOIN
```sql
-- Get all classes with their teacher names
SELECT classes.class_name, teachers.name
FROM classes
INNER JOIN teachers ON classes.teacher_id = teachers.id;
```

---

### LEFT JOIN
```sql
-- Get all teachers and their classes (even if no classes)
SELECT teachers.name, classes.class_name
FROM teachers
LEFT JOIN classes ON teachers.id = classes.teacher_id;
```

---

### RIGHT JOIN
```sql
-- Get all classes and their teachers (from right table)
SELECT classes.class_name, teachers.name
FROM classes
RIGHT JOIN teachers ON classes.teacher_id = teachers.id;
```

---

## 12. Connecting Python to MySQL

### Installation
```bash
pip install mysql-connector-python
```

---

### Basic Connection
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="school"
)

cursor = connection.cursor()
print("Connected successfully!")

cursor.close()
connection.close()
```

---

### INSERT in Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="school"
)

cursor = connection.cursor()

sql = "INSERT INTO students (name, age, email, grade) VALUES (%s, %s, %s, %s)"
values = ("David", 22, "david@email.com", "B")

cursor.execute(sql, values)
connection.commit()

print(cursor.rowcount, "record inserted")

cursor.close()
connection.close()
```

---

### SELECT in Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="school"
)

cursor = connection.cursor()

cursor.execute("SELECT * FROM students")

for row in cursor.fetchall():
    print(row)

# Or get one row
cursor.execute("SELECT * FROM students WHERE id = 1")
result = cursor.fetchone()
print(result)

cursor.close()
connection.close()
```

---

### UPDATE in Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="school"
)

cursor = connection.cursor()

sql = "UPDATE students SET age = %s WHERE name = %s"
values = (23, "Alice")

cursor.execute(sql, values)
connection.commit()

print(cursor.rowcount, "record updated")

cursor.close()
connection.close()
```

---

### DELETE in Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="school"
)

cursor = connection.cursor()

sql = "DELETE FROM students WHERE id = %s"
value = (1,)

cursor.execute(sql, value)
connection.commit()

print(cursor.rowcount, "record deleted")

cursor.close()
connection.close()
```

---

### Using `with` statement (Best Practice)
```python
import mysql.connector

try:
    connection = mysql.connector.connect(
        host="localhost",
        user="root",
        password="your_password",
        database="school"
    )

    cursor = connection.cursor()
    cursor.execute("SELECT * FROM students")

    for row in cursor.fetchall():
        print(row)

except mysql.connector.Error as err:
    print(f"Error: {err}")

finally:
    if cursor:
        cursor.close()
    if connection:
        connection.close()
```

---

## 13. Best Practices

### ✅ DO:
1. **Use parameterized queries** (prevent SQL injection)
```python
sql = "SELECT * FROM students WHERE name = %s"
cursor.execute(sql, (name,))
```

2. **Close connections properly**
```python
cursor.close()
connection.close()
```

3. **Use meaningful column names**
```sql
CREATE TABLE students (
    student_id INT,
    full_name VARCHAR(100),
    date_of_birth DATE
);
```

4. **Use PRIMARY KEY and FOREIGN KEY**
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

---

### ❌ DON'T:
1. **Don't use string concatenation for queries**
```python
# BAD - SQL injection risk
sql = "SELECT * FROM students WHERE name = '" + name + "'"

# GOOD - Use parameterized queries
sql = "SELECT * FROM students WHERE name = %s"
cursor.execute(sql, (name,))
```

2. **Don't hardcode passwords**
```python
# BAD
password = "root123"

# GOOD - Use environment variables
import os
password = os.getenv('DB_PASSWORD')
```

---

## Summary

| Command | Purpose |
|---------|---------|
| `CREATE DATABASE` | Create database |
| `CREATE TABLE` | Create table |
| `INSERT INTO` | Add data |
| `SELECT` | Retrieve data |
| `UPDATE` | Modify data |
| `DELETE` | Remove data |
| `WHERE` | Filter rows |
| `ORDER BY` | Sort results |
| `LIMIT` | Limit results |
| `JOIN` | Combine tables |
| `GROUP BY` | Group results |

---
