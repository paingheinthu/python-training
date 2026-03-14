# Exercises: Lists, Dictionaries, Loops, and Conditionals

## Lists Exercises

1. Create a list of numbers from 1 to 10.
```python
numbers = list(range(1, 11))
print(numbers)
```

2. Add the number 11 to the list.
```python
numbers.append(11)
print(numbers)
```

3. Remove the number 5 from the list.
```python
numbers.remove(5)
print(numbers)
```

4. Find the sum of all numbers in the list.
```python
total = sum(numbers)
print(total)
```

5. Print all even numbers from the list.
```python
for number in numbers:
    if number % 2 == 0:
        print(number)
```

6. Reverse the list.
```python
numbers.reverse()
print(numbers)
```

7. Find the largest number in the list.
```python
largest_number = max(numbers)
print(largest_number)
```

8. Count how many numbers are greater than 7.
```python
count = 0
for number in numbers:
    if number > 7:
        count += 1
print(count)
```

9. Create a new list with the square of each number.
```python
squared_numbers = [number**2 for number in numbers]
print(squared_numbers)
```

10. Merge two lists `[1,2,3]` and `[4,5,6]`.
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
merged_list = list1 + list2
print(merged_list)
```


## Dictionary Exercises

11. Create a dictionary with keys as names and values as ages.
```python
people = {"Alice": 30, "Bob": 25, "Charlie": 35}
print(people)
```

12. Add a new key-value pair to the dictionary.
```python
people["David"] = 40
print(people)
```

13. Remove a key from the dictionary.
```python
del people["Bob"]
print(people)
```

14. Find the age of a person given their name.
```python
age = people["Alice"]
print(age)
```

15. Print all keys of the dictionary.
```python
print(people.keys())
```

16. Print all values of the dictionary.
```python
print(people.values())
```

17. Check if a key exists in the dictionary.
```python
if "Charlie" in people:
    print("Charlie exists in the dictionary.")
```

18. Count the number of items in the dictionary.
```python
count = len(people)
print(count)
```

19. Create a dictionary from two lists: keys `['a','b','c']` and values `[1,2,3]`.
```python
keys = ['a', 'b', 'c']
values = [1, 2, 3]
new_dict = dict(zip(keys, values))
print(new_dict)
```

20. Update the value of an existing key.
```python
people["Alice"] = 31
print(people)
```


## For Loop Exercises

21. Print numbers from 1 to 20 using a loop.
```python
for i in range(1, 21):
    print(i)
```

22. Print all odd numbers from 1 to 20.
```python
for i in range(1, 21):
    if i % 2 != 0:
        print(i)
```

23. Print the multiplication table of 5.
```python
for i in range(1, 11):
    print(f"5 * {i} = {5*i}")
```

24. Iterate through a list of names and print each name.
```python
names = ["Alice", "Bob", "Charlie"]
for name in names:
    print(name)
```

25. Create a new list containing only numbers divisible by 3.
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
divisible_by_3 = []
for number in numbers:
    if number % 3 == 0:
        divisible_by_3.append(number)
print(divisible_by_3)
```

26. Sum all numbers from 1 to 50 using a loop.
```python
total = 0
for i in range(1, 51):
    total += i
print(total)
```

27. Find the factorial of a number using a loop.
```python
number = 5
factorial = 1
for i in range(1, number + 1):
    factorial *= i
print(factorial)
```

28. Print each character of a string individually.
```python
string = "hello"
for char in string:
    print(char)
```

29. Print the index and value of each element in a list.
```python
numbers = [10, 20, 30, 40, 50]
for index, value in enumerate(numbers):
    print(f"Index: {index}, Value: {value}")
```

30. Count how many numbers in a list are positive.
```python
numbers = [-1, 2, -3, 4, -5, 6]
positive_count = 0
for number in numbers:
    if number > 0:
        positive_count += 1
print(positive_count)
```


## While Loop Exercises

31. Print numbers from 10 down to 1 using a while loop.
```python
i = 10
while i >= 1:
    print(i)
    i -= 1
```

32. Calculate the sum of numbers until the sum exceeds 100.
```python
total = 0
i = 1
while total <= 100:
    total += i
    i += 1
print(total)
```

33. Guess a number game: loop until the correct number is guessed.
```python
import random

number_to_guess = random.randint(1, 10)
guess = 0
while guess != number_to_guess:
    guess = int(input("Guess a number between 1 and 10: "))
print("You guessed it!")
```

34. Print all numbers divisible by 7 from 1 to 100.
```python
i = 1
while i <= 100:
    if i % 7 == 0:
        print(i)
    i += 1
```

35. Find the first number divisible by 13 between 100 and 200.
```python
i = 100
while i <= 200:
    if i % 13 == 0:
        print(i)
        break
    i += 1
```


## Condition Exercises (if, elif, else)

36. Check if a number is even or odd.
```python
number = 10
if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

37. Check if a number is positive, negative, or zero.
```python
number = -5
if number > 0:
    print("Positive")
elif number < 0:
    print("Negative")
else:
    print("Zero")
```

38. Find the largest of three numbers.
```python
a = 10
b = 20
c = 15
if a >= b and a >= c:
    largest = a
elif b >= a and b >= c:
    largest = b
else:
    largest = c
print(largest)
```

39. Determine if a year is a leap year.
```python
year = 2024
if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print("Leap year")
else:
    print("Not a leap year")
```

40. Check if a person is eligible to vote (age ≥ 18).
```python
age = 20
if age >= 18:
    print("Eligible to vote")
else:
    print("Not eligible to vote")
```

41. Print a grade based on marks: A (90+), B (80-89), C (70-79), F (<70).
```python
marks = 85
if marks >= 90:
    grade = "A"
elif marks >= 80:
    grade = "B"
elif marks >= 70:
    grade = "C"
else:
    grade = "F"
print(grade)
```

42. Check if a string contains the letter "a".
```python
string = "hello world"
if "a" in string:
    print("Contains 'a'")
else:
    print("Does not contain 'a'")
```

43. Determine if a number is divisible by 2 and 5.
```python
number = 10
if number % 2 == 0 and number % 5 == 0:
    print("Divisible by 2 and 5")
else:
    print("Not divisible by 2 and 5")
```

44. Print "Fizz" if divisible by 3, "Buzz" if divisible by 5, "FizzBuzz" if divisible by both.
```python
number = 15
if number % 3 == 0 and number % 5 == 0:
    print("FizzBuzz")
elif number % 3 == 0:
    print("Fizz")
elif number % 5 == 0:
    print("Buzz")
```

45. Check if a key exists in a dictionary and print its value or "Not found".
```python
people = {"Alice": 30, "Bob": 25}
if "Alice" in people:
    print(people["Alice"])
else:
    print("Not found")
```

46. Compare two lists and print the common elements.
```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
common_elements = []
for item in list1:
    if item in list2:
        common_elements.append(item)
print(common_elements)
```

47. Determine if a list is sorted in ascending order.
```python
numbers = [1, 2, 3, 4, 5]
is_sorted = True
for i in range(len(numbers) - 1):
    if numbers[i] > numbers[i+1]:
        is_sorted = False
        break
if is_sorted:
    print("Sorted")
else:
    print("Not sorted")
```

48. Print the longest word in a list of words.
```python
words = ["apple", "banana", "cherry"]
longest_word = ""
for word in words:
    if len(word) > len(longest_word):
        longest_word = word
print(longest_word)
```

49. Check if a number is a prime number.
```python
number = 7
is_prime = True
if number > 1:
    for i in range(2, int(number**0.5) + 1):
        if number % i == 0:
            is_prime = False
            break
else:
    is_prime = False

if is_prime:
    print("Prime")
else:
    print("Not prime")
```

50. Find the second largest number in a list.
```python
numbers = [10, 20, 4, 45, 99]
numbers.sort()
print(numbers[-2])
```

