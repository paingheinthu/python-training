# File Read/Write & File Operations — Python Complete Guide

## Table of Contents
1. What is File I/O?
2. Opening and Closing Files
3. Reading Files
4. Writing Files
5. Appending to Files
6. Working with Different File Formats
7. File Operations Best Practices
8. Common Errors and Solutions
9. Exercises

---

## 1. What is File I/O?

File I/O (Input/Output) is the process of reading data from files or writing data to files.

**Why we need it:**
- Store data persistently
- Read configuration files
- Process large datasets
- Log application events
- Exchange data between programs

---

## 2. Opening and Closing Files

### The basic syntax:
```python
# Opening a file
file = open('filename.txt', mode)

# Doing something with the file
# ...

# Closing the file
file.close()
```

### File Modes

| Mode | Purpose |
|------|---------|
| `'r'` | Read (default) — file must exist |
| `'w'` | Write — creates new file or overwrites existing |
| `'a'` | Append — adds to the end of file |
| `'x'` | Create — creates new file, errors if exists |
| `'rb'` | Read binary |
| `'wb'` | Write binary |

---

## 3. Reading Files

### Method 1: Using `read()` - Read entire file as string

```python
file = open('data.txt', 'r')
content = file.read()
print(content)
file.close()
```

**Example:**
```python
file = open('hello.txt', 'r')
data = file.read()
print(data)  # prints entire file content
file.close()
```

---

### Method 2: Using `readline()` - Read one line at a time

```python
file = open('data.txt', 'r')
line1 = file.readline()
line2 = file.readline()
print(line1)
print(line2)
file.close()
```

**Example:**
```python
file = open('hello.txt', 'r')
first_line = file.readline()
second_line = file.readline()
print(first_line)
print(second_line)
file.close()
```

---

### Method 3: Using `readlines()` - Read all lines as list

```python
file = open('data.txt', 'r')
lines = file.readlines()
for line in lines:
    print(line)
file.close()
```

**Example:**
```python
file = open('hello.txt', 'r')
all_lines = file.readlines()
for line in all_lines:
    print(line.strip())  # strip() removes \n
file.close()
```

---

### Method 4: Iterating through file (most efficient)

```python
file = open('data.txt', 'r')
for line in file:
    print(line.strip())
file.close()
```

---

## 4. Writing Files

### Basic write operation

```python
file = open('output.txt', 'w')
file.write('Hello, World!\n')
file.write('This is a new line.\n')
file.close()
```

**Example:**
```python
file = open('greeting.txt', 'w')
file.write('Welcome to Python!\n')
file.write('File I/O is fun!\n')
file.close()

# Read it back
file = open('greeting.txt', 'r')
print(file.read())
file.close()
```

**Output:**
```
Welcome to Python!
File I/O is fun!
```

---

### Writing with loops

```python
file = open('numbers.txt', 'w')
for i in range(1, 6):
    file.write(f"Number: {i}\n")
file.close()
```

---

## 5. Appending to Files

### Using 'a' mode to add content

```python
file = open('output.txt', 'a')
file.write('Appended line\n')
file.close()
```

**Example:**
```python
# Create file
file = open('log.txt', 'w')
file.write('Log started\n')
file.close()

# Append to file
file = open('log.txt', 'a')
file.write('First event\n')
file.write('Second event\n')
file.close()

# Read entire file
file = open('log.txt', 'r')
print(file.read())
file.close()
```

**Output:**
```
Log started
First event
Second event
```

---

## 6. The `with` Statement (Context Manager) — BEST PRACTICE

The `with` statement automatically closes files, even if errors occur.

```python
with open('data.txt', 'r') as file:
    content = file.read()
    print(content)
# File is automatically closed here
```

**Why it's better:**
- Automatic file closing
- Cleaner code
- Handles errors gracefully

---

### Examples with `with`

**Reading:**
```python
with open('hello.txt', 'r') as file:
    for line in file:
        print(line.strip())
```

**Writing:**
```python
with open('output.txt', 'w') as file:
    file.write('Line 1\n')
    file.write('Line 2\n')
```

**Appending:**
```python
with open('log.txt', 'a') as file:
    file.write('New log entry\n')
```

---

## 7. Working with Different File Formats

### 7.1 Text Files

```python
# Writing
with open('notes.txt', 'w') as file:
    file.write('This is a simple text file\n')

# Reading
with open('notes.txt', 'r') as file:
    content = file.read()
    print(content)
```

---

### 7.2 CSV Files (Comma-Separated Values)

```python
import csv

# Writing CSV
with open('data.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'Age', 'City'])
    writer.writerow(['Alice', 30, 'New York'])
    writer.writerow(['Bob', 25, 'Los Angeles'])

# Reading CSV
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

**Output:**
```
['Name', 'Age', 'City']
['Alice', '30', 'New York']
['Bob', '25', 'Los Angeles']
```

---

### 7.3 JSON Files

```python
import json

# Writing JSON
data = {
    'name': 'Alice',
    'age': 30,
    'city': 'New York'
}

with open('data.json', 'w') as file:
    json.dump(data, file, indent=2)

# Reading JSON
with open('data.json', 'r') as file:
    loaded_data = json.load(file)
    print(loaded_data)
    print(loaded_data['name'])
```

---

## 8. File Operations Best Practices

### ✅ DO:

1. **Use `with` statement**
```python
with open('file.txt', 'r') as file:
    content = file.read()
```

2. **Strip newlines when reading**
```python
with open('file.txt', 'r') as file:
    for line in file:
        clean_line = line.strip()
```

3. **Use descriptive file paths**
```python
filename = 'data.txt'
with open(filename, 'r') as file:
    data = file.read()
```

---

### ❌ DON'T:

1. **Forget to close files**
```python
# BAD - file never closes
file = open('data.txt', 'r')
content = file.read()
```

2. **Assume files exist**
```python
# MAY FAIL - file might not exist
file = open('nonexistent.txt', 'r')
```

---

## 9. Error Handling

### Checking if file exists

```python
import os

if os.path.exists('file.txt'):
    with open('file.txt', 'r') as file:
        content = file.read()
else:
    print("File not found")
```

---

### Try-except for error handling

```python
try:
    with open('data.txt', 'r') as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("File does not exist")
except IOError:
    print("Error reading file")
```

---

## 10. Common File Operations

### Check file size

```python
import os

file_size = os.path.getsize('data.txt')
print(f"File size: {file_size} bytes")
```

---

### Get file modification time

```python
import os
import time

file_time = os.path.getmtime('data.txt')
formatted_time = time.ctime(file_time)
print(f"Last modified: {formatted_time}")
```

---

### Delete a file

```python
import os

if os.path.exists('old_file.txt'):
    os.remove('old_file.txt')
```

---

### Rename a file

```python
import os

os.rename('old_name.txt', 'new_name.txt')
```

---

## Summary

| Task | Syntax |
|------|--------|
| Read entire file | `file.read()` |
| Read line by line | `file.readline()` or loop `for line in file` |
| Read all lines | `file.readlines()` |
| Write to file | `file.write(text)` |
| Append to file | Open with mode `'a'` |
| Close file | `file.close()` or use `with` |
| Check if exists | `os.path.exists(filename)` |
| Delete file | `os.remove(filename)` |

---
