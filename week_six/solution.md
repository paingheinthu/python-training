# Solutions: SQL & MySQL Database

## Database & Table Creation Exercises

### 1. Create a database
```sql
CREATE DATABASE company;
```

---

### 2. Create employees table
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    salary INT,
    department VARCHAR(100)
);
```

---

### 3. Create students table
```sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    enrollment_date DATE
);
```

---

### 4. Create products table
```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    product_name VARCHAR(100),
    price DECIMAL(10, 2),
    quantity_in_stock INT
);
```

---

### 6. Add column to employees
```sql
ALTER TABLE employees ADD hire_date DATE;
```

---

### 7. Add column with default value
```sql
ALTER TABLE students ADD age INT DEFAULT 18;
```

---

### 10. Create customers and orders table with relationship
```sql
CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    created_at DATETIME
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```

---

## INSERT Exercises

### 11. Insert single employee record
```sql
INSERT INTO employees (name, salary, department)
VALUES ('Alice', 50000, 'Engineering');
```

---

### 12. Insert 3 students
```sql
INSERT INTO students (name, email, phone, enrollment_date)
VALUES
    ('Bob', 'bob@email.com', '555-1111', '2024-02-01'),
    ('Charlie', 'charlie@email.com', '555-2222', '2024-02-05'),
    ('Diana', 'diana@email.com', '555-3333', '2024-02-10');
```

---

### 13. Insert 5 products
```sql
INSERT INTO products (product_name, price, quantity_in_stock)
VALUES
    ('Laptop', 999.99, 5),
    ('Mouse', 29.99, 50),
    ('Keyboard', 79.99, 30),
    ('Monitor', 299.99, 10),
    ('USB Cable', 9.99, 100);
```

---

### 16. Insert employee with hire_date
```sql
INSERT INTO employees (name, salary, department, hire_date)
VALUES ('Eve', 60000, 'Marketing', '2024-01-15');
```

---

## SELECT Exercises

### 21. Select all employees
```sql
SELECT * FROM employees;
```

---

### 22. Select name and salary
```sql
SELECT name, salary FROM employees;
```

---

### 24. Select first 5 employees
```sql
SELECT * FROM employees LIMIT 5;
```

---

### 25. Select products with price > 100
```sql
SELECT * FROM products WHERE price > 100;
```

---

### 29. Select distinct departments
```sql
SELECT DISTINCT department FROM employees;
```

---

### 30. Sort by price highest first
```sql
SELECT * FROM products ORDER BY price DESC;
```

---

## WHERE Clause Exercises

### 31. Employees with salary > 50000
```sql
SELECT * FROM employees WHERE salary > 50000;
```

---

### 33. Employees from Sales OR Marketing
```sql
SELECT * FROM employees
WHERE department = 'Sales' OR department = 'Marketing';
```

---

### 35. Employees with name containing 'son'
```sql
SELECT * FROM employees WHERE name LIKE '%son%';
```

---

### 38. Employees NOT in HR
```sql
SELECT * FROM employees WHERE department != 'HR';
```

---

### 40. Products with price between 50 and 200
```sql
SELECT * FROM products WHERE price BETWEEN 50 AND 200;
```

---

## UPDATE Exercises

### 41. Update Alice's salary
```sql
UPDATE employees SET salary = 55000 WHERE name = 'Alice';
```

---

### 42. Update all Sales department salary
```sql
UPDATE employees SET salary = 45000 WHERE department = 'Sales';
```

---

### 46. Increase all prices by 10%
```sql
UPDATE products SET price = price * 1.10;
```

---

### 50. Add $5000 to Engineering department
```sql
UPDATE employees SET salary = salary + 5000 WHERE department = 'Engineering';
```

---

## DELETE Exercises

### 51. Delete employee with id = 1
```sql
DELETE FROM employees WHERE id = 1;
```

---

### 52. Delete products with zero stock
```sql
DELETE FROM products WHERE quantity_in_stock = 0;
```

---

### 56. Delete all HR employees
```sql
DELETE FROM employees WHERE department = 'HR';
```

---

## Aggregate Functions Exercises

### 61. Count total employees
```sql
SELECT COUNT(*) FROM employees;
```

---

### 63. Average salary
```sql
SELECT AVG(salary) FROM employees;
```

---

### 64. Highest salary
```sql
SELECT MAX(salary) FROM employees;
```

---

### 65. Lowest product price
```sql
SELECT MIN(price) FROM products;
```

---

### 70. Count employees by department
```sql
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

---

## ORDER BY & LIMIT Exercises

### 71. Employees sorted by salary (highest first)
```sql
SELECT * FROM employees ORDER BY salary DESC;
```

---

### 72. Students sorted by name
```sql
SELECT * FROM students ORDER BY name ASC;
```

---

### 73. Top 3 highest paid employees
```sql
SELECT * FROM employees ORDER BY salary DESC LIMIT 3;
```

---

### 74. Top 5 cheapest products
```sql
SELECT * FROM products ORDER BY price ASC LIMIT 5;
```

---

## JOIN Exercises

### 82. Employee and department INNER JOIN
```sql
-- First create departments table
CREATE TABLE departments (
    department_id INT PRIMARY KEY AUTO_INCREMENT,
    department_name VARCHAR(100)
);

-- Add department_id to employees
ALTER TABLE employees ADD department_id INT;
ALTER TABLE employees ADD FOREIGN KEY (department_id) REFERENCES departments(department_id);

-- INNER JOIN query
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

---

### 83. All departments with their employees (LEFT JOIN)
```sql
SELECT departments.department_name, employees.name
FROM departments
LEFT JOIN employees ON employees.department_id = departments.department_id;
```

---

## Python-MySQL Connection Exercises

### 91. Connect and display all employees
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()
cursor.execute("SELECT * FROM employees")

print("All Employees:")
for row in cursor.fetchall():
    print(row)

cursor.close()
connection.close()
```

---

### 92. Insert new employee via Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

sql = "INSERT INTO employees (name, salary, department) VALUES (%s, %s, %s)"
values = ("Frank", 58000, "Sales")

cursor.execute(sql, values)
connection.commit()

print(f"{cursor.rowcount} employee inserted")

cursor.close()
connection.close()
```

---

### 93. Update employee salary via Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

sql = "UPDATE employees SET salary = %s WHERE name = %s"
values = (65000, "Alice")

cursor.execute(sql, values)
connection.commit()

print(f"{cursor.rowcount} record updated")

cursor.close()
connection.close()
```

---

### 94. Delete student record via Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

sql = "DELETE FROM students WHERE id = %s"
value = (1,)

cursor.execute(sql, value)
connection.commit()

print(f"{cursor.rowcount} student deleted")

cursor.close()
connection.close()
```

---

### 95. Select and display all students
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()
cursor.execute("SELECT id, name, email, phone FROM students")

print("All Students:")
print(f"{'ID':<5} {'Name':<20} {'Email':<30} {'Phone':<15}")
print("-" * 70)

for row in cursor.fetchall():
    print(f"{row[0]:<5} {row[1]:<20} {row[2]:<30} {row[3]:<15}")

cursor.close()
connection.close()
```

---

### 96. Count total employees
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()
cursor.execute("SELECT COUNT(*) FROM employees")

total = cursor.fetchone()[0]
print(f"Total employees: {total}")

cursor.close()
connection.close()
```

---

### 97. Find highest and lowest salary
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

cursor.execute("SELECT MAX(salary) FROM employees")
highest = cursor.fetchone()[0]

cursor.execute("SELECT MIN(salary) FROM employees")
lowest = cursor.fetchone()[0]

print(f"Highest salary: ${highest}")
print(f"Lowest salary: ${lowest}")

cursor.close()
connection.close()
```

---

### 98. Insert multiple products via Python
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

sql = "INSERT INTO products (product_name, price, quantity_in_stock) VALUES (%s, %s, %s)"
values = [
    ("Headphones", 149.99, 20),
    ("Webcam", 79.99, 15),
    ("Desk Lamp", 39.99, 40)
]

cursor.executemany(sql, values)
connection.commit()

print(f"{cursor.rowcount} products inserted")

cursor.close()
connection.close()
```

---

### 99. Update all product prices (add 10%)
```python
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="company"
)

cursor = connection.cursor()

sql = "UPDATE products SET price = price * 1.10"
cursor.execute(sql)
connection.commit()

print(f"{cursor.rowcount} products price updated")

cursor.close()
connection.close()
```

---

### 100. Function to retrieve employee data
```python
import mysql.connector

def get_employees():
    try:
        connection = mysql.connector.connect(
            host="localhost",
            user="root",
            password="your_password",
            database="company"
        )

        cursor = connection.cursor()
        cursor.execute("SELECT * FROM employees")
        employees = cursor.fetchall()

        return employees

    except mysql.connector.Error as err:
        print(f"Error: {err}")
        return []

    finally:
        cursor.close()
        connection.close()

# Usage
employees = get_employees()
for emp in employees:
    print(emp)
```

---

## Project Solutions

### Project 1: Student Management Database
```python
import mysql.connector

class StudentManagementSystem:
    def __init__(self):
        self.connection = mysql.connector.connect(
            host="localhost",
            user="root",
            password="your_password",
            database="school"
        )
        self.cursor = self.connection.cursor()

    def create_tables(self):
        # Create students table
        self.cursor.execute("""
            CREATE TABLE IF NOT EXISTS students (
                student_id INT PRIMARY KEY AUTO_INCREMENT,
                name VARCHAR(100),
                email VARCHAR(100)
            )
        """)

        # Create courses table
        self.cursor.execute("""
            CREATE TABLE IF NOT EXISTS courses (
                course_id INT PRIMARY KEY AUTO_INCREMENT,
                course_name VARCHAR(100),
                instructor VARCHAR(100)
            )
        """)

        # Create enrollments table
        self.cursor.execute("""
            CREATE TABLE IF NOT EXISTS enrollments (
                enrollment_id INT PRIMARY KEY AUTO_INCREMENT,
                student_id INT,
                course_id INT,
                grade VARCHAR(2),
                FOREIGN KEY (student_id) REFERENCES students(student_id),
                FOREIGN KEY (course_id) REFERENCES courses(course_id)
            )
        """)

        self.connection.commit()

    def add_student(self, name, email):
        sql = "INSERT INTO students (name, email) VALUES (%s, %s)"
        self.cursor.execute(sql, (name, email))
        self.connection.commit()

    def add_course(self, course_name, instructor):
        sql = "INSERT INTO courses (course_name, instructor) VALUES (%s, %s)"
        self.cursor.execute(sql, (course_name, instructor))
        self.connection.commit()

    def enroll_student(self, student_id, course_id):
        sql = "INSERT INTO enrollments (student_id, course_id) VALUES (%s, %s)"
        self.cursor.execute(sql, (student_id, course_id))
        self.connection.commit()

    def get_student_courses(self, student_id):
        sql = """
            SELECT courses.course_name, enrollments.grade
            FROM courses
            INNER JOIN enrollments ON courses.course_id = enrollments.course_id
            WHERE enrollments.student_id = %s
        """
        self.cursor.execute(sql, (student_id,))
        return self.cursor.fetchall()

    def close(self):
        self.cursor.close()
        self.connection.close()

# Usage
sms = StudentManagementSystem()
sms.create_tables()
sms.add_student("Alice", "alice@email.com")
sms.add_student("Bob", "bob@email.com")
sms.add_course("Python 101", "Mr. Smith")
sms.add_course("Database", "Ms. Jones")
sms.enroll_student(1, 1)
sms.enroll_student(1, 2)

courses = sms.get_student_courses(1)
print(f"Courses for student 1: {courses}")

sms.close()
```

---
