# Solutions: Using AI to Debug & Code Generate

## Prompt Writing Examples

### 1. Good Prompt for Maximum in List
```
Write a Python function called 'find_max' that:
- Takes a list of numbers as input
- Returns the maximum number
- Works with both integers and floats
- Handles edge cases (empty list)
Include error handling and test cases.
```

---

### 2. Detailed Prompt for Todo Class
```
Create a Python class called 'TodoList' with these methods:
- __init__() to initialize empty task list
- add(task: str) to add a task
- remove(task: str) to remove a task
- list_all() to return all tasks
- mark_complete(task: str) to mark task as done

Include docstrings and error handling for missing tasks.
Provide test cases.
```

---

### 3. Prompt for JSON Reading
```
Write a Python function that:
- Reads a JSON file from a given path
- Pretty-prints the JSON with indentation
- Handles FileNotFoundError if file doesn't exist
- Handles json.JSONDecodeError if JSON is invalid

Include error messages that explain what went wrong.
```

---

## Generated Code Examples

### 11. Remove Duplicates (from AI)
```python
def remove_duplicates(items):
    """Remove duplicates while preserving order."""
    seen = set()
    result = []
    for item in items:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# Test cases
print(remove_duplicates([1, 2, 2, 3, 1, 4]))  # [1, 2, 3, 4]
print(remove_duplicates(['a', 'b', 'a', 'c']))  # ['a', 'b', 'c']
print(remove_duplicates([]))  # []
```

---

### 12. Person Class (from AI)
```python
class Person:
    def __init__(self, name, age, email):
        self.name = name
        self.age = age
        self.email = email

    def get_info(self):
        return f"{self.name}, {self.age} years old, {self.email}"

    def have_birthday(self):
        self.age += 1
        return f"{self.name} is now {self.age}"

# Usage
person = Person("Alice", 30, "alice@email.com")
print(person.get_info())
print(person.have_birthday())
```

---

### 19. Password Validator (from AI)
```python
def validate_password(password):
    """
    Validate password:
    - At least 8 characters
    - Contains uppercase letter
    - Contains lowercase letter
    - Contains number
    - Contains special character
    """
    if len(password) < 8:
        return False, "Password must be at least 8 characters"

    has_upper = any(char.isupper() for char in password)
    has_lower = any(char.islower() for char in password)
    has_digit = any(char.isdigit() for char in password)
    has_special = any(char in "!@#$%^&*" for char in password)

    if not has_upper:
        return False, "Password must contain uppercase letter"
    if not has_lower:
        return False, "Password must contain lowercase letter"
    if not has_digit:
        return False, "Password must contain number"
    if not has_special:
        return False, "Password must contain special character"

    return True, "Password is valid"

# Test
print(validate_password("weak"))  # False
print(validate_password("Strong123!"))  # True
```

---

## Verification Examples

### 23. BankAccount Class Testing
```python
class BankAccount:
    def __init__(self, balance=0):
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return True
        return False

    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            return True
        return False

    def get_balance(self):
        return self.balance

# Testing
def test_bank_account():
    account = BankAccount(100)

    # Test initial balance
    assert account.get_balance() == 100, "Initial balance incorrect"

    # Test deposit
    assert account.deposit(50) == True, "Deposit failed"
    assert account.get_balance() == 150, "Balance after deposit incorrect"

    # Test withdraw
    assert account.withdraw(30) == True, "Withdraw failed"
    assert account.get_balance() == 120, "Balance after withdraw incorrect"

    # Test invalid operations
    assert account.withdraw(150) == False, "Should not withdraw more than balance"
    assert account.deposit(-10) == False, "Should not deposit negative amount"

    print("All tests passed!")

test_bank_account()
```

---

## Debugging Examples

### 31. IndexError Debugging
**Your code:**
```python
numbers = [1, 2, 3]
print(numbers[5])  # IndexError: list index out of range
```

**What to ask AI:**
```
I'm getting IndexError when trying to access index 5 in a list with 3 elements.
How do I safely check if an index exists before accessing it?
```

**AI might suggest:**
```python
numbers = [1, 2, 3]

# Option 1: Check length
if len(numbers) > 5:
    print(numbers[5])
else:
    print("Index out of range")

# Option 2: Use try-except
try:
    print(numbers[5])
except IndexError:
    print("Index out of range")
```

---

### 32. Function Returns None
**Your code:**
```python
def add_numbers(a, b):
    a + b  # Missing return statement!

result = add_numbers(5, 3)
print(result)  # None
```

**What to ask AI:**
```
My function should return the sum of two numbers but it returns None.
What's wrong with this code?
```

**Fix:**
```python
def add_numbers(a, b):
    return a + b  # Add return statement
```

---

## Learning Examples

### 41. Decorator Explanation Request
**Prompt to AI:**
```
Explain what a Python decorator is in simple terms.
Show a real example of a decorator that adds timing to a function.
```

**Study the response and understand:**
- What decorators are
- How they work
- Why they're useful
- How to create one

---

### 42. List Comprehension Examples
**Prompt:**
```
Show me 3 different examples of list comprehensions:
1. Squaring numbers
2. Filtering even numbers
3. Converting strings to integers
Explain each one line by line.
```

**Code to study:**
```python
# Example 1: Square numbers
squares = [x**2 for x in range(5)]
# Result: [0, 1, 4, 9, 16]

# Example 2: Filter even numbers
evens = [x for x in range(10) if x % 2 == 0]
# Result: [0, 2, 4, 6, 8]

# Example 3: Convert strings to integers
numbers = [int(x) for x in ['1', '2', '3']]
# Result: [1, 2, 3]
```

---

## Real-world Project Example

### Student Grade System (51-55)

**Exercise 51: Calculate Average**
```python
def calculate_average(grades):
    if not grades:
        return 0
    return sum(grades) / len(grades)

# Test
print(calculate_average([90, 85, 95]))  # 90.0
```

**Exercise 52: Read from CSV**
```python
import csv

def read_grades_from_csv(filename):
    grades = []
    try:
        with open(filename, 'r') as file:
            reader = csv.DictReader(file)
            for row in reader:
                grades.append({
                    'name': row['name'],
                    'grade': int(row['grade'])
                })
    except FileNotFoundError:
        print(f"File {filename} not found")
    return grades

# Usage
students = read_grades_from_csv('grades.csv')
```

**Exercise 53: Find Highest Grade**
```python
def find_highest_grade(students):
    if not students:
        return None
    return max(students, key=lambda s: s['grade'])

# Usage
top_student = find_highest_grade(students)
print(f"Top student: {top_student['name']}")
```

**Exercise 54: Generate Report**
```python
def generate_report(students):
    report = "GRADE REPORT\n"
    report += "=" * 40 + "\n"
    for student in students:
        report += f"{student['name']}: {student['grade']}\n"
    report += f"Average: {calculate_average([s['grade'] for s in students]):.2f}\n"
    return report

# Usage
print(generate_report(students))
```

**Exercise 55: Validate Grades**
```python
def validate_grade(grade):
    try:
        grade_int = int(grade)
        if 0 <= grade_int <= 100:
            return True, "Valid grade"
        else:
            return False, "Grade must be between 0 and 100"
    except ValueError:
        return False, "Grade must be a number"

# Test
print(validate_grade(95))   # (True, "Valid grade")
print(validate_grade(105))  # (False, "Grade must be...")
print(validate_grade("abc")) # (False, "Grade must be...")
```

---

## Debugging Request Examples

### Example: TypeError Debugging
**Your error:**
```
TypeError: unsupported operand type(s) for +: 'str' and 'int'
```

**What to ask AI:**
```
I'm getting this error: TypeError: unsupported operand type(s) for +: 'str' and 'int'

Here's my code:
```python
age = "25"
result = age + 5
```

How do I fix this?
```

**AI Response might suggest:**
```python
# Option 1: Convert string to int
age = "25"
result = int(age) + 5

# Option 2: Convert to string for concatenation
age = "25"
result = age + str(5)

# Option 3: Use f-string
age = "25"
result = f"{age}5"
```

---

## Critical Thinking Example

### 71. Compare Two Solutions

**Ask AI:**
```
Generate two different ways to find the most common item in a list.
```

**Compare them:**
```python
# Method 1: Using Counter
from collections import Counter

def most_common_v1(items):
    return Counter(items).most_common(1)[0][0]

# Method 2: Manual counting
def most_common_v2(items):
    counts = {}
    for item in items:
        counts[item] = counts.get(item, 0) + 1
    return max(counts, key=counts.get)

# Which is better?
# v1: More Pythonic, readable, built-in optimized
# v2: More educational, shows manual logic
```

---

## Project: Todo App with AI

**Step 1: Ask AI for TodoList class**
```python
class TodoList:
    def __init__(self):
        self.tasks = []

    def add(self, task):
        self.tasks.append({'task': task, 'done': False})

    def remove(self, task):
        self.tasks = [t for t in self.tasks if t['task'] != task]

    def complete(self, task):
        for t in self.tasks:
            if t['task'] == task:
                t['done'] = True

    def list_all(self):
        return self.tasks
```

**Step 2: Ask AI for file persistence**
```python
import json

def save_tasks(todo_list, filename='tasks.json'):
    with open(filename, 'w') as f:
        json.dump(todo_list.list_all(), f)

def load_tasks(todo_list, filename='tasks.json'):
    try:
        with open(filename, 'r') as f:
            tasks = json.load(f)
            for task in tasks:
                todo_list.tasks.append(task)
    except FileNotFoundError:
        pass
```

**Step 3: Ask AI for CLI interface**
```python
def main():
    todo = TodoList()
    load_tasks(todo)

    while True:
        print("\n1. Add task\n2. List tasks\n3. Complete task\n4. Remove task\n5. Exit")
        choice = input("Choose: ")

        if choice == '1':
            task = input("Enter task: ")
            todo.add(task)
        elif choice == '2':
            for t in todo.list_all():
                status = "✓" if t['done'] else "○"
                print(f"{status} {t['task']}")
        elif choice == '5':
            save_tasks(todo)
            break

if __name__ == '__main__':
    main()
```

---

## Summary Checklist

When using AI for coding:
- [ ] Write clear, specific prompts
- [ ] Ask for examples and explanations
- [ ] Understand the generated code
- [ ] Test thoroughly with multiple cases
- [ ] Verify edge case handling
- [ ] Check for security issues
- [ ] Review best practices
- [ ] Don't blindly copy-paste
- [ ] Learn from the code structure
- [ ] Ask follow-up questions

---
