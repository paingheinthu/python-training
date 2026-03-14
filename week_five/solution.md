# Solutions: Classes & Objects

## Beginner Exercises

### 1. Person class with name and age
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

print(person1.name, person1.age)  # Alice 30
print(person2.name, person2.age)  # Bob 25
```

---

### 2. Book class
```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

book = Book("Python Basics", "Guido van Rossum")
print(book.title)   # Python Basics
print(book.author)  # Guido van Rossum
```

---

### 3. Circle class with area calculation
```python
import math

class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

circle = Circle(5)
print(circle.area())  # 78.53981633974483
```

---

### 4. Rectangle class with area
```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

rect = Rectangle(5, 10)
print(rect.area())  # 50
```

---

### 5. Student class
```python
class Student:
    def __init__(self, name, grade, score):
        self.name = name
        self.grade = grade
        self.score = score

student = Student("Alice", "A", 95)
print(f"{student.name}: Grade {student.grade}, Score {student.score}")
```

---

### 6. BankAccount class
```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def check_balance(self):
        return self.balance

account = BankAccount(1000)
print(account.check_balance())  # 1000
```

---

### 7. Car class with describe()
```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

    def describe(self):
        return f"{self.year} {self.brand} {self.model}"

car = Car("Toyota", "Corolla", 2020)
print(car.describe())  # 2020 Toyota Corolla
```

---

### 8. Temperature class
```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    def to_fahrenheit(self):
        return (self.celsius * 9/5) + 32

    def from_fahrenheit(self, fahrenheit):
        self.celsius = (fahrenheit - 32) * 5/9

temp = Temperature(25)
print(temp.to_fahrenheit())  # 77.0
```

---

### 9. Movie class
```python
class Movie:
    def __init__(self, title, director, rating):
        self.title = title
        self.director = director
        self.rating = rating

movie = Movie("Inception", "Christopher Nolan", 8.8)
print(f"{movie.title} by {movie.director}: {movie.rating}/10")
```

---

### 10. Bicycle class
```python
class Bicycle:
    def __init__(self, brand, speed):
        self.brand = brand
        self.speed = speed

bike = Bicycle("Trek", 25)
print(f"{bike.brand} bicycle with speed {bike.speed} km/h")
```

---

## Intermediate Exercises

### 11. Dog class with bark()
```python
class Dog:
    def __init__(self, name, breed, age):
        self.name = name
        self.breed = breed
        self.age = age

    def bark(self):
        print(f"{self.name} barks: Woof!")

dog = Dog("Buddy", "Golden Retriever", 3)
dog.bark()  # Buddy barks: Woof!
```

---

### 12. Calculator class
```python
class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b

    def multiply(self, a, b):
        return a * b

    def divide(self, a, b):
        if b == 0:
            return None
        return a / b

calc = Calculator()
print(calc.add(10, 5))        # 15
print(calc.divide(20, 4))     # 5.0
```

---

### 13. Person with full_name()
```python
class Person:
    def __init__(self, first_name, last_name, age):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age

    def full_name(self):
        return f"{self.first_name} {self.last_name}"

person = Person("John", "Doe", 30)
print(person.full_name())  # John Doe
```

---

### 14. BankAccount with deposit/withdraw
```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return True
        return False

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            return True
        return False

account = BankAccount(1000)
account.deposit(500)
print(account.balance)     # 1500
account.withdraw(200)
print(account.balance)     # 1300
```

---

### 15. Employee class
```python
class Employee:
    def __init__(self, name, salary, department):
        self.name = name
        self.salary = salary
        self.department = department

    def get_info(self):
        return f"{self.name}, Salary: ${self.salary}, Dept: {self.department}"

emp = Employee("Alice", 50000, "Engineering")
print(emp.get_info())
```

---

### 16. Student with average grade
```python
class Student:
    def __init__(self, name, grades):
        self.name = name
        self.grades = grades

    def average_grade(self):
        return sum(self.grades) / len(self.grades)

student = Student("Bob", [85, 90, 88, 92])
print(student.average_grade())  # 88.75
```

---

### 17. Library class
```python
class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def remove_book(self, book):
        if book in self.books:
            self.books.remove(book)

    def list_books(self):
        return self.books

lib = Library()
lib.add_book("Python 101")
lib.add_book("Data Science")
print(lib.list_books())  # ['Python 101', 'Data Science']
```

---

### 18. Weather class
```python
class Weather:
    def __init__(self, temperature, condition):
        self.temperature = temperature
        self.condition = condition

    def describe(self):
        return f"Temperature: {self.temperature}°C, Condition: {self.condition}"

weather = Weather(25, "Sunny")
print(weather.describe())
```

---

### 19. Counter class
```python
class Counter:
    def __init__(self):
        self.count = 0

    def increment(self):
        self.count += 1

    def decrement(self):
        self.count -= 1

    def get_count(self):
        return self.count

counter = Counter()
counter.increment()
counter.increment()
print(counter.get_count())  # 2
counter.decrement()
print(counter.get_count())  # 1
```

---

### 20. ShoppingCart class
```python
class ShoppingCart:
    def __init__(self):
        self.items = []

    def add_item(self, item, price):
        self.items.append((item, price))

    def remove_item(self, item):
        self.items = [(i, p) for i, p in self.items if i != item]

    def total(self):
        return sum(price for item, price in self.items)

cart = ShoppingCart()
cart.add_item("Apple", 1.5)
cart.add_item("Banana", 0.75)
print(cart.total())  # 2.25
```

---

## Inheritance & Polymorphism Exercises

### 21. Animal, Dog, Cat
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound")

class Dog(Animal):
    def speak(self):
        print(f"{self.name} barks: Woof!")

class Cat(Animal):
    def speak(self):
        print(f"{self.name} meows: Meow!")

dog = Dog("Buddy")
cat = Cat("Whiskers")

dog.speak()  # Buddy barks: Woof!
cat.speak()  # Whiskers meows: Meow!
```

---

### 22. Vehicle, Car, Motorcycle
```python
class Vehicle:
    def __init__(self, brand, year):
        self.brand = brand
        self.year = year

    def info(self):
        return f"{self.year} {self.brand}"

class Car(Vehicle):
    def info(self):
        return super().info() + " (Car)"

class Motorcycle(Vehicle):
    def info(self):
        return super().info() + " (Motorcycle)"

car = Car("Toyota", 2020)
moto = Motorcycle("Harley", 2019)

print(car.info())   # 2020 Toyota (Car)
print(moto.info())  # 2019 Harley (Motorcycle)
```

---

### 23. Shape, Square, Triangle
```python
class Shape:
    def area(self):
        return 0

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side ** 2

class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        return (self.base * self.height) / 2

square = Square(5)
triangle = Triangle(4, 6)

print(square.area())    # 25
print(triangle.area())  # 12.0
```

---

### 24. Person, Student, Teacher
```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, student_id):
        super().__init__(name)
        self.student_id = student_id

    def get_info(self):
        return f"Student: {self.name}, ID: {self.student_id}"

class Teacher(Person):
    def __init__(self, name, subject):
        super().__init__(name)
        self.subject = subject

    def get_info(self):
        return f"Teacher: {self.name}, Subject: {self.subject}"

student = Student("Alice", "001")
teacher = Teacher("Mr. Smith", "Math")

print(student.get_info())  # Student: Alice, ID: 001
print(teacher.get_info())  # Teacher: Mr. Smith, Subject: Math
```

---

### 25. Bird, Eagle, Penguin
```python
class Bird:
    def __init__(self, name):
        self.name = name

    def fly(self):
        print(f"{self.name} flies high")

class Eagle(Bird):
    def fly(self):
        print(f"{self.name} soars through the sky")

class Penguin(Bird):
    def fly(self):
        print(f"{self.name} cannot fly (penguins swim instead)")

eagle = Eagle("Eagle")
penguin = Penguin("Penguin")

eagle.fly()     # Eagle soars through the sky
penguin.fly()   # Penguin cannot fly (penguins swim instead)
```

---

## Advanced Exercises

### 31. User class with private password
```python
class User:
    def __init__(self, username, password):
        self.username = username
        self.__password = password

    def set_password(self, new_password):
        self.__password = new_password

    def verify_password(self, password):
        return self.__password == password

user = User("alice", "secret123")
print(user.verify_password("secret123"))  # True
print(user.verify_password("wrong"))      # False
user.set_password("newpass")
print(user.verify_password("newpass"))    # True
```

---

### 32. Rectangle with __str__ and __repr__
```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def __str__(self):
        return f"Rectangle({self.width} x {self.height})"

    def __repr__(self):
        return f"Rectangle(width={self.width}, height={self.height})"

rect = Rectangle(5, 10)
print(str(rect))   # Rectangle(5 x 10)
print(repr(rect))  # Rectangle(width=5, height=10)
```

---

### 33. Vector class with __add__
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __str__(self):
        return f"Vector({self.x}, {self.y})"

v1 = Vector(1, 2)
v2 = Vector(3, 4)
v3 = v1 + v2
print(v3)  # Vector(4, 6)
```

---

### 40. Class variable example
```python
class Student:
    school_name = "Central High"  # Class variable

    def __init__(self, name):
        self.name = name  # Instance variable

student1 = Student("Alice")
student2 = Student("Bob")

print(student1.school_name)  # Central High
print(student2.school_name)  # Central High
print(Student.school_name)   # Central High
```

---

### 43. Using super()
```python
class FinancialAccount:
    def __init__(self, balance):
        self.balance = balance

class BankAccount(FinancialAccount):
    def __init__(self, balance, account_type):
        super().__init__(balance)
        self.account_type = account_type

    def deposit(self, amount):
        self.balance += amount

account = BankAccount(1000, "Savings")
account.deposit(500)
print(account.balance)  # 1500
print(account.account_type)  # Savings
```

---

## Project Solutions

### Project 1: Bank Management System
```python
class Account:
    def __init__(self, account_number, balance):
        self.account_number = account_number
        self.balance = balance
        self.transactions = []

    def deposit(self, amount):
        self.balance += amount
        self.transactions.append(f"Deposit: +${amount}")

    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            self.transactions.append(f"Withdrawal: -${amount}")
        else:
            print("Insufficient balance")

    def get_balance(self):
        return self.balance

class SavingsAccount(Account):
    def __init__(self, account_number, balance, interest_rate):
        super().__init__(account_number, balance)
        self.interest_rate = interest_rate

    def apply_interest(self):
        interest = self.balance * self.interest_rate / 100
        self.balance += interest
        self.transactions.append(f"Interest: +${interest:.2f}")

class CheckingAccount(Account):
    def __init__(self, account_number, balance, monthly_fee):
        super().__init__(account_number, balance)
        self.monthly_fee = monthly_fee

    def charge_fee(self):
        self.balance -= self.monthly_fee
        self.transactions.append(f"Monthly fee: -${self.monthly_fee}")

# Usage
savings = SavingsAccount("S001", 1000, 5)
savings.deposit(500)
savings.apply_interest()
print(savings.get_balance())  # 1550.0

checking = CheckingAccount("C001", 2000, 10)
checking.withdraw(200)
checking.charge_fee()
print(checking.get_balance())  # 1790
```

---

### Project 2: Student Management System
```python
class School:
    def __init__(self, name):
        self.name = name
        self.students = []
        self.teachers = []

    def enroll_student(self, student):
        self.students.append(student)

    def hire_teacher(self, teacher):
        self.teachers.append(teacher)

    def get_all_students(self):
        return [s.name for s in self.students]

class Student:
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.grades = {}

    def assign_grade(self, subject, grade):
        self.grades[subject] = grade

    def get_average(self):
        if not self.grades:
            return 0
        return sum(self.grades.values()) / len(self.grades)

class Teacher:
    def __init__(self, name, subject):
        self.name = name
        self.subject = subject

    def teach(self):
        print(f"{self.name} is teaching {self.subject}")

# Usage
school = School("Central High")
student = Student("Alice", "001")
teacher = Teacher("Mr. Smith", "Math")

school.enroll_student(student)
school.hire_teacher(teacher)

student.assign_grade("Math", 95)
student.assign_grade("English", 88)
print(student.get_average())  # 91.5
```

---
