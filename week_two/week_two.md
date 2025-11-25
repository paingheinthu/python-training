# Programming Training — Python Syntax, Comments, Lists & Loops

## Recap
 - Programming history
 - Variables
 - Condition & Truth Table

---

## Objectives
* Understand Python basic syntax
* Comments and style
* Lists (arrays) and common operations
* Loops: for, while, loop control
* Hands-on exercises & mini-challenges

---

## Python Syntax — The Basics
* Interpreter vs. Compiler (quick)
* Indentation is syntax: no braces
* Statements, expressions and blocks
* Case-sensitive names


## Hello world — first program
```python
# simple print
print('Hello, world!')
```


## Indentation is Syntax (No Braces)
Python uses indentation to define code blocks instead of `{}` braces.
```python
# Correct indentation
def greet():
    print("Hello!")
    print("Welcome!")

# Incorrect (will cause IndentationError)
def greet():
print("Hello!")
```

## Statements, Expressions & Blocks
Python separates simple expressions from larger statements that form blocks.
```python
# Expression (evaluates to a value)
x = 3 + 5

# Statement (performs an action)
print(x)

# Block (group of statements via indentation)
if x > 5:
    print("x is large")
    x += 1
```

## Case-Sensitive Names
Python treats variable names with different cases as different identifiers.
```python
value = 10
Value = 20
VALUE = 30

print(value)  # 10
print(Value)  # 20
print(VALUE)  # 30
```
---
## Comments & Good Style
* Single-line: # comment
* Multi-line / docstring: triple quotes
* Why: readability, TODOs, docstrings
* PEP8 basics: 79-char lines, snake_case

---

## Examples of comments
```python
# This is a single-line comment
'''
This is a multi-line docstring (or comment)
Useful for function/module docs
'''
def add(a, b):
    """Return sum of a and b."""
    return a + b
```
---

---

## Lists — Python arrays
* Ordered, mutable collection
* Can contain mixed types
* Indexing (0-based) and slicing
* Common methods: append, extend, insert, pop, remove, sort

---
## Tuple Examples
```python
# Example 1: Basic tuple
t1 = (1, 2, 3)

# Example 2: Mixed types
t2 = ("apple", 3.14, True)

# Example 3: Nested tuple
t3 = (1, (2, 3), 4)

#Example 4: single tuple
t4 = (1,)
```

## List Examples
```python
# Example 1: Basic list
l1 = [1, 2, 3]

# Example 2: Adding items
l2 = []
l2.append("apple")
l2.append("banana")
l2.append("cherry")
print(l2)
print(l2[0])  # 'apple'
print(l2[1:3])  # slice

```

## Dictionary Examples
```python
# Example 1: Basic dictionary
d1 = {"name": "Alice", "age": 25}

# Example 2: Adding values
d2 = {}
d2["city"] = "Yangon"
d2["country"] = "Myanmar"
```
---

## Looping — for and while
* for: iterate over sequences (lists, range, strings)
* while: loop with condition
* break and continue for control
* use enumerate() when index needed

---
## Using range() and For loop examples
The `range()` function generates sequences of numbers.
```python
# Basic usage
for i in range(5):
    print(i)  # 0 1 2 3 4

# Start and end
for i in range(2, 6):
    print(i)  # 2 3 4 5

# With step
for i in range(0, 10, 2):
    print(i)  # 0 2 4 6 8

for idx, val in enumerate(['a','b','c']):
    print(idx, val)


# List comprehension
l3 = [x * 2 for x in range(5)]

# Looping through dict
d3 = {"a": 1, "b": 2}
for key, value in d3.items():
    print(key, value)
```

---

## While loop example
```python
count = 0
while count < 3:
    print('tick', count)
    count += 1
```

---

## Hands-on Exercises (15–20 min)
Work in pairs — rotate after 10 minutes.
1. Write a function that returns even numbers from a list
2. Using a loop, compute factorial of n
3. Given a list of names, print numbered list using enumerate

---

## Quick Quiz (live)
1. What is the output: print(len([1,2,3]))?
2. How to comment a single line?
3. What does list.pop() do?

---

## Wrap-up & Next Steps
* Recap takeaways
* Homework: small script using lists & loops
* Preview: functions, modules

---