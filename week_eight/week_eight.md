# Week 8: Mini Project — Capstone

## Overview

This week you'll apply everything you've learned in weeks 1-7 to build a complete project. The mini project should integrate multiple concepts:

- **Programming Fundamentals** (variables, conditions, loops)
- **Data Structures** (lists, dictionaries)
- **Functions & Modules** (code organization, reusability)
- **Object-Oriented Programming** (classes, inheritance, encapsulation)
- **File I/O** (reading/writing data)
- **Databases** (storing and retrieving data)
- **Debugging** (testing and error handling)

---

## Project Requirements

### Functional Requirements
Your project must:
1. Use at least 3 classes/objects
2. Implement CRUD operations (Create, Read, Update, Delete)
3. Store data persistently (database or file)
4. Handle user input with validation
5. Include error handling
6. Use at least one inheritance relationship
7. Implement 3+ functions that are reusable

---

### Code Quality Requirements
Your project must:
1. Follow Python naming conventions (snake_case, PascalCase)
2. Include docstrings for functions and classes
3. Have meaningful variable names
4. Be organized in logical sections
5. Include comments where logic is complex
6. Handle edge cases

---

### Testing Requirements
Your project should:
1. Include test cases for key functions
2. Demonstrate data validation
3. Handle errors gracefully
4. Work with sample data

---

## Grading Rubric

| Criteria | Points |
|----------|--------|
| **Functionality** | 30 |
| - All features work as described | |
| - CRUD operations complete | |
| - Data persists correctly | |
| **Code Quality** | 25 |
| - Classes properly designed | |
| - Functions are reusable | |
| - Good naming conventions | |
| - Proper error handling | |
| **OOP Design** | 20 |
| - Appropriate use of classes | |
| - Good inheritance design | |
| - Encapsulation practiced | |
| **Data Management** | 15 |
| - Database/file integration | |
| - Data validation | |
| - Transaction handling | |
| **Documentation** | 10 |
| - Code comments | |
| - Function docstrings | |
| - README with usage instructions | |

**Total: 100 points**

---

## Project Selection Process

### Step 1: Choose Project Type
Decide which project interests you most:
- Student Management System
- E-commerce Platform
- Personal Finance Tracker
- Library Management
- Chat Application
- Game with Database
- Or propose your own!

---

### Step 2: Plan Your Project
Create a plan that includes:
1. **Data model** — What data will you store?
2. **Classes** — What classes do you need?
3. **Database schema** — How will you structure the database?
4. **Features** — What are the main features?
5. **User interface** — How will users interact with your app?

---

### Step 3: Implement
1. Start with database/file setup
2. Create core classes
3. Implement CRUD operations
4. Add input validation
5. Add error handling
6. Test thoroughly

---

### Step 4: Test
1. Test all CRUD operations
2. Test with edge cases (empty inputs, invalid data)
3. Test error handling
4. Test data persistence
5. Test with multiple users/scenarios

---

### Step 5: Document
1. Add docstrings to all functions/classes
2. Add comments for complex logic
3. Create README with instructions
4. Document database schema
5. Show sample usage

---

## Project Structure

```
my_project/
├── main.py              # Entry point
├── config.py            # Configuration (database settings)
├── models.py            # Class definitions
├── database.py          # Database operations
├── utils.py             # Helper functions
├── requirements.txt     # Dependencies (mysql-connector-python, etc.)
├── README.md            # Project documentation
├── tests.py             # Test cases (optional but recommended)
└── data/                # Sample data files
    ├── sample_data.csv
    └── database_schema.sql
```

---

## Example: Student Management System

### Data Model
```
Students:
- id (Primary Key)
- name
- email
- enrollment_date
- gpa

Courses:
- id (Primary Key)
- name
- instructor
- credits

Enrollments:
- id (Primary Key)
- student_id (Foreign Key)
- course_id (Foreign Key)
- grade
```

---

### Classes
```python
class Student:
    def __init__(self, name, email)
    def enroll_in_course(course)
    def get_gpa()
    def update_email(new_email)

class Course:
    def __init__(self, name, instructor, credits)
    def get_enrolled_students()

class School:
    def __init__(self)
    def add_student(student)
    def add_course(course)
    def generate_transcript(student)
```

---

### Features
1. Add/Remove students
2. Add/Remove courses
3. Enroll students in courses
4. View student transcripts
5. Calculate GPA
6. Generate reports

---

## Tips for Success

### DO:
1. **Start simple** — Implement basic features first
2. **Test early** — Test as you code
3. **Commit frequently** — Save progress
4. **Ask questions** — Use AI to help, but understand the code
5. **Document well** — Good documentation is crucial
6. **Handle errors** — Think about what could go wrong
7. **Validate input** — Don't trust user input

### DON'T:
1. **Don't over-engineer** — Keep it simple
2. **Don't skip testing** — Test everything
3. **Don't hardcode values** — Use variables/config
4. **Don't ignore edge cases** — Handle empty/invalid data
5. **Don't copy-paste code** — Write reusable functions
6. **Don't skip documentation** — Future you will thank you

---

## Example Timeline

### Day 1: Planning & Setup
- [ ] Plan project structure
- [ ] Set up database
- [ ] Create basic file structure

### Day 2: Core Classes
- [ ] Create main classes
- [ ] Implement basic methods
- [ ] Test class creation

### Day 3: CRUD Operations
- [ ] Implement Create operations
- [ ] Implement Read operations
- [ ] Implement Update operations
- [ ] Implement Delete operations

### Day 4: Features
- [ ] Add validation
- [ ] Add error handling
- [ ] Implement special features

### Day 5: Testing & Polish
- [ ] Write test cases
- [ ] Test edge cases
- [ ] Add documentation
- [ ] Clean up code

---

## Common Pitfalls & Solutions

### Pitfall 1: Database Connection Issues
**Problem:** Can't connect to MySQL
**Solution:**
- Verify MySQL is running
- Check credentials
- Verify database exists
- Test connection with simple query

---

### Pitfall 2: Data Not Persisting
**Problem:** Data is lost after restart
**Solution:**
- Check if you're committing database transactions
- Verify file write operations complete
- Check file permissions

---

### Pitfall 3: Poor Class Design
**Problem:** Classes are too large or don't make sense
**Solution:**
- One class = one responsibility
- Use inheritance for shared behavior
- Keep methods focused

---

### Pitfall 4: No Error Handling
**Problem:** Program crashes on invalid input
**Solution:**
- Use try-except blocks
- Validate all user input
- Provide meaningful error messages

---

### Pitfall 5: Untested Code
**Problem:** Features don't work as expected
**Solution:**
- Write test cases
- Test edge cases
- Test with real data

---

## Submission Checklist

Before submitting, verify:
- [ ] All features implemented
- [ ] Code runs without errors
- [ ] All classes properly defined
- [ ] Database/file operations work
- [ ] Input validation present
- [ ] Error handling included
- [ ] Code is well-commented
- [ ] Functions have docstrings
- [ ] README.md is complete
- [ ] Sample data/setup included
- [ ] No hardcoded values
- [ ] Proper file structure

---

## Project Ideas

1. **Student Management System** — Manage students, courses, grades
2. **E-commerce Store** — Products, orders, customers, inventory
3. **Personal Finance Tracker** — Expenses, income, budgets, reports
4. **Library Management** — Books, members, loans, returns
5. **Hospital Management** — Patients, doctors, appointments, medical records
6. **Restaurant System** — Dishes, orders, customers, billing
7. **Chat Application** — Users, messages, conversations, file storage
8. **Project Management Tool** — Projects, tasks, team members, deadlines
9. **Weather App** — Save locations, store weather history, provide reports
10. **Real Estate System** — Properties, agents, clients, transactions

---

## Resources

- Python Documentation: https://docs.python.org/3/
- MySQL Documentation: https://dev.mysql.com/doc/
- AI Assistant (Claude/ChatGPT) for help with:
  - Code generation
  - Debugging
  - Learning concepts
  - Architecture suggestions

---

## Success Criteria

Your project is successful if:
1. ✅ All requested features work correctly
2. ✅ Code is clean and well-organized
3. ✅ Database/file operations work properly
4. ✅ Error handling is comprehensive
5. ✅ Code is properly documented
6. ✅ You can explain your design decisions
7. ✅ You learned something new

---
