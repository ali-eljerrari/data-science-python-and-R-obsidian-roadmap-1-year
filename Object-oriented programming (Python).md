
---


Object-Oriented Programming (OOP) is a programming paradigm that uses "objects" to design software. Python is an object-oriented language from the ground up, which makes it a great language to learn OOP concepts.

## Table of Contents

1. [Introduction to Object-Oriented Programming](#1-introduction)
2. [Classes and Objects](#2-classes-and-objects)
3. [Attributes and Methods](#3-attributes-and-methods)
4. [Constructors (`__init__` method)](#4-constructors)
5. [Encapsulation](#5-encapsulation)
6. [Inheritance](#6-inheritance)
7. [Polymorphism](#7-polymorphism)
8. [Abstraction](#8-abstraction)
9. [Magic Methods and Operator Overloading](#9-magic-methods)
10. [Class and Static Methods](#10-class-static-methods)
11. [Class Variables vs Instance Variables](#11-class-instance-variables)
12. [Property Decorators (`@property`)](#12-property-decorators)
13. [Method Resolution Order (MRO)](#13-mro)
14. [Multiple Inheritance](#14-multiple-inheritance)
15. [Abstract Classes and Interfaces](#15-abstract-classes)
16. [Namespaces and Scope](#16-namespaces-scope)
17. [Best Practices](#17-best-practices)
18. [Conclusion](#18-conclusion)

---

<a name="1-introduction"></a>
## 1. Introduction to Object-Oriented Programming

OOP revolves around the concept of "objects," which can contain data and code to manipulate that data. The data and code are structured together in a way that models real-world entities.

**Key Concepts:**

- **Class:** A blueprint for creating objects.
- **Object:** An instance of a class.
- **Method:** A function defined within a class.
- **Attribute:** A variable bound to an instance of a class.

---

<a name="2-classes-and-objects"></a>
## 2. Classes and Objects

### 2.1 Defining a Class

```python
class Person:
    pass  # An empty class
```

### 2.2 Creating an Object (Instance)

```python
person1 = Person()
```

**Example with Attributes:**

```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age

# Creating instances
person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

print(person1.name)  # Output: Alice
print(person2.age)   # Output: 25
```

---

<a name="3-attributes-and-methods"></a>
## 3. Attributes and Methods

### 3.1 Attributes

Attributes are variables that belong to an object or class.

- **Instance Attributes:** Specific to an instance.
- **Class Attributes:** Shared across all instances.

### 3.2 Methods

Methods are functions defined inside a class.

```python
class Calculator:
    def add(self, x, y):
        return x + y

calc = Calculator()
result = calc.add(5, 3)
print(result)  # Output: 8
```

**Note:** The first parameter `self` refers to the instance calling the method.

---

<a name="4-constructors"></a>
## 4. Constructors (`__init__` method)

The `__init__` method initializes an object's state when it's created.

```python
class Employee:
    def __init__(self, name, position):
        self.name = name
        self.position = position

emp = Employee("Charlie", "Developer")
print(emp.name)       # Output: Charlie
print(emp.position)   # Output: Developer
```

---

<a name="5-encapsulation"></a>
## 5. Encapsulation

Encapsulation is the bundling of data and methods that operate on that data within one unit, e.g., a class.

### 5.1 Access Modifiers

- **Public:** Accessible from anywhere.
- **Protected:** Prefix with a single underscore `_`. Should not be accessed directly.
- **Private:** Prefix with double underscores `__`. Name mangling occurs.

**Example:**

```python
class Robot:
    def __init__(self):
        self.__serial_number = "12345"  # Private attribute

    def get_serial_number(self):
        return self.__serial_number

robot = Robot()
print(robot.get_serial_number())  # Output: 12345
# print(robot.__serial_number)    # AttributeError
```

---

<a name="6-inheritance"></a>
## 6. Inheritance

Inheritance allows a class to inherit attributes and methods from another class.

### 6.1 Single Inheritance

```python
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

dog = Dog()
dog.eat()   # Output: Eating
dog.bark()  # Output: Barking
```

### 6.2 Overriding Methods

```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Cat(Animal):
    def speak(self):
        print("Meow")

cat = Cat()
cat.speak()  # Output: Meow
```

---

<a name="7-polymorphism"></a>
## 7. Polymorphism

Polymorphism allows methods to do different things based on the object it is acting upon.

**Example with Method Overriding:**

```python
class Shape:
    def area(self):
        pass

class Square(Shape):
    def __init__(self, side):
        self.side = side
    def area(self):
        return self.side ** 2

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return 3.14 * self.radius ** 2

shapes = [Square(4), Circle(3)]
for shape in shapes:
    print(shape.area())
# Output:
# 16
# 28.26
```

---

<a name="8-abstraction"></a>
## 8. Abstraction

Abstraction means hiding complex reality while exposing only the necessary parts.

In Python, abstraction can be achieved using abstract base classes (ABCs) from the `abc` module.

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start_engine(self):
        pass

class Car(Vehicle):
    def start_engine(self):
        print("Engine started")

# vehicle = Vehicle()      # Error: Can't instantiate abstract class
car = Car()
car.start_engine()          # Output: Engine started
```

---

<a name="9-magic-methods"></a>
## 9. Magic Methods and Operator Overloading

Magic methods are special methods with double underscores that allow objects to implement certain behaviors.

### 9.1 Common Magic Methods

- `__str__(self)`: Defines behavior for `str()` and `print()`
- `__add__(self, other)`: Defines behavior for addition `+`
- `__len__(self)`: Defines behavior for `len()`

**Example of `__str__` and `__add__`:**

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point ({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

p1 = Point(2, 3)
p2 = Point(5, 7)
print(p1)        # Output: Point (2, 3)
p3 = p1 + p2
print(p3)        # Output: Point (7, 10)
```

---

<a name="10-class-static-methods"></a>
## 10. Class and Static Methods

### 10.1 Class Methods

- Use the `@classmethod` decorator.
- Receive the class (`cls`) as the first argument.

```python
class MyClass:
    count = 0

    @classmethod
    def increment_count(cls):
        cls.count += 1

MyClass.increment_count()
print(MyClass.count)  # Output: 1
```

### 10.2 Static Methods

- Use the `@staticmethod` decorator.
- Do not receive `self` or `cls`.

```python
class Utility:
    @staticmethod
    def add(x, y):
        return x + y

result = Utility.add(5, 7)
print(result)  # Output: 12
```

---

<a name="11-class-instance-variables"></a>
## 11. Class Variables vs Instance Variables

- **Class Variables:** Shared across all instances.
- **Instance Variables:** Unique to each instance.

```python
class Employee:
    company_name = "TechCorp"  # Class variable

    def __init__(self, name):
        self.name = name       # Instance variable

emp1 = Employee("Alice")
emp2 = Employee("Bob")
print(emp1.company_name)  # Output: TechCorp
print(emp2.company_name)  # Output: TechCorp

Employee.company_name = "NewTech"
print(emp1.company_name)  # Output: NewTech
print(emp2.company_name)  # Output: NewTech
```

---

<a name="12-property-decorators"></a>
## 12. Property Decorators (`@property`)

Property decorators allow you to access methods like attributes.

```python
class Celsius:
    def __init__(self, temperature=0):
        self._temperature = temperature

    @property
    def temperature(self):
        print("Getting value")
        return self._temperature

    @temperature.setter
    def temperature(self, value):
        print("Setting value")
        if value < -273.15:
            raise ValueError("Temperature below -273.15 is not possible")
        self._temperature = value

temp = Celsius()
temp.temperature = 37
print(temp.temperature)
# Output:
# Setting value
# Getting value
# 37
```

---

<a name="13-mro"></a>
## 13. Method Resolution Order (MRO)

MRO is the order in which base classes are searched for a method during inheritance.

```python
class A:
    def process(self):
        print("Process in A")

class B(A):
    pass

class C(A):
    def process(self):
        print("Process in C")

class D(B, C):
    pass

d = D()
d.process()
# Output: Process in C

print(D.__mro__)
# Output: (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
```

---

<a name="14-multiple-inheritance"></a>
## 14. Multiple Inheritance

A class can inherit from multiple classes.

```python
class Flyable:
    def fly(self):
        print("Flying")

class Swimmable:
    def swim(self):
        print("Swimming")

class Duck(Flyable, Swimmable):
    pass

duck = Duck()
duck.fly()   # Output: Flying
duck.swim()  # Output: Swimming
```

---

<a name="15-abstract-classes"></a>
## 15. Abstract Classes and Interfaces

Abstract classes cannot be instantiated and are used to define interfaces.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

rect = Rectangle(5, 10)
print(rect.area())  # Output: 50
```

---

<a name="16-namespaces-scope"></a>
## 16. Namespaces and Scope

- **Local Scope:** Variables defined within a function.
- **Global Scope:** Variables defined at the top level.
- **Class/Object Scope:** Variables within a class or object.

```python
x = "global"

def outer():
    x = "outer"
    def inner():
        nonlocal x
        x = "inner"
        print("Inner x:", x)
    inner()
    print("Outer x:", x)

outer()
print("Global x:", x)
# Output:
# Inner x: inner
# Outer x: inner
# Global x: global
```

---

<a name="17-best-practices"></a>
## 17. Best Practices

- **Use Meaningful Names:** Class and method names should be descriptive.
- **Follow PEP 8 Guidelines:** For naming conventions and code style.
- **Use Properties Instead of Getters and Setters:** Utilize `@property` decorators.
- **Prefer Composition Over Inheritance:** When appropriate.
- **Avoid Multiple Inheritance if Possible:** Can lead to complex code.

---

<a name="18-conclusion"></a>
## 18. Conclusion

Object-Oriented Programming is a powerful paradigm that helps in creating modular, reusable, and organized code. Python's support for OOP makes it easier to implement complex systems with clear structures.

---

# Object-Oriented Programming in Python Exam Answers

Below is a 30-question multiple-choice exam on Object-Oriented Programming (OOP) in Python. Each question has four options, and the correct answer is indicated with a checked checkbox. Explanations are provided for clarity.

---

## **Multiple Choice Questions**

**1.** What is the term for a blueprint or template in OOP from which objects are created?

- [ ] a) Object
- [x] b) Class
- [ ] c) Method
- [ ] d) Module

**Explanation:** A **class** is a blueprint for creating objects in OOP.

---

**2.** Which method is called when an object is created in Python?

- [ ] a) `__del__`
- [x] b) `__init__`
- [ ] c) `__new__`
- [ ] d) `__start__`

**Explanation:** The `__init__` method is the constructor in Python and is called when an object is instantiated.

---

**3.** In Python, what is the term for functions defined inside a class?

- [ ] a) Attributes
- [ ] b) Objects
- [x] c) Methods
- [ ] d) Variables

**Explanation:** Functions defined inside a class are called **methods**.

---

**4.** What is the output of the following code?

```python
class MyClass:
    class_var = 10

obj1 = MyClass()
obj2 = MyClass()
MyClass.class_var = 20
print(obj1.class_var)
```

- [ ] a) 10
- [x] b) 20
- [ ] c) Error
- [ ] d) None

**Explanation:** `class_var` is a class variable shared among all instances. Changing it via the class affects all instances.

---

**5.** Which of the following is used to indicate that a method belongs to the class rather than an instance?

- [ ] a) `@staticmethod`
- [x] b) `@classmethod`
- [ ] c) `@property`
- [ ] d) `@private`

**Explanation:** `@classmethod` is used to define a method that belongs to the class.

---

**6.** What does encapsulation in OOP refer to?

- [ ] a) Inheriting attributes from a parent class
- [x] b) Bundling data and methods operating on that data
- [ ] c) Modifying existing code
- [ ] d) Hiding the superclass methods

**Explanation:** Encapsulation is the bundling of data and methods that operate on that data.

---

**7.** Which keyword is used to inherit from a parent class in Python?

- [ ] a) `inherits`
- [x] b) `class SubClass(ParentClass):`
- [ ] c) `extends`
- [ ] d) `super`

**Explanation:** Inheritance is implemented by specifying the parent class in parentheses after the subclass name.

---

**8.** What is method overriding?

- [ ] a) Changing the method signature in a subclass
- [ ] b) Creating multiple methods with the same name in a class
- [x] c) Redefining a parent class's method in a subclass
- [ ] d) None of the above

**Explanation:** Method overriding allows a subclass to provide a specific implementation of a method already defined in its superclass.

---

**9.** What will be the output of the following code?

```python
class A:
    def display(self):
        print("A")

class B(A):
    pass

obj = B()
obj.display()
```

- [x] a) A
- [ ] b) B
- [ ] c) Error
- [ ] d) None

**Explanation:** Class `B` inherits from `A` but doesn't override `display()`, so it uses `A`'s method.

---

**10.** What is polymorphism in OOP?

- [ ] a) The ability of a class to inherit from multiple classes
- [ ] b) The ability of a function to change its behavior depending on the object
- [x] c) The ability to take many forms; methods behaving differently based on the object
- [ ] d) Encapsulating multiple methods into one

**Explanation:** Polymorphism allows methods to perform differently based on the object invoking them.

---

**11.** Which method would you override to change the string representation of an object?

- [x] a) `__str__`
- [ ] b) `__repr__`
- [ ] c) `__init__`
- [ ] d) `__del__`

**Explanation:** The `__str__` method defines the human-readable string representation of an object.

---

**12.** What does the `super()` function do in Python?

- [ ] a) Returns the superclass object
- [x] b) Allows you to call methods of the superclass
- [ ] c) Creates a new class
- [ ] d) Initializes the object

**Explanation:** `super()` is used to call methods from the superclass in a subclass.

---

**13.** In the context of OOP, what is an abstract class?

- [ ] a) A class with no methods
- [ ] b) A class that cannot be extended
- [x] c) A class that cannot be instantiated and may contain abstract methods
- [ ] d) A class with only static methods

**Explanation:** An abstract class cannot be instantiated and often includes abstract methods that subclasses must implement.

---

**14.** Which module provides the infrastructure for defining Abstract Base Classes (ABCs) in Python?

- [ ] a) `collections`
- [ ] b) `abc`
- [x] c) `abc` (Abstract Base Classes)
- [ ] d) `abstract`

**Explanation:** The `abc` module provides the tools for creating abstract base classes.

---

**15.** What is the output of the following code?

```python
class MyClass:
    def __init__(self):
        self.__hidden = "secret"

obj = MyClass()
print(obj.__hidden)
```

- [ ] a) secret
- [ ] b) None
- [ ] c) Error
- [x] d) AttributeError

**Explanation:** Variables prefixed with double underscores are name-mangled and cannot be accessed directly.

---

**16.** How do you declare a static method in a Python class?

- [x] a) Use the `@staticmethod` decorator
- [ ] b) Use the `@classmethod` decorator
- [ ] c) Define the method outside the class
- [ ] d) Prefix the method name with `static_`

**Explanation:** `@staticmethod` decorator is used to define a static method.

---

**17.** What is the Method Resolution Order (MRO) in Python?

- [ ] a) The order in which methods are overridden
- [x] b) The order in which base classes are searched for a method
- [ ] c) The order in which methods are defined in a class
- [ ] d) The order in which objects are instantiated

**Explanation:** MRO defines the order in which base classes are searched when looking for a method.

---

**18.** What is multiple inheritance?

- [ ] a) Inheriting from the same class multiple times
- [ ] b) A class inheriting from itself
- [x] c) A class inheriting from more than one base class
- [ ] d) None of the above

**Explanation:** Multiple inheritance allows a class to inherit from multiple base classes.

---

**19.** Which of the following is NOT a benefit of using OOP?

- [ ] a) Encapsulation
- [ ] b) Code reusability
- [ ] c) Modularity
- [x] d) Faster execution time

**Explanation:** OOP provides organizational benefits but may not necessarily result in faster execution time.

---

**20.** What does the `@property` decorator do?

- [ ] a) Defines a method as a class method
- [ ] b) Makes an attribute private
- [x] c) Allows a method to be accessed like an attribute
- [ ] d) Defines a method as static

**Explanation:** The `@property` decorator allows you to access a method like an attribute.

---

**21.** In Python, what is name mangling?

- [ ] a) The process of encoding method names
- [x] b) The transformation of private attribute names to avoid naming conflicts
- [ ] c) Compressing variable names
- [ ] d) Encrypting class names

**Explanation:** Name mangling is used to prevent naming conflicts in subclasses.

---

**22.** What will be the output of the following code?

```python
class A:
    def __init__(self):
        self.var = 1

class B(A):
    def __init__(self):
        super().__init__()
        self.var = 2

obj = B()
print(obj.var)
```

- [ ] a) 1
- [x] b) 2
- [ ] c) Error
- [ ] d) None

**Explanation:** The `B` class overrides `var` after calling `super().__init__()`.

---

**23.** Which of the following best describes composition in OOP?

- [ ] a) A class inheriting from another class
- [x] b) A class containing an instance of another class
- [ ] c) Overriding methods from a superclass
- [ ] d) Implementing abstract methods

**Explanation:** Composition involves building classes that contain instances of other classes.

---

**24.** What is the main purpose of the `__del__` method in a class?

- [x] a) It acts as a destructor and is called when an object is about to be destroyed
- [ ] b) It initializes a new object
- [ ] c) It deletes an attribute
- [ ] d) It duplicates an object

**Explanation:** The `__del__` method is called when an object is about to be destroyed.

---

**25.** Which built-in function can be used to check if an object is an instance of a particular class?

- [ ] a) `type()`
- [x] b) `isinstance()`
- [ ] c) `issubclass()`
- [ ] d) `id()`

**Explanation:** `isinstance(object, class)` checks if an object is an instance of a class or its subclass.

---

**26.** In the context of inheritance, what does the term "overriding" mean?

- [ ] a) A subclass adds new methods
- [x] b) A subclass provides a specific implementation for a method already defined in its superclass
- [ ] c) A superclass changes its methods
- [ ] d) Methods are shared between classes

**Explanation:** Overriding means redefining a method in a subclass.

---

**27.** How can you prevent a class from being inherited in Python?

- [ ] a) By declaring it as `final`
- [ ] b) By making it private
- [x] c) Python does not provide a way to prevent inheritance
- [ ] d) By raising an error in the constructor

**Explanation:** Python does not have a built-in way to prevent a class from being inherited.

---

**28.** What is the output of the following code?

```python
class Test:
    def __init__(self):
        self.x = 0

    def increment(self):
        self.x += 1

obj1 = Test()
obj2 = Test()
obj1.increment()
print(obj1.x, obj2.x)
```

- [ ] a) 1 1
- [x] b) 1 0
- [ ] c) 0 1
- [ ] d) 0 0

**Explanation:** `obj1` and `obj2` are separate instances; incrementing `obj1.x` does not affect `obj2.x`.

---

**29.** Which of the following statements about class variables is TRUE?

- [ ] a) Class variables are unique to each instance of the class.
- [x] b) Class variables are shared among all instances of the class.
- [ ] c) Class variables cannot be changed.
- [ ] d) Class variables are defined inside methods.

**Explanation:** Class variables are shared across all instances of a class.

---

**30.** What does the `__name__ == "__main__"` check do in a Python script?

- [ ] a) Checks if a class is the main class
- [x] b) Determines if the script is being run directly or being imported
- [ ] c) Checks for the main method in a class
- [ ] d) Initializes the main object

**Explanation:** This check allows code to run only if the script is executed directly.

---

