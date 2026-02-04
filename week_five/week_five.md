# Classes & Objects — Object-Oriented Programming in Python

## Table of Contents
1. What is a Class?
2. What is an Object?
3. Creating a Class
4. The `__init__` Method (Constructor)
5. Attributes and Methods
6. The `self` Parameter
7. Creating and Using Objects
8. Inheritance
9. Method Overriding
10. Encapsulation
11. Special Methods
12. Exercises

---

## 1. What is a Class?

A **class** is a blueprint or template for creating objects. It defines:
- **Attributes** — data/properties of an object
- **Methods** — functions that describe behavior

**Real-world analogy:**
- Class = Cookie cutter (blueprint)
- Object = Each cookie made from the cutter (instance)

---

## 2. What is an Object?

An **object** is an instance of a class. It's a concrete thing created from the class blueprint.

**Example:**
```
Class: Car (blueprint)
Objects: My car (Toyota), Your car (Honda), Another car (BMW)
```

---

## 3. Creating a Class

### Basic Syntax

```python
class ClassName:
    # attributes and methods go here
    pass
```

### Simple Example

```python
class Dog:
    pass

# Create an object (instance)
my_dog = Dog()
print(my_dog)  # <__main__.Dog object at 0x...>
```

---

## 4. The `__init__` Method (Constructor)

The `__init__` method is called automatically when an object is created. It initializes the object's attributes.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Create objects
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

print(dog1.name)  # Buddy
print(dog2.age)   # 5
```

---

## 5. Attributes and Methods

### Attributes (Data)
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

### Methods (Functions)
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, my name is {self.name}")

    def have_birthday(self):
        self.age += 1
```

---

## 6. The `self` Parameter

`self` refers to the current object. It lets methods access the object's attributes.

```python
class Person:
    def __init__(self, name):
        self.name = name  # self.name is an attribute of THIS object

    def introduce(self):
        print(f"I am {self.name}")  # self refers to the object

person = Person("Alice")
person.introduce()  # Output: I am Alice
```

---

## 7. Creating and Using Objects

```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

    def describe(self):
        return f"{self.year} {self.brand} {self.model}"

    def age_of_car(self, current_year):
        return current_year - self.year

# Create objects
car1 = Car("Toyota", "Corolla", 2020)
car2 = Car("Honda", "Civic", 2022)

# Use attributes
print(car1.brand)  # Toyota

# Use methods
print(car1.describe())      # 2020 Toyota Corolla
print(car1.age_of_car(2025))  # 5
```

---

## 8. Inheritance

**Inheritance** allows a child class to inherit attributes and methods from a parent class.

### Syntax

```python
class ParentClass:
    # parent attributes and methods
    pass

class ChildClass(ParentClass):
    # child can use parent's methods
    # and add its own
    pass
```

### Example

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

# Create objects
dog = Dog("Buddy")
cat = Cat("Whiskers")

dog.speak()  # Buddy barks: Woof!
cat.speak()  # Whiskers meows: Meow!
```

---

## 9. Method Overriding

**Method overriding** means a child class provides a different implementation of a method from the parent class.

```python
class Vehicle:
    def start(self):
        print("Vehicle started")

class Car(Vehicle):
    def start(self):
        print("Car engine started")

class Bike(Vehicle):
    def start(self):
        print("Bike engine started")

# Usage
car = Car()
car.start()  # Car engine started

bike = Bike()
bike.start()  # Bike engine started
```

---

## 10. Using `super()` to Call Parent Methods

Use `super()` to call methods from the parent class.

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} speaks")

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Call parent's __init__
        self.breed = breed

    def speak(self):
        super().speak()  # Call parent's speak()
        print(f"{self.name} barks!")

dog = Dog("Max", "Golden Retriever")
dog.speak()
# Output:
# Max speaks
# Max barks!
```

---

## 11. Encapsulation (Private Attributes)

Use `_` or `__` prefix to indicate private attributes (not meant to be accessed directly).

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def withdraw(self, amount):
        if amount > 0 and amount <= self.__balance:
            self.__balance -= amount

    def get_balance(self):
        return self.__balance

account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # 1500
account.withdraw(200)
print(account.get_balance())  # 1300
```

---

## 12. Special Methods

Special methods (dunder methods) start and end with `__`.

### `__str__` — String representation
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"

person = Person("Alice", 30)
print(person)  # Person(name=Alice, age=30)
```

---

### `__repr__` — Official representation
```python
class Person:
    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

person = Person("Bob", 25)
print(repr(person))  # Person('Bob', 25)
```

---

### `__len__` — Custom length
```python
class MyList:
    def __init__(self, items):
        self.items = items

    def __len__(self):
        return len(self.items)

my_list = MyList([1, 2, 3, 4, 5])
print(len(my_list))  # 5
```

---

### `__add__` — Custom addition
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

## 13. `isinstance()` Check

Check if an object is an instance of a class.

```python
class Dog:
    pass

class Cat:
    pass

dog = Dog()
cat = Cat()

print(isinstance(dog, Dog))   # True
print(isinstance(dog, Cat))   # False
print(isinstance(cat, Cat))   # True
```

---

## 14. Class Variables vs Instance Variables

### Instance Variables (per object)
```python
class Person:
    def __init__(self, name):
        self.name = name  # Instance variable

person1 = Person("Alice")
person2 = Person("Bob")

print(person1.name)  # Alice
print(person2.name)  # Bob
```

### Class Variables (shared by all objects)
```python
class Person:
    species = "Homo sapiens"  # Class variable

    def __init__(self, name):
        self.name = name  # Instance variable

person1 = Person("Alice")
person2 = Person("Bob")

print(person1.species)  # Homo sapiens
print(person2.species)  # Homo sapiens
print(Person.species)   # Homo sapiens (access via class)
```

---

## Summary

| Concept | Example |
|---------|---------|
| Class definition | `class Dog:` |
| Create object | `dog = Dog()` |
| `__init__` method | `def __init__(self, name):` |
| Instance variable | `self.name = name` |
| Method | `def bark(self):` |
| Inheritance | `class Puppy(Dog):` |
| Override method | `def bark(self):` in child class |
| Private attribute | `self.__private` |
| Special method | `def __str__(self):` |

---
