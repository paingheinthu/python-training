# Functions & Modules — Detailed Notes + Exercises (Python Only)

## Table of Contents
1. What is a Function?
2. Why Do We Use Functions?
3. Function Structure
4. Parameters vs Arguments
5. Return Values
6. Pure vs Impure Functions
7. What is a Module?
8. Importing Modules
9. Creating Your Own Module
10. Exercises

---

# 1. What is a Function?

A function is a reusable block of code that performs a specific task.

Example (conceptual):
    def wash_dishes():
        pick soap
        scrub
        rinse

---

# 2. Why Do We Use Functions?

| Benefit          | Explanation          |
| ---------------- | -------------------- |
| Reusability      | Use logic many times |
| Maintainability  | Easy to update logic |
| Readability      | Code becomes clean   |
| Avoid repetition | No duplicated code   |

---

# 3. Function Structure

General structure:
```python
    def function_name(parameter1, parameter2):
        # logic
        return result
```

Parts:
- Name
- Parameters
- Body
- Return value

---

# 4. Parameters vs Arguments

Example:
```python
def add(a, b):   # a and b are parameters
    return a + b

add(3, 5)        # 3 and 5 are arguments
```

---

# 5. Return Values

A function may:
- return a value
- return multiple values
- return nothing (None)

Example:
```python
def multiply(a, b):
    return a * b
```
---

# 6. Pure vs Impure Functions

Pure function:
```python
def square(x):
    return x * x
```
Impure function:
```python
def alert(msg):
    print(msg)
```

---

# 7. What is a Module?

A module is a Python file containing:
- functions
- variables
- classes

Examples:
- utils.py
- math_tools.py

---

# 8. Importing Modules
```python
import math
from datetime import datetime
import json as js
```
---

# 9. Creating Your Own Module

File:
utils.py
```python
def greet(name):
    return f"Hello, {name}"
```

Usage:
```python
import utils
print(utils.greet("Paing"))
```

---

# 10. Exercises

## Beginner Exercises
1. Write a function that prints your name.
2. Write a function that adds two numbers.
3. Write a function that calculates rectangle area.
4. Write a function that checks if a number is even.
5. Create a module with say_hello() and import it.

---

## Intermediate Exercises
6. Write sum_list(numbers) that returns total.
7. Write a function returning largest of 3 numbers.
8. Write a function to reverse a string.
9. Write a function that counts vowels.
10. Create mathutils.py with add, subtract, multiply, divide.

---

## Challenge Exercises
11. Create bank.py containing:
    - deposit(balance, amount)
    - withdraw(balance, amount)
    - transfer(bal_a, bal_b, amount)

    Rules:
    - no negative balance
    - must be pure functions (no print)

12. Write is_palindrome(text) without slicing.
13. Create a module that loads a file, counts words, finds most frequent word.

---