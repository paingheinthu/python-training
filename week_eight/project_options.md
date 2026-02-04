# Week 8 Project Options

Choose ONE of the following projects to implement. Each project should integrate:
- Classes & OOP
- File I/O or Database
- Functions & Modules
- Error Handling
- Data Validation

---

## Project 1: Student Management System ⭐⭐⭐

### Overview
A system to manage students, courses, enrollments, and grades at a school.

### Features
1. **Student Management**
   - Add/remove students
   - View student details
   - Update student information

2. **Course Management**
   - Add/remove courses
   - View enrolled students
   - Manage course instructors

3. **Enrollment Management**
   - Enroll students in courses
   - Drop courses
   - View enrolled courses per student

4. **Grade Management**
   - Assign grades to students
   - Calculate GPA
   - Generate transcripts
   - Generate grade reports

5. **Data Persistence**
   - Store all data in MySQL database
   - Save/load student transcripts to files

### Classes Needed
```python
class Student:
    - name, email, enrollment_date
    - Methods: enroll_course(), get_gpa(), generate_transcript()

class Course:
    - name, instructor, credits, max_students
    - Methods: add_student(), remove_student(), is_full()

class Enrollment:
    - student_id, course_id, grade, date_enrolled
    - Methods: assign_grade(), calculate_contribution_to_gpa()

class School:
    - students[], courses[], enrollments[]
    - Methods: add_student(), add_course(), enroll(), generate_reports()
```

### Database Schema
```sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    enrollment_date DATE,
    created_at TIMESTAMP
);

CREATE TABLE courses (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    instructor VARCHAR(100),
    credits INT,
    max_students INT
);

CREATE TABLE enrollments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT,
    course_id INT,
    grade CHAR(1),
    date_enrolled DATE,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);
```

### Complexity: Medium
### Estimated Time: 4-5 days

---

## Project 2: Personal Finance Tracker ⭐⭐⭐

### Overview
Track income, expenses, budgets, and financial goals.

### Features
1. **Income Management**
   - Add income sources
   - Track income by category
   - View income history

2. **Expense Management**
   - Add expenses with categories
   - View expenses by category
   - Monthly expense breakdown
   - Expense trends

3. **Budget Management**
   - Set budgets per category
   - Track spending vs. budget
   - Alert when budget exceeded

4. **Goal Tracking**
   - Set financial goals
   - Track progress
   - Estimate time to reach goal

5. **Reporting**
   - Monthly financial summary
   - Spending patterns
   - Income vs. expenses comparison
   - Export reports to CSV/PDF

### Classes Needed
```python
class Transaction:
    - amount, category, date, description
    - Methods: get_info()

class Income(Transaction):
    - source
    - Methods: to_database()

class Expense(Transaction):
    - payment_method
    - Methods: to_database()

class Budget:
    - category, limit, current_spending, start_date
    - Methods: add_expense(), is_exceeded(), get_remaining()

class FinanceTracker:
    - incomes[], expenses[], budgets[]
    - Methods: add_income(), add_expense(), generate_report()
```

### Database Schema
```sql
CREATE TABLE transactions (
    id INT PRIMARY KEY AUTO_INCREMENT,
    type ENUM('income', 'expense'),
    amount DECIMAL(10, 2),
    category VARCHAR(50),
    description VARCHAR(200),
    date DATE
);

CREATE TABLE budgets (
    id INT PRIMARY KEY AUTO_INCREMENT,
    category VARCHAR(50),
    limit_amount DECIMAL(10, 2),
    month INT,
    year INT
);

CREATE TABLE goals (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    target_amount DECIMAL(10, 2),
    current_amount DECIMAL(10, 2),
    deadline DATE
);
```

### Complexity: Medium
### Estimated Time: 4-5 days

---

## Project 3: E-commerce Store System ⭐⭐⭐⭐

### Overview
An online store with products, shopping cart, orders, and inventory management.

### Features
1. **Product Management**
   - Add/remove products
   - Update inventory
   - Search products by category
   - View product details

2. **Customer Management**
   - Register customers
   - Manage customer profiles
   - View order history

3. **Shopping Cart**
   - Add items to cart
   - Remove items
   - Update quantities
   - Calculate totals

4. **Order Management**
   - Create orders from cart
   - Track order status
   - Generate invoices
   - Calculate shipping

5. **Inventory Management**
   - Track stock levels
   - Alert low stock items
   - Manage restocks

### Classes Needed
```python
class Product:
    - id, name, price, category, stock
    - Methods: update_stock(), get_info()

class Customer:
    - id, name, email, address, phone
    - Methods: place_order(), get_order_history()

class CartItem:
    - product_id, quantity, price
    - Methods: calculate_subtotal()

class ShoppingCart:
    - items[], customer_id
    - Methods: add_item(), remove_item(), calculate_total()

class Order:
    - order_id, customer_id, items[], order_date, status
    - Methods: generate_invoice(), update_status()

class Store:
    - products[], customers[], orders[]
    - Methods: create_order(), process_payment(), generate_report()
```

### Database Schema
```sql
CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    price DECIMAL(10, 2),
    category VARCHAR(50),
    stock INT
);

CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    address VARCHAR(200),
    phone VARCHAR(20)
);

CREATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATETIME,
    status VARCHAR(20),
    total DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

CREATE TABLE order_items (
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

### Complexity: Hard
### Estimated Time: 5-6 days

---

## Project 4: Library Management System ⭐⭐⭐

### Overview
Manage books, members, loans, and library operations.

### Features
1. **Book Management**
   - Add/remove books
   - Track book copies
   - View book details
   - Search by author/title

2. **Member Management**
   - Register members
   - View member details
   - Track membership status
   - Calculate fines

3. **Loan Management**
   - Check out books
   - Return books
   - Track due dates
   - Renew loans

4. **Fine Management**
   - Calculate overdue fines
   - Track member fines
   - Generate fine reports

5. **Reporting**
   - Most borrowed books
   - Member borrowing history
   - Overdue books report
   - Revenue from fines

### Classes Needed
```python
class Book:
    - isbn, title, author, genre, copies_available
    - Methods: get_info(), is_available()

class Member:
    - id, name, email, phone, membership_date
    - Methods: borrow_book(), return_book(), get_fine()

class Loan:
    - loan_id, member_id, book_id, checkout_date, due_date
    - Methods: calculate_fine(), is_overdue()

class Library:
    - books[], members[], loans[]
    - Methods: checkout_book(), return_book(), calculate_fines()
```

### Database Schema
```sql
CREATE TABLE books (
    id INT PRIMARY KEY AUTO_INCREMENT,
    isbn VARCHAR(20),
    title VARCHAR(100),
    author VARCHAR(100),
    genre VARCHAR(50),
    total_copies INT,
    available_copies INT
);

CREATE TABLE members (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    membership_date DATE
);

CREATE TABLE loans (
    id INT PRIMARY KEY AUTO_INCREMENT,
    member_id INT,
    book_id INT,
    checkout_date DATE,
    due_date DATE,
    return_date DATE,
    FOREIGN KEY (member_id) REFERENCES members(id),
    FOREIGN KEY (book_id) REFERENCES books(id)
);
```

### Complexity: Medium
### Estimated Time: 4-5 days

---

## Project 5: Restaurant Management System ⭐⭐⭐⭐

### Overview
Manage restaurant menu, orders, tables, and billing.

### Features
1. **Menu Management**
   - Add/remove dishes
   - Categorize dishes
   - Manage pricing
   - Track ingredients

2. **Table Management**
   - Manage table reservations
   - Track table status (available/occupied)
   - Manage table capacity

3. **Order Management**
   - Create orders for tables
   - Track order status
   - Modify orders
   - Complete orders

4. **Billing**
   - Generate bills
   - Apply discounts
   - Calculate taxes
   - Process payments

5. **Inventory**
   - Track ingredient stock
   - Alert low stock items
   - Update ingredient usage

### Classes Needed
```python
class Dish:
    - name, category, price, ingredients, availability
    - Methods: get_info(), is_available()

class Table:
    - table_number, capacity, status
    - Methods: occupy(), free(), get_occupancy()

class OrderItem:
    - dish_id, quantity, special_requests
    - Methods: calculate_price()

class Order:
    - order_id, table_id, items[], order_time, status
    - Methods: add_item(), remove_item(), calculate_total()

class Bill:
    - bill_id, order_id, subtotal, tax, discount, total
    - Methods: apply_discount(), calculate_tax()

class Restaurant:
    - dishes[], tables[], orders[], bills[]
    - Methods: create_order(), generate_bill(), close_order()
```

### Complexity: Hard
### Estimated Time: 5-6 days

---

## Project 6: Hospital Management System ⭐⭐⭐⭐

### Overview
Manage patients, doctors, appointments, and medical records.

### Features
1. **Patient Management**
   - Register patients
   - Maintain medical history
   - Track vital signs
   - View patient records

2. **Doctor Management**
   - Manage doctor profiles
   - Track specialties
   - Manage availability

3. **Appointment Management**
   - Schedule appointments
   - Cancel appointments
   - Reschedule appointments
   - View schedule

4. **Medical Records**
   - Store medical history
   - Track prescriptions
   - Track diagnoses
   - Generate medical reports

5. **Billing**
   - Generate invoices
   - Track payments
   - Manage insurance

### Database Schema
```sql
CREATE TABLE patients (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    dob DATE,
    phone VARCHAR(20),
    address VARCHAR(200)
);

CREATE TABLE doctors (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    specialty VARCHAR(50),
    phone VARCHAR(20),
    available_hours VARCHAR(100)
);

CREATE TABLE appointments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    patient_id INT,
    doctor_id INT,
    appointment_date DATETIME,
    status VARCHAR(20),
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);

CREATE TABLE medical_records (
    id INT PRIMARY KEY AUTO_INCREMENT,
    patient_id INT,
    diagnosis VARCHAR(200),
    prescription VARCHAR(300),
    visit_date DATE,
    FOREIGN KEY (patient_id) REFERENCES patients(id)
);
```

### Complexity: Hard
### Estimated Time: 5-6 days

---

## Project 7: Chat Application ⭐⭐⭐⭐⭐

### Overview
A simple messaging application with user accounts and chat history.

### Features
1. **User Management**
   - Register users
   - User login
   - User profiles

2. **Conversations**
   - Create conversations
   - Add participants
   - View conversation list

3. **Messaging**
   - Send messages
   - Receive messages
   - Message history
   - Search messages

4. **Notifications**
   - Unread message count
   - Message timestamp

5. **Data Persistence**
   - Save all conversations
   - Save all messages
   - Load history on login

### Complexity: Very Hard
### Estimated Time: 6-7 days

---

## Recommendation

**For beginners:** Start with Project 1 (Student Management) or Project 4 (Library)

**For intermediate:** Try Project 2 (Finance Tracker) or Project 3 (E-commerce)

**For advanced:** Challenge yourself with Project 5 (Restaurant), 6 (Hospital), or 7 (Chat)

---

## Custom Project

You can also propose your own project! Requirements:
- Must use classes
- Must include database
- Must implement CRUD operations
- Must handle errors
- Must validate input
- Should be completed in 5 days

Submit your project idea for approval before starting.

---
