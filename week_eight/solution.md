# Week 8 Project Solution: Student Management System

This is a complete sample implementation of the Student Management System. Use this as a reference for your own project.

---

## File Structure
```
student_management/
├── main.py
├── models.py
├── database.py
├── utils.py
├── config.py
├── requirements.txt
├── README.md
└── schema.sql
```

---

## File 1: config.py
```python
"""Configuration file for database connection."""

DB_CONFIG = {
    'host': 'localhost',
    'user': 'root',
    'password': 'your_password',
    'database': 'student_management'
}
```

---

## File 2: models.py
```python
"""Class definitions for Student Management System."""

class Student:
    """Represents a student in the system."""

    def __init__(self, name, email, enrollment_date=None):
        """Initialize a student."""
        self.id = None
        self.name = name
        self.email = email
        self.enrollment_date = enrollment_date
        self.courses = []

    def __str__(self):
        """String representation of student."""
        return f"Student({self.id}, {self.name}, {self.email})"

    def add_course(self, course):
        """Enroll in a course."""
        if course not in self.courses:
            self.courses.append(course)

    def remove_course(self, course_id):
        """Drop a course."""
        self.courses = [c for c in self.courses if c.id != course_id]

    def get_info(self):
        """Get student information."""
        return {
            'id': self.id,
            'name': self.name,
            'email': self.email,
            'enrollment_date': self.enrollment_date,
            'courses_enrolled': len(self.courses)
        }


class Course:
    """Represents a course."""

    def __init__(self, name, instructor, credits):
        """Initialize a course."""
        self.id = None
        self.name = name
        self.instructor = instructor
        self.credits = credits
        self.students = []

    def __str__(self):
        """String representation of course."""
        return f"Course({self.id}, {self.name}, {self.instructor})"

    def add_student(self, student):
        """Add student to course."""
        if student not in self.students:
            self.students.append(student)

    def remove_student(self, student_id):
        """Remove student from course."""
        self.students = [s for s in self.students if s.id != student_id]

    def get_student_count(self):
        """Get number of enrolled students."""
        return len(self.students)

    def get_info(self):
        """Get course information."""
        return {
            'id': self.id,
            'name': self.name,
            'instructor': self.instructor,
            'credits': self.credits,
            'enrolled_students': self.get_student_count()
        }


class Enrollment:
    """Represents a student's enrollment in a course."""

    def __init__(self, student_id, course_id, grade=None):
        """Initialize an enrollment."""
        self.id = None
        self.student_id = student_id
        self.course_id = course_id
        self.grade = grade
        self.enrollment_date = None

    def assign_grade(self, grade):
        """Assign a grade to this enrollment."""
        valid_grades = ['A', 'B', 'C', 'D', 'F']
        if grade in valid_grades:
            self.grade = grade
            return True
        return False

    def get_grade_points(self):
        """Get point value of grade."""
        grade_points = {'A': 4.0, 'B': 3.0, 'C': 2.0, 'D': 1.0, 'F': 0.0}
        return grade_points.get(self.grade, 0.0)

    def __str__(self):
        """String representation."""
        return f"Enrollment(Student:{self.student_id}, Course:{self.course_id}, Grade:{self.grade})"


class School:
    """Manages students, courses, and enrollments."""

    def __init__(self, db):
        """Initialize school with database connection."""
        self.db = db
        self.students = {}
        self.courses = {}
        self.enrollments = []

    def add_student(self, name, email):
        """Add a new student."""
        if not self._is_valid_email(email):
            return False, "Invalid email format"

        student = Student(name, email)
        student_id = self.db.insert_student(student)
        student.id = student_id
        self.students[student_id] = student
        return True, f"Student added with ID: {student_id}"

    def add_course(self, name, instructor, credits):
        """Add a new course."""
        if credits < 1 or credits > 4:
            return False, "Credits must be between 1 and 4"

        course = Course(name, instructor, credits)
        course_id = self.db.insert_course(course)
        course.id = course_id
        self.courses[course_id] = course
        return True, f"Course added with ID: {course_id}"

    def enroll_student(self, student_id, course_id):
        """Enroll a student in a course."""
        if student_id not in self.students:
            return False, "Student not found"
        if course_id not in self.courses:
            return False, "Course not found"

        enrollment = Enrollment(student_id, course_id)
        enrollment_id = self.db.insert_enrollment(enrollment)
        enrollment.id = enrollment_id
        self.enrollments.append(enrollment)

        self.students[student_id].add_course(self.courses[course_id])
        self.courses[course_id].add_student(self.students[student_id])

        return True, f"Enrollment successful with ID: {enrollment_id}"

    def assign_grade(self, enrollment_id, grade):
        """Assign a grade to an enrollment."""
        enrollment = next((e for e in self.enrollments if e.id == enrollment_id), None)
        if not enrollment:
            return False, "Enrollment not found"

        if enrollment.assign_grade(grade):
            self.db.update_grade(enrollment_id, grade)
            return True, f"Grade {grade} assigned"
        else:
            return False, "Invalid grade"

    def get_student_transcript(self, student_id):
        """Get student's transcript."""
        if student_id not in self.students:
            return None

        student = self.students[student_id]
        transcript = {
            'student_id': student_id,
            'name': student.name,
            'email': student.email,
            'courses': []
        }

        for enrollment in self.enrollments:
            if enrollment.student_id == student_id:
                course = self.courses[enrollment.course_id]
                transcript['courses'].append({
                    'course_name': course.name,
                    'credits': course.credits,
                    'grade': enrollment.grade or 'In Progress'
                })

        return transcript

    def get_student_gpa(self, student_id):
        """Calculate student's GPA."""
        if student_id not in self.students:
            return None

        total_credits = 0
        total_points = 0

        for enrollment in self.enrollments:
            if enrollment.student_id == student_id and enrollment.grade:
                course = self.courses[enrollment.course_id]
                total_credits += course.credits
                total_points += enrollment.get_grade_points() * course.credits

        if total_credits == 0:
            return 0.0

        gpa = total_points / total_credits
        return round(gpa, 2)

    def remove_student(self, student_id):
        """Remove a student."""
        if student_id in self.students:
            self.db.delete_student(student_id)
            del self.students[student_id]
            self.enrollments = [e for e in self.enrollments if e.student_id != student_id]
            return True, "Student removed"
        return False, "Student not found"

    def remove_course(self, course_id):
        """Remove a course."""
        if course_id in self.courses:
            self.db.delete_course(course_id)
            del self.courses[course_id]
            self.enrollments = [e for e in self.enrollments if e.course_id != course_id]
            return True, "Course removed"
        return False, "Course not found"

    @staticmethod
    def _is_valid_email(email):
        """Validate email format."""
        return '@' in email and '.' in email.split('@')[1]
```

---

## File 3: database.py
```python
"""Database operations for Student Management System."""

import mysql.connector
from config import DB_CONFIG


class Database:
    """Handles all database operations."""

    def __init__(self):
        """Initialize database connection."""
        self.connection = None
        self.cursor = None

    def connect(self):
        """Connect to database."""
        try:
            self.connection = mysql.connector.connect(**DB_CONFIG)
            self.cursor = self.connection.cursor()
            print("Database connected successfully")
            return True
        except mysql.connector.Error as err:
            print(f"Error connecting to database: {err}")
            return False

    def disconnect(self):
        """Close database connection."""
        if self.cursor:
            self.cursor.close()
        if self.connection:
            self.connection.close()
        print("Database disconnected")

    def insert_student(self, student):
        """Insert a new student."""
        sql = "INSERT INTO students (name, email, enrollment_date) VALUES (%s, %s, NOW())"
        self.cursor.execute(sql, (student.name, student.email))
        self.connection.commit()
        return self.cursor.lastrowid

    def insert_course(self, course):
        """Insert a new course."""
        sql = "INSERT INTO courses (name, instructor, credits) VALUES (%s, %s, %s)"
        self.cursor.execute(sql, (course.name, course.instructor, course.credits))
        self.connection.commit()
        return self.cursor.lastrowid

    def insert_enrollment(self, enrollment):
        """Insert a new enrollment."""
        sql = "INSERT INTO enrollments (student_id, course_id) VALUES (%s, %s)"
        self.cursor.execute(sql, (enrollment.student_id, enrollment.course_id))
        self.connection.commit()
        return self.cursor.lastrowid

    def update_grade(self, enrollment_id, grade):
        """Update a grade."""
        sql = "UPDATE enrollments SET grade = %s WHERE id = %s"
        self.cursor.execute(sql, (grade, enrollment_id))
        self.connection.commit()

    def get_all_students(self):
        """Get all students."""
        sql = "SELECT * FROM students"
        self.cursor.execute(sql)
        return self.cursor.fetchall()

    def get_all_courses(self):
        """Get all courses."""
        sql = "SELECT * FROM courses"
        self.cursor.execute(sql)
        return self.cursor.fetchall()

    def get_student_enrollments(self, student_id):
        """Get enrollments for a student."""
        sql = "SELECT * FROM enrollments WHERE student_id = %s"
        self.cursor.execute(sql, (student_id,))
        return self.cursor.fetchall()

    def delete_student(self, student_id):
        """Delete a student."""
        self.cursor.execute("DELETE FROM enrollments WHERE student_id = %s", (student_id,))
        self.cursor.execute("DELETE FROM students WHERE id = %s", (student_id,))
        self.connection.commit()

    def delete_course(self, course_id):
        """Delete a course."""
        self.cursor.execute("DELETE FROM enrollments WHERE course_id = %s", (course_id,))
        self.cursor.execute("DELETE FROM courses WHERE id = %s", (course_id,))
        self.connection.commit()
```

---

## File 4: main.py
```python
"""Main entry point for Student Management System."""

from database import Database
from models import School
import json


def main():
    """Main application loop."""
    db = Database()
    if not db.connect():
        return

    school = School(db)

    while True:
        print("\n=== Student Management System ===")
        print("1. Add Student")
        print("2. Add Course")
        print("3. Enroll Student")
        print("4. Assign Grade")
        print("5. View Student Transcript")
        print("6. View Student GPA")
        print("7. View All Students")
        print("8. View All Courses")
        print("9. Exit")

        choice = input("\nChoose an option: ").strip()

        if choice == '1':
            add_student(school)
        elif choice == '2':
            add_course(school)
        elif choice == '3':
            enroll_student(school)
        elif choice == '4':
            assign_grade(school)
        elif choice == '5':
            view_transcript(school)
        elif choice == '6':
            view_gpa(school)
        elif choice == '7':
            view_all_students(school, db)
        elif choice == '8':
            view_all_courses(school, db)
        elif choice == '9':
            print("Goodbye!")
            db.disconnect()
            break
        else:
            print("Invalid choice. Please try again.")


def add_student(school):
    """Add a new student."""
    name = input("Enter student name: ").strip()
    email = input("Enter student email: ").strip()

    success, message = school.add_student(name, email)
    print(message)


def add_course(school):
    """Add a new course."""
    name = input("Enter course name: ").strip()
    instructor = input("Enter instructor name: ").strip()

    try:
        credits = int(input("Enter credits (1-4): ").strip())
        success, message = school.add_course(name, instructor, credits)
        print(message)
    except ValueError:
        print("Invalid credits. Must be a number.")


def enroll_student(school):
    """Enroll a student in a course."""
    try:
        student_id = int(input("Enter student ID: ").strip())
        course_id = int(input("Enter course ID: ").strip())
        success, message = school.enroll_student(student_id, course_id)
        print(message)
    except ValueError:
        print("Invalid ID. Must be a number.")


def assign_grade(school):
    """Assign a grade to an enrollment."""
    try:
        enrollment_id = int(input("Enter enrollment ID: ").strip())
        grade = input("Enter grade (A/B/C/D/F): ").strip().upper()
        success, message = school.assign_grade(enrollment_id, grade)
        print(message)
    except ValueError:
        print("Invalid ID. Must be a number.")


def view_transcript(school):
    """View a student's transcript."""
    try:
        student_id = int(input("Enter student ID: ").strip())
        transcript = school.get_student_transcript(student_id)

        if transcript:
            print("\n=== Student Transcript ===")
            print(f"Student: {transcript['name']} ({transcript['student_id']})")
            print(f"Email: {transcript['email']}")
            print("\nCourses:")
            for course in transcript['courses']:
                print(f"  - {course['course_name']} ({course['credits']} credits): {course['grade']}")
        else:
            print("Student not found.")
    except ValueError:
        print("Invalid ID. Must be a number.")


def view_gpa(school):
    """View a student's GPA."""
    try:
        student_id = int(input("Enter student ID: ").strip())
        gpa = school.get_student_gpa(student_id)

        if gpa is not None:
            print(f"\nStudent {student_id} GPA: {gpa}")
        else:
            print("Student not found.")
    except ValueError:
        print("Invalid ID. Must be a number.")


def view_all_students(school, db):
    """View all students."""
    print("\n=== All Students ===")
    students = db.get_all_students()

    if students:
        print(f"{'ID':<5} {'Name':<20} {'Email':<30}")
        print("-" * 55)
        for student in students:
            print(f"{student[0]:<5} {student[1]:<20} {student[2]:<30}")
    else:
        print("No students found.")


def view_all_courses(school, db):
    """View all courses."""
    print("\n=== All Courses ===")
    courses = db.get_all_courses()

    if courses:
        print(f"{'ID':<5} {'Name':<20} {'Instructor':<20} {'Credits':<7}")
        print("-" * 52)
        for course in courses:
            print(f"{course[0]:<5} {course[1]:<20} {course[2]:<20} {course[3]:<7}")
    else:
        print("No courses found.")


if __name__ == '__main__':
    main()
```

---

## File 5: schema.sql
```sql
CREATE DATABASE IF NOT EXISTS student_management;
USE student_management;

CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    enrollment_date DATETIME,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE courses (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    instructor VARCHAR(100),
    credits INT CHECK (credits BETWEEN 1 AND 4),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE enrollments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT NOT NULL,
    course_id INT NOT NULL,
    grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F')) DEFAULT NULL,
    enrollment_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);
```

---

## File 6: requirements.txt
```
mysql-connector-python==8.0.33
```

---

## File 7: README.md
```markdown
# Student Management System

A comprehensive system for managing students, courses, and enrollments.

## Features
- Add/remove students and courses
- Enroll students in courses
- Assign grades
- View student transcripts
- Calculate GPA
- View all students and courses

## Installation

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Set up database:
```bash
mysql -u root -p < schema.sql
```

3. Configure database credentials in `config.py`

## Usage

Run the application:
```bash
python main.py
```

Follow the menu prompts to manage students and courses.

## Architecture

- `main.py`: Entry point and CLI interface
- `models.py`: Class definitions (Student, Course, Enrollment, School)
- `database.py`: Database operations
- `config.py`: Configuration settings
- `schema.sql`: Database schema

## Classes

### Student
Represents a student with name, email, and enrollment information.

### Course
Represents a course with name, instructor, and credits.

### Enrollment
Represents a student's enrollment in a course with grade information.

### School
Manages students, courses, and enrollments.
```

---

## Testing

```python
# Test basic functionality
def test_student_management():
    db = Database()
    db.connect()

    school = School(db)

    # Test adding student
    success, msg = school.add_student("Alice", "alice@email.com")
    assert success == True

    # Test adding course
    success, msg = school.add_course("Python 101", "Mr. Smith", 3)
    assert success == True

    # Test enrollment
    success, msg = school.enroll_student(1, 1)
    assert success == True

    # Test assigning grade
    success, msg = school.assign_grade(1, 'A')
    assert success == True

    # Test GPA calculation
    gpa = school.get_student_gpa(1)
    assert gpa == 4.0

    db.disconnect()
    print("All tests passed!")

test_student_management()
```

---

## Key Learning Points

1. **OOP Design**: Classes represent real entities (Student, Course)
2. **Inheritance**: Could extend with TeachingAssistant(Student)
3. **Database Integration**: All data persists in MySQL
4. **Error Handling**: Validates input before database operations
5. **Modular Code**: Separated concerns (models, database, UI)
6. **Documentation**: Docstrings for all functions/classes

---
