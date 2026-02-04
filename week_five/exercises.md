# Exercises: Classes & Objects

## Beginner Exercises

1. Create a `Person` class with attributes `name` and `age`. Create two objects and print their attributes.

2. Create a `Book` class with `__init__` method that takes `title` and `author`. Create a book object.

3. Create a `Circle` class that takes `radius` as input. Add a method to calculate the area (π × r²).

4. Create a `Rectangle` class with `width` and `height`. Add a method to calculate the area.

5. Create a `Student` class with `name`, `grade`, and `score` attributes.

6. Create a `BankAccount` class with `balance` attribute. Add a method to check the balance.

7. Create a `Car` class with `brand`, `model`, and `year`. Add a method `describe()` that returns a description.

8. Create a `Temperature` class that converts between Celsius and Fahrenheit.

9. Create a `Movie` class with `title`, `director`, and `rating`.

10. Create a `Bicycle` class with `brand` and `speed` attributes.

---

## Intermediate Exercises

11. Create a `Dog` class with `name`, `breed`, and `age`. Add a method `bark()` that prints a message.

12. Create a `Calculator` class with methods `add()`, `subtract()`, `multiply()`, and `divide()`.

13. Create a `Person` class with `__init__` that initializes `first_name`, `last_name`, and `age`. Add a method `full_name()` that returns the full name.

14. Create a `BankAccount` class with methods `deposit()` and `withdraw()`. Ensure balance doesn't go negative.

15. Create an `Employee` class with `name`, `salary`, and `department`. Add a method `get_info()` that returns employee details.

16. Create a `Student` class with `name` and `grades` (list). Add a method to calculate the average grade.

17. Create a `Library` class that stores a list of books. Add methods to add and remove books.

18. Create a `Weather` class with `temperature` and `condition`. Add a method to describe the weather.

19. Create a `Counter` class with methods to increment and decrement a count.

20. Create a `ShoppingCart` class with items. Add methods to add, remove, and calculate the total price.

---

## Inheritance & Polymorphism Exercises

21. Create an `Animal` class with a `speak()` method. Create `Dog` and `Cat` classes that inherit from `Animal` and override `speak()`.

22. Create a `Vehicle` class with `brand` and `year`. Create `Car` and `Motorcycle` classes that inherit from `Vehicle`.

23. Create a `Shape` class with an `area()` method. Create `Square` and `Triangle` classes that calculate their areas.

24. Create a `Person` class. Create `Student` and `Teacher` classes that inherit from `Person`. Add methods to each.

25. Create a `Bird` class with a `fly()` method. Create `Eagle` and `Penguin` classes. Override `fly()` in `Penguin` to return "Penguins can't fly".

26. Create a `Product` class. Create `Book` and `Electronics` classes that inherit from `Product` and override a method.

27. Create a `Transport` class with `speed`. Create `Car`, `Train`, and `Plane` classes that inherit and add specific methods.

28. Create a `Player` class. Create `Warrior` and `Mage` classes that inherit and override an `attack()` method.

29. Create a `BankAccount` class. Create `SavingsAccount` and `CheckingAccount` that inherit and override methods.

30. Create a `Furniture` class. Create `Chair`, `Table`, and `Bed` classes that inherit and have different prices.

---

## Advanced Exercises

31. Create a `User` class with private `__password` attribute. Add methods to set and verify the password (without exposing it).

32. Create a `Rectangle` class with `__init__`, `__str__()`, and `__repr__()` methods.

33. Create a `Vector` class with `x` and `y` coordinates. Implement `__add__()` to add two vectors.

34. Create a `Person` class with `__init__`, `__str__()`, and a method `__repr__()`.

35. Create a `BankAccount` class with `__str__()` that displays account info nicely.

36. Create a `Box` class with `__init__` and `__len__()` that returns the volume.

37. Create a `ShoppingCart` class with `__add__()` to merge two carts.

38. Create a `Point` class representing (x, y). Implement `__add__()` and `__sub__()`.

39. Create a `Money` class with amount and currency. Implement `__add__()` and `__str__()`.

40. Create a `Game` class that uses a class variable to track the number of games played.

41. Create a `Student` class with a class variable for school name. All students share the same school.

42. Create a `Company` class with a class variable for company name and instance variables for employees.

43. Create a `BankAccount` class using super() with a parent `FinancialAccount` class.

44. Create an `Animal` class and `Dog` class that uses `super()` in its methods.

45. Create a `MusicPlayer` class that can play, pause, and stop music.

46. Create a `FileHandler` class to read and write files using class methods.

47. Create a `Deck` class with a list of cards. Add a method to shuffle and deal cards.

48. Create a `Game` class that uses multiple objects (players, cards, etc.) interacting together.

49. Create a system of classes: `Company`, `Employee`, and `Department` that work together.

50. Create a small game with classes: `Player`, `Enemy`, and `Game` that manages the interaction.

---

## Project-Based Exercises

### Project 1: Bank Management System
- Create `Account` class (account number, balance)
- Create `SavingsAccount` and `CheckingAccount` subclasses
- Implement deposit, withdraw, and interest calculation
- Add transaction history

### Project 2: Student Management System
- Create `School` class with a list of students
- Create `Student` class with name, ID, grades
- Create `Teacher` class with name and subjects
- Add methods to enroll students, assign grades

### Project 3: E-commerce System
- Create `Product` class
- Create `ShoppingCart` class
- Create `Order` class
- Implement calculating totals and managing inventory

### Project 4: Zoo Management
- Create `Animal` class with various subclasses
- Create `Zoo` class that manages animals
- Implement feeding, care, and information display

### Project 5: Library Management System
- Create `Book` class with title, author, ISBN
- Create `Member` class
- Create `Library` class that manages books and members
- Implement borrowing and returning books

---
