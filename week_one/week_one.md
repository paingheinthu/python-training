## Type of programming

### Imperative programming

> OOP

- Java
- PHP
- Python
- C#

### Functional programming

- Lisp
- Haskell
- Elixir

### Declarative programming

- SQL
- HTML
- CSS



### Low Level

### High Level

### Static Type

### Dynamic Type



### History

```
1940s – Machine Code, Assembly
1950s – FORTRAN, LISP (first high-level)
1960s – C (structured programming)
1970s – Smalltalk, Pascal
1980s – C++, OOP boom
1990s – Java, JavaScript, PHP
2000s – Python, Ruby
2010s – Go, Rust
2020s – Multi-paradigm, AI-focused languages
```

## Variable
Variable names must start with a letter. Variable names cannot contain spaces and must be meaningful name. Variables cannot be the same as reserved keywords such as `if` or `const`.

- Camel case
  > variableName
- Snake case
  > variable_name
- Pascal case
  > ClassName
- All capital letter
  > CONSTANT_NAME
- Kebab case
  > file-name

---
 - python
  > variable_name, ClassName, CONSTANT_NAME, function_name, file_name
 - PHP
  > variableName, functionName, ClassName, FileName, CONSTANT_NAME, json_key, db_key
 - GO
  > localVariable, PublicVariable, functionName, PublicFunction, file_name, CONSTANT_NAME

## Basic Boolean Values

| Expression | Result  |
| ---------- | ------- |
| `True`     | ✅ True  |
| `False`    | ❌ False |

---

## NOT Operator (`not` in Python / `!` in Go)

| Input | Output |
| ----- | ------ |
| True  | False  |
| False | True   |

**Example**
```python
print(not True)   # False
print(not False)  # True
```
```go
fmt.Println(!true)   // false
fmt.Println(!false)  // true
```

---

## AND Operator (`and` / `&&`)

| A     | B     | A and B |
| ----- | ----- | ------- |
| False | False | False   |
| False | True  | False   |
| True  | False | False   |
| True  | True  | True    |

**Example**
```python
print(True and True)   # True
print(True and False)  # False
```
```go
fmt.Println(true && true)   // true
fmt.Println(true && false)  // false
```

---

## OR Operator (`or` / `||`)

| A     | B     | A or B |
| ----- | ----- | ------ |
| False | False | False  |
| False | True  | True   |
| True  | False | True   |
| True  | True  | True   |

**Example**
```python
print(True or False)   # True
print(False or False)  # False
```
```go
fmt.Println(true || false)  // true
fmt.Println(false || false) // false
```

---

## Combined Logic Example

| Expression                 | Result |
| -------------------------- | ------ |
| `True and False`           | False  |
| `True or False`            | True   |
| `not False`                | True   |
| `not (True and False)`     | True   |
| `(True and True) or False` | True   |

---

## Comparison Operators

| Expression | Meaning          | Result |
| ---------- | ---------------- | ------ |
| `5 == 5`   | Equal            | True   |
| `5 != 3`   | Not equal        | True   |
| `5 > 3`    | Greater than     | True   |
| `5 < 3`    | Less than        | False  |
| `5 >= 5`   | Greater or equal | True   |
| `5 <= 4`   | Less or equal    | False  |

---

# Conditional Statements — if / elif / else (Python & Go)

## Concept
Conditionals let programs make decisions based on whether an expression is **True** or **False**.

---

## Python Syntax

```python
if condition:
    # code when condition is True
elif another_condition:
    # code when previous condition is False but this one is True
else:
    # code when all above conditions are False
```

### Example
```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 75:
    print("Grade: B")
elif score >= 60:
    print("Grade: C")
else:
    print("Grade: F")
```
**Output:**
```
Grade: B
```

---

## Go Syntax

```go
if condition {
    // code when condition is true
} else if anotherCondition {
    // code when previous condition is false but this is true
} else {
    // code when all conditions are false
}
```

### Example
```go
package main
import "fmt"

func main() {
    score := 85

    if score >= 90 {
        fmt.Println("Grade: A")
    } else if score >= 75 {
        fmt.Println("Grade: B")
    } else if score >= 60 {
        fmt.Println("Grade: C")
    } else {
        fmt.Println("Grade: F")
    }
}
```
**Output:**
```
Grade: B
```

---

## Comparison Examples

| Expression | Meaning                 | Result       |
| ---------- | ----------------------- | ------------ |
| `x > y`    | x greater than y        | True / False |
| `x < y`    | x less than y           | True / False |
| `x == y`   | x equal to y            | True / False |
| `x != y`   | x not equal to y        | True / False |
| `x >= y`   | x greater or equal to y | True / False |
| `x <= y`   | x less or equal to y    | True / False |

---

## Nested If Example

**Python**
```python
age = 20
if age >= 18:
    if age >= 60:
        print("Senior Citizen")
    else:
        print("Adult")
else:
    print("Minor")
```

**Go**
```go
package main
import "fmt"

func main() {
    age := 20
    if age >= 18 {
        if age >= 60 {
            fmt.Println("Senior Citizen")
        } else {
            fmt.Println("Adult")
        }
    } else {
        fmt.Println("Minor")
    }
}
```

---

## Shortcut (Python only)
You can write **one-line if statements**:

```python
x = 10
print("Even") if x % 2 == 0 else print("Odd")
```

---

## Exercises

### Exercise 1 — Positive or Negative
Write a program to check whether a number is positive, negative, or zero.

**Expected Output:**
```
Enter number: -3
Negative
```

---

### Exercise 2 — Even or Odd
Check if a number is even or odd using modulo operator `%`.

---

### Exercise 3 — Grading System
Ask user for score and print grade using:
- 90+ → A
- 75–89 → B
- 60–74 → C
- below 60 → F

---

### Exercise 4 — Largest Number
Compare three numbers and print the largest one.

**Hint (Python):**
```python
if a > b and a > c:
    print("A is largest")
elif b > c:
    print("B is largest")
else:
    print("C is largest")
```

**Hint (Go):**
```go
if a > b && a > c {
    fmt.Println("A is largest")
} else if b > c {
    fmt.Println("B is largest")
} else {
    fmt.Println("C is largest")
}
```

---
