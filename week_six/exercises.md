# Exercises: SQL & MySQL Database

## Database & Table Creation Exercises

1. Create a database called `company`.

2. Create a `employees` table with columns: `id` (INT, PRIMARY KEY), `name` (VARCHAR), `salary` (INT), `department` (VARCHAR).

3. Create a `students` table with columns: `id`, `name`, `email`, `phone`, `enrollment_date`.

4. Create a `products` table with columns: `product_id`, `product_name`, `price`, `quantity_in_stock`.

5. Create a `courses` table with columns: `course_id`, `course_name`, `instructor`, `credits`.

6. Modify the `employees` table to add a column `hire_date` (DATE).

7. Modify the `students` table to add a column `age` (INT) with default value 18.

8. Drop the `courses` table (delete the entire table).

9. Create a `customers` table with `id`, `name`, `email`, `phone`, `created_at` (DATETIME).

10. Create a `orders` table with `order_id`, `customer_id` (FOREIGN KEY), `order_date`, `total_amount`.

---

## INSERT Exercises

11. Insert a record into `employees`: name "Alice", salary 50000, department "Engineering".

12. Insert 3 students into the `students` table with different names and emails.

13. Insert 5 products into the `products` table.

14. Insert multiple customers into the `customers` table in a single INSERT statement.

15. Insert an order into the `orders` table linking to a customer.

16. Insert a new employee with hire_date "2024-01-15".

17. Insert a student with name "Bob", email "bob@email.com", phone "555-1234", enrollment_date "2024-02-01".

18. Insert 3 employees with different departments.

19. Insert products with varying prices and stock quantities.

20. Insert an employee with all columns filled.

---

## SELECT Exercises

21. Select all records from the `employees` table.

22. Select only `name` and `salary` from employees.

23. Select all students with their names and emails.

24. Select the first 5 employees.

25. Select products where price is greater than 100.

26. Select all customers.

27. Select employees from the "Engineering" department.

28. Select students where name starts with 'A'.

29. Select all distinct departments from employees.

30. Select products ordered by price (highest first).

---

## WHERE Clause Exercises

31. Select employees with salary > 50000.

32. Select students with age >= 20.

33. Select employees from department "Sales" OR "Marketing".

34. Select products with quantity_in_stock < 10.

35. Select employees where name contains "son".

36. Select customers enrolled between "2024-01-01" and "2024-06-30".

37. Select orders with total_amount > 500.

38. Select employees NOT in "HR" department.

39. Select students with email containing "gmail".

40. Select products with price BETWEEN 50 and 200.

---

## UPDATE Exercises

41. Update employee "Alice" salary to 55000.

42. Update all employees in "Sales" to salary 45000.

43. Update student age to 21 where name is "Bob".

44. Update product price to 99.99 where product_id = 1.

45. Update customer phone number where name is "John".

46. Update all products to increase price by 10%.

47. Update employee hire_date to "2024-03-01" where id = 1.

48. Update student enrollment_date.

49. Update order total_amount where order_id = 5.

50. Update all employees in department "Engineering" to add $5000 to salary.

---

## DELETE Exercises

51. Delete the employee with id = 1.

52. Delete all products with quantity_in_stock = 0.

53. Delete all customers created before "2024-01-01".

54. Delete student where email = "old@email.com".

55. Delete orders with total_amount < 10.

56. Delete all employees from "HR" department.

57. Delete all employees (all records).

58. Delete a customer by name.

59. Delete products with price < 5.

60. Delete an order by order_id.

---

## Aggregate Functions Exercises

61. Count the total number of employees.

62. Count students with age > 20.

63. Find the average salary of employees.

64. Find the highest salary among employees.

65. Find the lowest price among products.

66. Sum the total quantity of all products.

67. Count distinct departments.

68. Find average price of products.

69. Count total orders.

70. Count employees by department (GROUP BY).

---

## ORDER BY & LIMIT Exercises

71. Select all employees sorted by salary (highest first).

72. Select students sorted by name (A-Z).

73. Select top 3 highest paid employees.

74. Select top 5 cheapest products.

75. Select employees sorted by hire_date (newest first).

76. Select products sorted by quantity (lowest first).

77. Select customers sorted by name and then by phone.

78. Select the 10th to 20th employees.

79. Select top 5 orders by total_amount.

80. Select students sorted by age, then by name.

---

## JOIN Exercises

81. Create an `employees` and `departments` table with a relationship.

82. Select employee name and their department name using INNER JOIN.

83. Select all departments and their employees using LEFT JOIN.

84. Select all employees and the projects they work on.

85. Find employees who don't have a department assigned (NULL values).

86. Create `students` and `courses` tables with many-to-many relationship.

87. Select students and their enrolled courses using JOIN.

88. Select courses and the students enrolled using JOIN.

89. Join employees with their manager's information.

90. Create orders and items relationship, then join them.

---

## Python-MySQL Connection Exercises

91. Connect to a MySQL database and display all employees.

92. Insert a new employee via Python.

93. Update an employee's salary via Python using parameterized query.

94. Delete a student record via Python.

95. Select and display all students from Python.

96. Count total employees via Python and print the result.

97. Find highest and lowest salary via Python.

98. Insert multiple products via Python.

99. Update all product prices (add 10%) via Python.

100. Create a function that connects to MySQL and retrieves employee data.

---

## Project-Based Exercises

### Project 1: Student Management Database
- Create tables: students, courses, enrollments
- Insert sample data
- Query: Students in a course, Average grade per student
- Update: Grades, Drop students

### Project 2: E-commerce Database
- Create tables: products, customers, orders, order_items
- Insert sample data
- Query: Total spent per customer, Most popular product
- Update: Inventory, Order status

### Project 3: Company HR System
- Create tables: employees, departments, salaries, attendance
- Insert sample data
- Query: Payroll, Department statistics
- Update: Salary increases, Job transfers

### Project 4: Library Management System
- Create tables: books, members, loans, returns
- Insert sample data
- Query: Available books, Borrowed by member
- Update: Loan status, Return dates

### Project 5: Social Media Database
- Create tables: users, posts, comments, likes
- Insert sample data
- Query: User posts, Most liked posts, Comments per post
- Update: Post content, Delete comments

---
