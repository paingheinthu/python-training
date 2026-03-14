# Solutions: File Read/Write & File Operations

## Basic File Reading Exercises

### 1. Create and read greeting.txt
```python
# First, create the file
with open('greeting.txt', 'w') as file:
    file.write('Hello, Python!')

# Then read it
with open('greeting.txt', 'r') as file:
    content = file.read()
    print(content)
```

---

### 2. Create file with name and read it back
```python
# Write name
with open('myname.txt', 'w') as file:
    file.write('Paing Hein Thu')

# Read it back
with open('myname.txt', 'r') as file:
    name = file.read()
    print(name)
```

---

### 3. Read file line by line with line numbers
```python
with open('file.txt', 'r') as file:
    for line_num, line in enumerate(file, 1):
        print(f"Line {line_num}: {line.strip()}")
```

---

### 4. Count total lines in a file
```python
with open('file.txt', 'r') as file:
    lines = file.readlines()
    total_lines = len(lines)
    print(f"Total lines: {total_lines}")
```

---

### 5. Count total characters in a file
```python
with open('file.txt', 'r') as file:
    content = file.read()
    total_chars = len(content)
    print(f"Total characters: {total_chars}")
```

---

### 6. Count words in a file
```python
with open('file.txt', 'r') as file:
    content = file.read()
    words = content.split()
    total_words = len(words)
    print(f"Total words: {total_words}")
```

---

### 7. Read only first 3 lines
```python
with open('file.txt', 'r') as file:
    for i in range(3):
        line = file.readline()
        if line:
            print(line.strip())
```

---

### 8. Print lines containing letter 'a'
```python
with open('file.txt', 'r') as file:
    for line in file:
        if 'a' in line.lower():
            print(line.strip())
```

---

### 9. Convert all text to uppercase
```python
with open('file.txt', 'r') as file:
    content = file.read()
    uppercase_content = content.upper()
    print(uppercase_content)
```

---

### 10. Remove empty lines when printing
```python
with open('file.txt', 'r') as file:
    for line in file:
        if line.strip():  # Only print non-empty lines
            print(line.strip())
```

---

## File Writing Exercises

### 11. Write name, age, and city
```python
with open('personal.txt', 'w') as file:
    file.write('Alice')
    file.write('\n')
    file.write('30')
    file.write('\n')
    file.write('New York')
```

---

### 12. Write numbers 1 to 10
```python
with open('numbers.txt', 'w') as file:
    for i in range(1, 11):
        file.write(f"{i}\n")
```

---

### 13. Write multiplication table of 7
```python
with open('table_7.txt', 'w') as file:
    for i in range(1, 11):
        file.write(f"7 * {i} = {7 * i}\n")
```

---

### 14. Write list of fruits
```python
fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry']

with open('fruits.txt', 'w') as file:
    for fruit in fruits:
        file.write(f"{fruit}\n")
```

---

### 15. Write formatted profile
```python
with open('profile.txt', 'w') as file:
    file.write("Name: Alice\n")
    file.write("Age: 30\n")
    file.write("City: New York\n")
```

---

### 16. Write even numbers 1 to 20
```python
with open('even_numbers.txt', 'w') as file:
    for i in range(2, 21, 2):
        file.write(f"{i}\n")
```

---

### 17. Write star pattern
```python
with open('pattern.txt', 'w') as file:
    for i in range(1, 6):
        file.write("*" * i + "\n")
```

---

### 18. Write squares of 1 to 10
```python
with open('squares.txt', 'w') as file:
    for i in range(1, 11):
        file.write(f"{i}^2 = {i**2}\n")
```

---

### 19. Write CSV header
```python
with open('data.csv', 'w') as file:
    file.write("Name,Age,Salary\n")
```

---

### 20. Write list of colors
```python
colors = ['red', 'green', 'blue', 'yellow', 'purple']

with open('colors.txt', 'w') as file:
    for color in colors:
        file.write(f"{color}\n")
```

---

## File Appending Exercises

### 21. Create and append to file
```python
# Create file
with open('log.txt', 'w') as file:
    file.write("Day 1: Started learning Python\n")

# Append to file
with open('log.txt', 'a') as file:
    file.write("Day 2: Learning file I/O\n")

# Read to verify
with open('log.txt', 'r') as file:
    print(file.read())
```

---

### 22. Append log entries with timestamps
```python
from datetime import datetime

with open('events.log', 'w') as file:
    file.write("Event Log Started\n")

events = [
    "Login successful",
    "File uploaded",
    "Process completed"
]

with open('events.log', 'a') as file:
    for event in events:
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        file.write(f"[{timestamp}] {event}\n")
```

---

### 23. Append only if line doesn't exist
```python
new_line = "This is a new entry\n"

with open('data.txt', 'r') as file:
    content = file.read()

if new_line.strip() not in content:
    with open('data.txt', 'a') as file:
        file.write(new_line)
```

---

### 24. Create, write, then append
```python
# Create and write
with open('notes.txt', 'w') as file:
    file.write("Initial note\n")

# Append 5 more lines
with open('notes.txt', 'a') as file:
    for i in range(1, 6):
        file.write(f"Additional note {i}\n")
```

---

### 25. Append numbers after reading
```python
# Create initial file
with open('numbers.txt', 'w') as file:
    file.write("1\n2\n3\n")

# Read and append
with open('numbers.txt', 'r') as file:
    lines = file.readlines()
    last_number = int(lines[-1].strip())

with open('numbers.txt', 'a') as file:
    for i in range(last_number + 1, last_number + 4):
        file.write(f"{i}\n")
```

---

## File Processing Exercises

### 26. Count lines starting with 'T'
```python
count = 0
with open('file.txt', 'r') as file:
    for line in file:
        if line.strip().startswith('T'):
            count += 1
print(f"Lines starting with 'T': {count}")
```

---

### 27. Find the longest line
```python
with open('file.txt', 'r') as file:
    lines = file.readlines()
    longest_line = max(lines, key=len)
    print(f"Longest line: {longest_line.strip()}")
    print(f"Length: {len(longest_line.strip())}")
```

---

### 28. Print lines longer than 20 characters
```python
with open('file.txt', 'r') as file:
    for line in file:
        if len(line.strip()) > 20:
            print(line.strip())
```

---

### 29. Remove extra spaces and save
```python
with open('input.txt', 'r') as file:
    content = file.read()

# Remove extra spaces
cleaned_content = ' '.join(content.split())

with open('output.txt', 'w') as file:
    file.write(cleaned_content)
```

---

### 30. Replace word and save
```python
with open('input.txt', 'r') as file:
    content = file.read()

# Replace old_word with new_word
old_word = 'Python'
new_word = 'Java'
new_content = content.replace(old_word, new_word)

with open('output.txt', 'w') as file:
    file.write(new_content)
```

---

### 31. Reverse line order
```python
with open('input.txt', 'r') as file:
    lines = file.readlines()

reversed_lines = lines[::-1]

with open('output.txt', 'w') as file:
    file.writelines(reversed_lines)
```

---

### 32. Word frequency counter
```python
from collections import Counter

with open('file.txt', 'r') as file:
    content = file.read().lower()

words = content.split()
word_freq = Counter(words)
most_common_word = word_freq.most_common(1)[0]

print(f"Most common word: '{most_common_word[0]}' appears {most_common_word[1]} times")
```

---

### 33. Sum numbers from file
```python
with open('numbers.txt', 'r') as file:
    total = 0
    for line in file:
        number = int(line.strip())
        total += number

print(f"Sum: {total}")
```

---

### 34. Filter names starting with 'A'
```python
with open('names.txt', 'r') as file:
    names = file.readlines()

with open('names_with_A.txt', 'w') as file:
    for name in names:
        if name.strip().startswith('A'):
            file.write(name)
```

---

### 35. Sort lines alphabetically
```python
with open('input.txt', 'r') as file:
    lines = file.readlines()

sorted_lines = sorted(lines)

with open('output.txt', 'w') as file:
    file.writelines(sorted_lines)
```

---

## Working with Multiple Files

### 36. Copy file contents
```python
with open('source.txt', 'r') as source:
    content = source.read()

with open('destination.txt', 'w') as dest:
    dest.write(content)
```

---

### 37. Merge two files
```python
with open('output.txt', 'w') as output:
    # Write first file
    with open('file1.txt', 'r') as file1:
        output.write(file1.read())

    # Write second file
    with open('file2.txt', 'r') as file2:
        output.write(file2.read())
```

---

### 38. Compare two files
```python
with open('file1.txt', 'r') as f1:
    lines1 = f1.readlines()

with open('file2.txt', 'r') as f2:
    lines2 = f2.readlines()

for i, (line1, line2) in enumerate(zip(lines1, lines2), 1):
    if line1 != line2:
        print(f"Line {i} is different:")
        print(f"  File1: {line1.strip()}")
        print(f"  File2: {line2.strip()}")
```

---

### 39. Read, process, and write
```python
with open('input.txt', 'r') as input_file:
    lines = input_file.readlines()

# Process: convert to uppercase
processed_lines = [line.upper() for line in lines]

with open('output.txt', 'w') as output_file:
    output_file.writelines(processed_lines)
```

---

### 40. Merge number lists
```python
with open('numbers1.txt', 'r') as f1:
    numbers1 = f1.readlines()

with open('numbers2.txt', 'r') as f2:
    numbers2 = f2.readlines()

with open('merged_numbers.txt', 'w') as output:
    output.writelines(numbers1)
    output.writelines(numbers2)
```

---

## Error Handling Exercises

### 41. Handle file not found
```python
try:
    with open('nonexistent.txt', 'r') as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("Error: File not found!")
```

---

### 42. Handle read-only file
```python
try:
    with open('readonly.txt', 'w') as file:
        file.write('test')
except PermissionError:
    print("Error: Cannot write to file (read-only)")
```

---

### 43. Check if file exists
```python
import os

filename = 'file.txt'
if os.path.exists(filename):
    with open(filename, 'r') as file:
        content = file.read()
        print(content)
else:
    print(f"Error: {filename} does not exist")
```

---

### 44. Safe read function
```python
def safe_read(filename):
    try:
        with open(filename, 'r') as file:
            return file.read()
    except FileNotFoundError:
        print(f"File not found: {filename}")
        return None
    except Exception as e:
        print(f"Error reading file: {e}")
        return None

result = safe_read('data.txt')
if result:
    print(result)
```

---

### 45. Safe delete function
```python
import os

filename = 'old_file.txt'
try:
    if os.path.exists(filename):
        os.remove(filename)
        print(f"Deleted: {filename}")
    else:
        print(f"File not found: {filename}")
except Exception as e:
    print(f"Error deleting file: {e}")
```

---

## CSV & Data Format Exercises

### 46. Create CSV file
```python
import csv

with open('students.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'ID', 'Grade'])
    writer.writerow(['Alice', '001', 'A'])
    writer.writerow(['Bob', '002', 'B'])
    writer.writerow(['Charlie', '003', 'A'])
```

---

### 47. Read CSV file
```python
import csv

with open('students.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

---

### 48. Filter CSV by grade
```python
import csv

with open('students.csv', 'r') as file:
    reader = csv.reader(file)
    next(reader)  # Skip header
    for row in reader:
        if row[2] == 'A':
            print(f"{row[0]}: {row[2]}")
```

---

### 49. Add row to CSV
```python
import csv

# Read existing data
with open('students.csv', 'r') as file:
    reader = csv.reader(file)
    rows = list(reader)

# Add new row
rows.append(['David', '004', 'B'])

# Write back
with open('students.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(rows)
```

---

### 50. Calculate average from CSV
```python
import csv

total = 0
count = 0

with open('scores.csv', 'r') as file:
    reader = csv.reader(file)
    next(reader)  # Skip header
    for row in reader:
        score = int(row[1])
        total += score
        count += 1

average = total / count if count > 0 else 0
print(f"Average score: {average:.2f}")
```

---

## JSON File Exercises

### 51. Write dictionary to JSON
```python
import json

data = {
    'name': 'Alice',
    'age': 30,
    'city': 'New York'
}

with open('person.json', 'w') as file:
    json.dump(data, file, indent=2)
```

---

### 52. Read JSON and print values
```python
import json

with open('person.json', 'r') as file:
    data = json.load(file)
    print(f"Name: {data['name']}")
    print(f"Age: {data['age']}")
    print(f"City: {data['city']}")
```

---

### 53. JSON with list of dictionaries
```python
import json

people = [
    {'name': 'Alice', 'age': 30, 'city': 'New York'},
    {'name': 'Bob', 'age': 25, 'city': 'Los Angeles'},
    {'name': 'Charlie', 'age': 35, 'city': 'Chicago'}
]

with open('people.json', 'w') as file:
    json.dump(people, file, indent=2)
```

---

### 54. Add entry to JSON
```python
import json

# Read existing
with open('people.json', 'r') as file:
    people = json.load(file)

# Add new entry
people.append({'name': 'David', 'age': 28, 'city': 'Boston'})

# Write back
with open('people.json', 'w') as file:
    json.dump(people, file, indent=2)
```

---

### 55. Extract names from JSON
```python
import json

with open('people.json', 'r') as file:
    people = json.load(file)

with open('names.txt', 'w') as file:
    for person in people:
        file.write(f"{person['name']}\n")
```

---

## Advanced Exercises

### 56. File statistics
```python
def file_statistics(filename):
    with open(filename, 'r') as file:
        content = file.read()

    lines = content.split('\n')
    words = content.split()

    stats = {
        'total_lines': len([l for l in lines if l.strip()]),
        'total_words': len(words),
        'total_characters': len(content)
    }

    with open('stats.txt', 'w') as file:
        for key, value in stats.items():
            file.write(f"{key}: {value}\n")

    return stats

file_statistics('input.txt')
```

---

### 57. Filter numbers greater than 100
```python
with open('numbers.txt', 'r') as file:
    numbers = file.readlines()

with open('large_numbers.txt', 'w') as file:
    for num_str in numbers:
        num = int(num_str.strip())
        if num > 100:
            file.write(f"{num}\n")
```

---

### 58. Character frequency counter
```python
with open('file.txt', 'r') as file:
    content = file.read()

char_freq = {}
for char in content:
    if char.isalpha():
        char = char.lower()
        char_freq[char] = char_freq.get(char, 0) + 1

# Sort by frequency
sorted_freq = sorted(char_freq.items(), key=lambda x: x[1], reverse=True)
for char, freq in sorted_freq:
    print(f"{char}: {freq}")
```

---

### 59. Convert to uppercase and save
```python
with open('input.txt', 'r') as file:
    content = file.read()

uppercase_content = content.upper()

with open('output.txt', 'w') as file:
    file.write(uppercase_content)
```

---

### 60. Directory file listing
```python
import os

output = []
for filename in os.listdir('.'):
    if os.path.isfile(filename):
        size = os.path.getsize(filename)
        output.append(f"{filename} - {size} bytes\n")

with open('file_listing.txt', 'w') as file:
    file.writelines(output)
```

---

## Project Solutions

### Project 1: Student Grade Manager
```python
def add_student(name, grade):
    with open('grades.txt', 'a') as file:
        file.write(f"{name},{grade}\n")

def calculate_average():
    total = 0
    count = 0
    with open('grades.txt', 'r') as file:
        for line in file:
            name, grade = line.strip().split(',')
            total += int(grade)
            count += 1
    return total / count if count > 0 else 0

def find_highest():
    highest_name = ""
    highest_grade = -1
    with open('grades.txt', 'r') as file:
        for line in file:
            name, grade = line.strip().split(',')
            grade = int(grade)
            if grade > highest_grade:
                highest_grade = grade
                highest_name = name
    return highest_name, highest_grade

# Usage
add_student('Alice', 95)
add_student('Bob', 87)
add_student('Charlie', 92)

print(f"Average: {calculate_average():.2f}")
name, grade = find_highest()
print(f"Highest: {name} with {grade}")
```

---

### Project 2: Personal Diary
```python
from datetime import datetime

def add_entry(text):
    with open('diary.txt', 'a') as file:
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        file.write(f"[{timestamp}] {text}\n")

def read_all_entries():
    with open('diary.txt', 'r') as file:
        print(file.read())

def search_entries(keyword):
    with open('diary.txt', 'r') as file:
        for line in file:
            if keyword.lower() in line.lower():
                print(line.strip())

# Usage
add_entry('Today was a great day!")
add_entry("Learned about file I/O in Python")
search_entries("Python")
```

---
