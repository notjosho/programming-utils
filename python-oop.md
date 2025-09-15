# Python Object-Oriented Programming (OOP)

Object-Oriented Programming is a programming paradigm that organizes code into objects and classes, modeling real-world entities and their interactions.

## What is OOP?

**Object-Oriented Programming** is a way of organizing code that groups related data (attributes) and functions (methods) together into objects. Instead of writing procedural code, you create blueprints (classes) that define how objects should behave.

**Key Benefits:**
- **Modularity**: Code is organized into separate, reusable components
- **Reusability**: Classes can be used multiple times and extended
- **Maintainability**: Changes to one class don't affect others
- **Real-world modeling**: Code structure mirrors real-world relationships

## Classes and Objects

**Class**: A blueprint or template that defines the structure and behavior of objects.
**Object**: An instance of a class - a specific implementation with actual data.

Think of a class like a cookie cutter and objects like the actual cookies made from it.

### Basic Class Definition
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, I'm {self.name}"

# Creating objects
person1 = Person("Alice", 25)
print(person1.greet())  # Hello, I'm Alice
```

### Class Attributes vs Instance Attributes

**Attributes** are the data/variables that belong to a class or object. They store the state and characteristics of the object.

**Class Attributes**: Shared by all instances of the class
**Instance Attributes**: Unique to each individual object

```python
class Dog:
    species = "Canis lupus"  # Class attribute

    def __init__(self, name, breed):
        self.name = name      # Instance attribute
        self.breed = breed    # Instance attribute
```

### Methods

**Methods** are functions that belong to a class and define what objects can do. They operate on the object's data (attributes).

```python
class Calculator:
    def __init__(self, value=0):
        self.value = value

    def add(self, number):      # Instance method
        self.value += number
        return self

    def get_result(self):       # Instance method
        return self.value
```

### Constructors

**Constructor** (`__init__`): A special method that automatically runs when an object is created. It initializes the object's attributes.

```python
class Person:
    def __init__(self, name, age):  # Constructor
        self.name = name            # Initialize attributes
        self.age = age

# When you create an object, __init__ runs automatically
person = Person("Alice", 25)  # Constructor is called here
```

## The Four Pillars of OOP

The four fundamental principles that define object-oriented programming:

### 1. Encapsulation
**Definition**: Bundling data and methods together while controlling access to them.
**Purpose**: Protects data integrity and hides internal implementation details.
```python
class BankAccount:
    def __init__(self, balance=0):
        self._balance = balance  # Protected attribute
        self.__pin = 1234       # Private attribute

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount

    def get_balance(self):
        return self._balance
```

### 2. Inheritance
**Definition**: Creating new classes based on existing classes, inheriting their attributes and methods.
**Purpose**: Promotes code reuse and establishes hierarchical relationships.
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Cat(Animal):  # Cat inherits from Animal
    def speak(self):
        return f"{self.name} says Meow!"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"
```

### 3. Polymorphism
**Definition**: The ability for different classes to be treated as instances of the same type through a common interface.
**Purpose**: Allows the same code to work with objects of different types.
```python
def animal_sound(animal):
    return animal.speak()  # Same method, different behavior

cat = Cat("Whiskers")
dog = Dog("Buddy")

print(animal_sound(cat))  # Whiskers says Meow!
print(animal_sound(dog))  # Buddy says Woof!
```

### 4. Abstraction
**Definition**: Hiding complex implementation details while exposing only essential features.
**Purpose**: Simplifies interfaces and reduces complexity for users of the class.
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)
```

## Resources

- [Python Classes Documentation](https://docs.python.org/3/tutorial/classes.html)
- [Real Python OOP Tutorial](https://realpython.com/python3-object-oriented-programming/)
- [Python OOP Concepts](https://www.programiz.com/python-programming/object-oriented-programming)