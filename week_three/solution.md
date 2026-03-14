# Python Exercises – All Solutions

```python
# =========================
# Beginner Exercises
# =========================

def print_name():
    print("Paing Hein Thu")


def add(a, b):
    return a + b


def rectangle_area(width, height):
    return width * height


def is_even(number):
    return number % 2 == 0


# hello.py
def say_hello():
    print("Hello!")


# =========================
# Intermediate Exercises
# =========================

def sum_list(numbers):
    total = 0
    for n in numbers:
        total += n
    return total


def largest(a, b, c):
    max_value = a
    if b > max_value:
        max_value = b
    if c > max_value:
        max_value = c
    return max_value


def reverse_string(text):
    result = ""
    for char in text:
        result = char + result
    return result


def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count


# mathutils.py
def math_add(a, b):
    return a + b


def math_subtract(a, b):
    return a - b


def math_multiply(a, b):
    return a * b


def math_divide(a, b):
    if b == 0:
        return None
    return a / b


# =========================
# Challenge Exercises
# =========================

# bank.py
def deposit(balance, amount):
    if amount < 0:
        return balance
    return balance + amount


def withdraw(balance, amount):
    if amount < 0 or amount > balance:
        return balance
    return balance - amount


def transfer(balance_a, balance_b, amount):
    if amount < 0 or amount > balance_a:
        return balance_a, balance_b
    return balance_a - amount, balance_b + amount


def is_palindrome(text):
    left = 0
    right = len(text) - 1
    while left < right:
        if text[left] != text[right]:
            return False
        left += 1
        right -= 1
    return True


def analyze_file(filename):
    with open(filename, "r", encoding="utf-8") as file:
        text = file.read().lower()

    words = text.split()
    frequency = {}

    for word in words:
        frequency[word] = frequency.get(word, 0) + 1

    most_frequent_word = max(frequency, key=frequency.get)

    return {
        "total_words": len(words),
        "most_frequent_word": most_frequent_word,
        "count": frequency[most_frequent_word],
    }