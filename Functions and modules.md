# Functions and Modules in Python

Understanding **functions** and **modules** is essential for writing organized, reusable, and efficient code in Python. Functions allow you to encapsulate code for reuse, while modules enable you to organize functions, classes, and variables into separate files.

---

## **1. Functions**

A function is a block of organized, reusable code that performs a single, related action. Functions provide better modularity for your application and a high degree of code reusability.

### **1.1 Defining Functions**

In Python, you define a function using the `def` keyword, followed by the function name and parentheses `()`.

**Syntax:**

```python
def function_name(parameters):
    """Docstring describing the function."""
    # Function body
    return [expression]
```

- **`function_name`**: The name of the function.
- **`parameters`**: Optional. A comma-separated list of parameters (arguments) that the function accepts.
- **`return`**: Optional. The value that the function returns to the caller.

**Example:**

```python
def greet(name):
    """Greets a person with the given name."""
    print(f"Hello, {name}!")
```

**Usage:**

```python
greet("Alice")  # Output: Hello, Alice!
```

### **1.2 Calling Functions**

To execute a function, you "call" it by using its name followed by parentheses, including any required arguments.

**Example:**

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # Output: 8
```

### **1.3 Function Parameters**

Functions can accept parameters, which allow you to pass data into functions.

#### **1.3.1 Positional Arguments**

Arguments passed to functions in the order they are defined.

**Example:**

```python
def multiply(a, b):
    return a * b

print(multiply(2, 3))  # Output: 6
```

#### **1.3.2 Keyword Arguments**

Arguments passed to functions with parameter names, allowing you to skip or reorder them.

**Example:**

```python
def introduce(name, age):
    print(f"My name is {name} and I'm {age} years old.")

introduce(age=25, name="Bob")  # Output: My name is Bob and I'm 25 years old.
```

#### **1.3.3 Default Parameters**

Parameters that have default values if no argument is provided.

**Example:**

```python
def greet(name="Guest"):
    print(f"Welcome, {name}!")

greet()            # Output: Welcome, Guest!
greet("Charlie")   # Output: Welcome, Charlie!
```

#### **1.3.4 Variable-length Arguments**

- **`*args`**: Allows you to pass a variable number of positional arguments to a function.
  
  **Example:**

  ```python
  def sum_numbers(*args):
      total = 0
      for num in args:
          total += num
      return total

  print(sum_numbers(1, 2, 3))      # Output: 6
  print(sum_numbers(4, 5, 6, 7))   # Output: 22
  ```

- **`**kwargs`**: Allows you to pass a variable number of keyword arguments.

  **Example:**

  ```python
  def print_info(**kwargs):
      for key, value in kwargs.items():
          print(f"{key}: {value}")

  print_info(name="Alice", age=30, city="New York")
  ```

  **Output:**

  ```
  name: Alice
  age: 30
  city: New York
  ```

### **1.4 Return Statement**

The `return` statement is used to exit a function and return a value to the caller.

**Example:**

```python
def square(number):
    return number ** 2

result = square(4)
print(result)  # Output: 16
```

If no `return` statement is used, the function returns `None` by default.

### **1.5 Docstrings**

Docstrings are string literals that appear right after the function definition and are used for documentation.

**Example:**

```python
def multiply(a, b):
    """Returns the product of a and b."""
    return a * b
```

You can access the docstring using the `__doc__` attribute.

```python
print(multiply.__doc__)  # Output: Returns the product of a and b.
```

### **1.6 Scope of Variables**

Variables defined inside a function are **local** to that function. Variables defined outside are **global**.

**Example:**

```python
x = 10  # Global variable

def func():
    x = 5  # Local variable
    print("Inside function:", x)

func()  # Output: Inside function: 5
print("Outside function:", x)  # Output: Outside function: 10
```

To modify a global variable inside a function, use the `global` keyword.

```python
x = 10

def modify_global():
    global x
    x = 5

modify_global()
print(x)  # Output: 5
```

### **1.7 Lambda Functions**

Anonymous functions defined using the `lambda` keyword. Useful for simple, single-expression functions.

**Syntax:**

```python
lambda arguments: expression
```

**Example:**

```python
square = lambda x: x ** 2
print(square(5))  # Output: 25
```

**Using with `map()`, `filter()`, and `sorted()` functions:**

```python
numbers = [1, 2, 3, 4, 5]

# Using map to square numbers
squared_numbers = list(map(lambda x: x ** 2, numbers))
print(squared_numbers)  # Output: [1, 4, 9, 16, 25]

# Using filter to get even numbers
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [2, 4]
```

---

## **2. Modules**

A module is a file containing Python definitions and statements. Modules help you organize your code logically.

### **2.1 Creating Modules**

To create a module, simply save your code in a file with a `.py` extension.

**Example:**

Create a file named `math_utils.py` with the following content:

```python
# math_utils.py

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b
```

### **2.2 Importing Modules**

Use the `import` statement to include a module in your script.

**Syntax:**

```python
import module_name
```

**Example:**

```python
import math_utils

result = math_utils.add(5, 3)
print(result)  # Output: 8
```

### **2.3 Importing Specific Functions**

You can import specific functions or variables from a module.

**Syntax:**

```python
from module_name import function_name
```

**Example:**

```python
from math_utils import subtract

result = subtract(10, 4)
print(result)  # Output: 6
```

### **2.4 Using Aliases**

You can assign an alias to a module or function using the `as` keyword.

**Example:**

```python
import math_utils as mu

result = mu.add(2, 3)
print(result)  # Output: 5
```

Or for functions:

```python
from math_utils import add as addition

result = addition(7, 8)
print(result)  # Output: 15
```

### **2.5 The `__name__` Variable**

When a module is run directly, the `__name__` variable is set to `'__main__'`. When imported, it is set to the module's name.

**Example in `math_utils.py`:**

```python
def add(a, b):
    return a + b

if __name__ == "__main__":
    # This code will only run when the module is executed directly
    print("Testing add function:")
    print(add(2, 3))  # Output: 5
```

### **2.6 Built-in Modules**

Python comes with a standard library of modules.

#### **2.6.1 The `math` Module**

Provides mathematical functions.

**Example:**

```python
import math

print(math.sqrt(16))       # Output: 4.0
print(math.factorial(5))   # Output: 120
```

#### **2.6.2 The `random` Module**

Generates random numbers.

**Example:**

```python
import random

print(random.randint(1, 10))  # Random integer between 1 and 10
print(random.choice(['apple', 'banana', 'cherry']))  # Randomly selects an item
```

#### **2.6.3 The `datetime` Module**

Handles date and time operations.

**Example:**

```python
import datetime

now = datetime.datetime.now()
print(now)  # Output: Current date and time
```

### **2.7 Installing External Modules**

You can install external modules (packages) using `pip`.

**Command:**

```bash
pip install package_name
```

**Example:**

```bash
pip install requests
```

Then in your Python script:

```python
import requests

response = requests.get('https://api.example.com/data')
print(response.status_code)
```

---

## **3. Packages**

A package is a way of structuring multiple modules by placing them in a folder with a special `__init__.py` file.

### **3.1 Creating a Package**

1. Create a directory with the package name.
2. Add an `__init__.py` file to the directory.
3. Add modules to the package directory.

**Directory Structure:**

```
my_package/
    __init__.py
    module1.py
    module2.py
```

### **3.2 Importing from Packages**

**Example:**

```python
from my_package import module1

module1.some_function()
```

### **3.3 The `__init__.py` File**

The `__init__.py` file can be empty or can include initialization code for the package.

---

## **4. Practical Examples**

### **4.1 Writing a Calculator Module**

**Create `calculator.py`:**

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b != 0:
        return a / b
    else:
        return "Cannot divide by zero"
```

**Use the module in another script:**

```python
import calculator

print(calculator.add(10, 5))        # Output: 15
print(calculator.divide(10, 0))     # Output: Cannot divide by zero
```

### **4.2 Creating a Package for String Utilities**

**Directory Structure:**

```
string_utils/
    __init__.py
    manipulations.py
    validations.py
```

**Content of `manipulations.py`:**

```python
def reverse_string(s):
    return s[::-1]

def to_uppercase(s):
    return s.upper()
```

**Content of `validations.py`:**

```python
def is_palindrome(s):
    return s == s[::-1]

def is_numeric(s):
    return s.isdigit()
```

**Using the Package:**

```python
from string_utils.manipulations import reverse_string
from string_utils.validations import is_palindrome

word = "radar"
print(reverse_string(word))            # Output: radar
print(is_palindrome(word))             # Output: True
```

---

## **5. Best Practices**

- **Keep Functions Focused:** Functions should perform a single task or related group of tasks.
  
- **Use Meaningful Names:** Function and module names should be descriptive.

- **Write Docstrings:** Document your functions and modules for better understanding and maintenance.

- **Avoid Global Variables:** Limit the use of global variables to reduce dependencies.

- **Handle Exceptions:** Anticipate and handle possible errors within your functions.

  ```python
  def divide(a, b):
      try:
          return a / b
      except ZeroDivisionError:
          return "Cannot divide by zero"
  ```

- **Modular Design:** Break down your code into modules and packages to promote reusability and organization.

- **Test Your Functions:** Write test cases to ensure your functions work as expected.

---

## **6. Summary**

- **Functions** allow you to encapsulate code for reuse and better organization.
  
- **Parameters** can be positional, keyword, default, or variable-length.

- **Modules** help you organize related functions and classes into separate files.

- **Importing** modules and functions allows you to use code from other files and libraries.

- **Packages** are directories containing modules, with an `__init__.py` file to initialize them.

- **Built-in Modules** provide a wealth of functionality, and external packages can be installed via `pip`.

---

**By mastering functions and modules, you enhance your ability to write clean, efficient, and maintainable Python code.**

---

# Python Functions and Modules Exam

Please select the correct answer(s) for each question by marking the checkbox next to it.

---

## **1. What keyword is used to define a function in Python?**

- [ ] `func`
- [x] `def`
- [ ] `function`
- [ ] `define`

---

## **2. How do you call a function named `my_function` in Python?**

- [ ] `call my_function()`
- [x] `my_function()`
- [ ] `def my_function()`
- [ ] `execute my_function`

---

## **3. What is the output of the following code?**

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

- [x] `Hello, Alice!`
- [ ] `Hello, name!`
- [ ] `greet`
- [ ] `None`

---

## **4. Which of the following statements is true about function parameters in Python?**

- [ ] All parameters must have default values.
- [x] Parameters can have default values.
- [ ] Functions cannot have parameters.
- [ ] Parameters must always be positional.

---

## **5. What does the `return` statement do in a function?**

- [ ] Outputs a value to the console.
- [x] Exits the function and returns a value to the caller.
- [ ] Defines a function's parameters.
- [ ] Stops the execution of the program.

---

## **6. How do you specify a default parameter value in a function definition?**

- [ ] `def func(a b=2):`
- [x] `def func(a, b=2):`
- [ ] `def func(a=2, b):`
- [ ] `def func(a=2, b=):`

---

## **7. What is a lambda function in Python?**

- [ ] A function that returns multiple values.
- [ ] A function without parameters.
- [x] An anonymous function expressed as a single expression.
- [ ] A function that only accepts keyword arguments.

---

## **8. How do you import a module named `math` in Python?**

- [ ] `include math`
- [x] `import math`
- [ ] `require 'math'`
- [ ] `using math`

---

## **9. Which of the following statements correctly imports only the `sqrt` function from the `math` module?**

- [x] `from math import sqrt`
- [ ] `import sqrt from math`
- [ ] `include math.sqrt`
- [ ] `using math.sqrt`

---

## **10. What will be the output of the following code?**

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)
```

- [ ] `23`
- [x] `5`
- [ ] `add`
- [ ] `None`

---

## **11. How do you give a function an alias upon import?**

- [ ] `import function as alias from module`
- [ ] `import module.function as alias`
- [x] `from module import function as alias`
- [ ] `alias = import module.function`

---

## **12. What is the purpose of the `__init__.py` file in a Python package?**

- [ ] It contains the main function of the package.
- [x] It indicates that the directory is a Python package.
- [ ] It initializes global variables.
- [ ] It stores package metadata.

---

## **13. Which statement is true about local and global variables in Python functions?**

- [ ] Variables defined inside a function are global.
- [ ] Variables defined outside all functions are local.
- [x] Variables defined inside a function are local to that function.
- [ ] All variables are global by default.

---

## **14. How can you access the docstring of a function named `my_function`?**

- [ ] `my_function.docstring`
- [x] `my_function.__doc__`
- [ ] `my_function.__name__`
- [ ] `doc(my_function)`

---

## **15. What will be the output of the following code?**

```python
def func(a, b=5, c=10):
    print(a, b, c)

func(3, c=20)
```

- [x] `3 5 20`
- [ ] `3 20 10`
- [ ] `3 20 5`
- [ ] `3 5 10`

---

## **16. How do you install an external package using `pip`?**

- [ ] `pip get package_name`
- [x] `pip install package_name`
- [ ] `pip import package_name`
- [ ] `pip require package_name`

---

## **17. What is the output of the following code?**

```python
square = lambda x: x ** 2
print(square(4))
```

- [ ] `4`
- [ ] `8`
- [x] `16`
- [ ] `LambdaFunction`

---

## **18. Which of the following is a correct way to create a module in Python?**

- [ ] Create a file named `module.py` containing functions and classes.
- [x] Save Python code in a `.py` file to be used as a module.
- [ ] Use the `create module` command in Python.
- [ ] Modules are built-in and cannot be created by users.

---

## **19. How do you import all functions from a module named `utilities`?**

- [ ] `include utilities.*`
- [ ] `import all from utilities`
- [x] `from utilities import *`
- [ ] `import utilities.all`

---

## **20. What will be the output of the following code?**

```python
def func(a, *args):
    print(a, args)

func(1, 2, 3, 4)
```

- [ ] `1 [2, 3, 4]`
- [x] `1 (2, 3, 4)`
- [ ] `1 2 3 4`
- [ ] `1 (2) (3) (4)`

---

## **21. What does `*args` allow you to do in a function definition?**

- [x] Pass a variable number of positional arguments.
- [ ] Pass a variable number of keyword arguments.
- [ ] Return multiple values.
- [ ] Define default parameter values.

---

## **22. How do you specify a function that accepts any number of keyword arguments?**

- [ ] `def func(**args):`
- [ ] `def func(*kwargs):`
- [x] `def func(**kwargs):`
- [ ] `def func(kwarg):`

---

## **23. What is the purpose of the `global` keyword in Python?**

- [ ] It declares a variable as local.
- [ ] It imports all global variables.
- [x] It allows you to modify a global variable inside a function.
- [ ] It creates a global function.

---

## **24. What will be the output of the following code?**

```python
x = 5

def func():
    x = 10
    print("Inside function:", x)

func()
print("Outside function:", x)
```

- [ ] `Inside function: 5` and `Outside function: 5`
- [x] `Inside function: 10` and `Outside function: 5`
- [ ] `Inside function: 10` and `Outside function: 10`
- [ ] `Inside function: 5` and `Outside function: 10`

---

## **25. Which built-in module would you use to generate random numbers?**

- [ ] `math`
- [x] `random`
- [ ] `datetime`
- [ ] `os`

---

## **26. What does the `__name__ == "__main__"` condition check for?**

- [ ] If the module is imported.
- [ ] If the module has classes.
- [x] If the module is being run directly.
- [ ] If the module has a `main` function.

---

## **27. How do you access a function named `func` from a module named `mod` located inside a package named `pack`?**

- [ ] `import pack.mod.func`
- [x] `from pack.mod import func`
- [ ] `import func from pack.mod`
- [ ] `from mod import func`

---

## **28. What will be the output of the following code?**

```python
def outer():
    x = "local"

    def inner():
        nonlocal x
        x = "nonlocal"
        print("Inner:", x)

    inner()
    print("Outer:", x)

outer()
```

- [ ] `Inner: local` and `Outer: local`
- [x] `Inner: nonlocal` and `Outer: nonlocal`
- [ ] `Inner: nonlocal` and `Outer: local`
- [ ] `NameError`

---

## **29. What is the correct way to handle exceptions that may occur in a function?**

- [ ] Using `try` and `except` blocks inside the function.
- [ ] Letting the exception occur and not handling it.
- [x] Both A and C are correct.
- [ ] Documenting the exception in the docstring.

---

## **30. How do you access the mathematical constant pi using the `math` module?**

- [ ] `math.pi()`
- [x] `math.pi`
- [ ] `pi.math`
- [ ] `math.constant.pi`

---

**Good luck on your exam!**