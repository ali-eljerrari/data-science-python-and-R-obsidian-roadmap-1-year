
---

## **Basic Syntax**

### **1. Comments**

Comments are non-executable lines in your code meant for documentation. Python supports:

- **Single-line comments** using the `#` symbol:

  ```python
  # This is a single-line comment
  print("Hello, World!")  # This prints a greeting
  ```

- **Multi-line comments** using triple quotes `'''` or `"""`:

  ```python
  """
  This is a multi-line comment.
  It can span several lines.
  """
  ```

### **2. Variables and Assignment**

Variables store data values. In Python, you create a variable by assigning it a value:

```python
x = 10          # Integer assignment
y = 3.14        # Float assignment
name = "Alice"  # String assignment
is_active = True  # Boolean assignment
```

- **Variable Naming Rules**:
  - Must start with a letter or underscore (`_`)
  - Can contain letters, digits, and underscores
  - Case-sensitive (`age` and `Age` are different)

### **3. Indentation and Code Blocks**

Python uses indentation to define code blocks, replacing the need for braces `{}` as in other languages.

- **Consistent Indentation**: Use 4 spaces per indentation level.
- **Indentation Errors**: Inconsistent indentation leads to `IndentationError`.

```python
if x > 0:
    print("Positive")
else:
    print("Non-positive")
```

### **4. Statements and Expressions**

- **Statements** perform an action (e.g., assignment, `print`, `if`).
- **Expressions** evaluate to a value (e.g., `2 + 2`, `x * y`).

```python
# Statement
x = 5

# Expression
y = x + 3
```

### **5. Control Flow Statements**

#### **a. Conditional Statements**

Control the flow of execution based on conditions.

- **if Statement**:

  ```python
  if condition:
      # Execute this block if condition is True
  ```

- **if-else Statement**:

  ```python
  if condition:
      # Execute if True
  else:
      # Execute if False
  ```

- **if-elif-else Statement**:

  ```python
  if condition1:
      # Execute if condition1 is True
  elif condition2:
      # Execute if condition2 is True
  else:
      # Execute if all above conditions are False
  ```

**Example**:

```python
age = 18
if age < 13:
    print("Child")
elif age < 20:
    print("Teenager")
else:
    print("Adult")
```

#### **b. Loops**

Loops allow you to execute a block of code multiple times.

- **for Loop**: Iterates over a sequence.

  ```python
  for item in sequence:
      # Code block
  ```

  **Example**:

  ```python
  for i in range(5):
      print(i)  # Prints numbers 0 to 4
  ```

- **while Loop**: Continues as long as a condition is True.

  ```python
  while condition:
      # Code block
  ```

  **Example**:

  ```python
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```

- **Loop Control Statements**:
  - `break`: Exits the loop.
  - `continue`: Skips to the next iteration.

### **6. Functions**

Functions are reusable blocks of code that perform a specific task.

- **Defining a Function**:

  ```python
  def function_name(parameters):
      # Code block
      return value  # Optional
  ```

- **Calling a Function**:

  ```python
  result = function_name(arguments)
  ```

**Example**:

```python
def add(a, b):
    return a + b

sum = add(5, 3)
print(sum)  # Output: 8
```

### **7. Modules and Import Statements**

Modules are files containing Python code (variables, functions, classes). Use `import` to include them in your program.

- **Import a Module**:

  ```python
  import module_name
  ```

- **Import Specific Items**:

  ```python
  from module_name import item_name
  ```

- **Import with Alias**:

  ```python
  import module_name as alias
  ```

**Example**:

```python
import math
print(math.sqrt(16))  # Output: 4.0
```

### **8. Input and Output**

- **Output**: Use `print()` to display data.

  ```python
  print("Hello, World!")
  ```

- **Input**: Use `input()` to receive user input.

  ```python
  name = input("Enter your name: ")
  print("Hello, " + name)
  ```

---

## **Data Types**

Python supports various built-in data types for different kinds of data.

### **1. Numeric Types**

#### **a. Integer (`int`)**

Whole numbers, positive or negative, without decimals.

```python
num = 10
```

#### **b. Floating-Point Number (`float`)**

Numbers with decimal points.

```python
pi = 3.14159
```

#### **c. Complex Number (`complex`)**

Numbers with a real and imaginary part.

```python
comp_num = 2 + 3j
```

### **2. String (`str`)**

A sequence of Unicode characters.

- **Defining Strings**:

  ```python
  single_quote_str = 'Hello'
  double_quote_str = "World"
  triple_quote_str = '''This is a
  multi-line string'''
  ```

- **String Operations**:

  ```python
  greeting = "Hello"
  name = "Alice"
  message = greeting + ", " + name + "!"  # Concatenation
  print(message)  # Output: Hello, Alice!
  ```

- **String Indexing and Slicing**:

  ```python
  text = "Python"
  first_char = text[0]        # 'P'
  last_char = text[-1]        # 'n'
  substring = text[1:4]       # 'yth'
  ```

*Zero Based Indexes:*

| String   | P   | y   | t   | h   | o   | n   |
| -------- | --- | --- | --- | --- | --- | --- |
| Human    | 1   | 2   | 3   | 4   | 5   | 6   |
| Computer | 0   | 1   | 2   | 3   | 4   | 5   |

- **String Methods**:

  ```python
  text = "hello world"
  print(text.upper())         # 'HELLO WORLD'
  print(text.capitalize())    # 'Hello world'
  print(text.replace('l', '*'))  # 'he**o wor*d'
  ```

### **3. Boolean (`bool`)**

Represents `True` or `False`.

```python
is_valid = True
has_errors = False
```

- **Logical Operations**:

  ```python
  a = True
  b = False
  print(a and b)  # False
  print(a or b)   # True
  print(not a)    # False
  ```

### **4. NoneType (`None`)**

Represents the absence of a value.

```python
result = None
```

### **5. Sequence Types**

#### **a. List (`list`)**

An ordered, mutable collection of items.

- **Defining a List**:

  ```python
  numbers = [1, 2, 3, 4, 5]
  mixed_list = [1, "two", 3.0, True]
  ```

- **Accessing Elements**:

  ```python
  first_item = numbers[0]     # 1
  last_item = numbers[-1]     # 5
  sub_list = numbers[1:3]     # [2, 3]
  ```

- **Modifying Lists**:

  ```python
  numbers.append(6)           # [1, 2, 3, 4, 5, 6]
  numbers.insert(0, 0)        # [0, 1, 2, 3, 4, 5, 6]
  numbers.remove(3)           # [0, 1, 2, 4, 5, 6]
  popped_item = numbers.pop() # Removes and returns the last item
  ```

- **List Comprehensions**:

  ```python
  squares = [x**2 for x in range(1, 6)]  # [1, 4, 9, 16, 25]
  ```

#### **b. Tuple (`tuple`)**

An ordered, immutable collection of items.

- **Defining a Tuple**:

  ```python
  coordinates = (10.0, 20.0)
  single_element_tuple = (5,)  # Note the comma
  ```

- **Accessing Elements**:

  ```python
  x_coord = coordinates[0]    # 10.0
  ```

#### **c. Range (`range`)**

Represents an immutable sequence of numbers.

- **Creating Ranges**:

  ```python
  range1 = range(5)           # 0 to 4
  range2 = range(1, 6)        # 1 to 5
  range3 = range(0, 10, 2)    # 0, 2, 4, 6, 8
  ```

### **6. Set (`set`)**

An unordered collection of unique items.

- **Defining a Set**:

  ```python
  unique_numbers = {1, 2, 3, 2, 1}
  print(unique_numbers)       # Output: {1, 2, 3}
  ```

- **Set Operations**:

  ```python
  set_a = {1, 2, 3}
  set_b = {3, 4, 5}
  union = set_a | set_b       # {1, 2, 3, 4, 5}
  intersection = set_a & set_b  # {3}
  difference = set_a - set_b  # {1, 2}
  ```

### **7. Dictionary (`dict`)**

An unordered collection of key-value pairs.

- **Defining a Dictionary**:

  ```python
  person = {
      'name': 'Alice',
      'age': 30,
      'city': 'New York'
  }
  ```

- **Accessing and Modifying Values**:

  ```python
  name = person['name']       # 'Alice'
  person['age'] = 31          # Update age
  person['country'] = 'USA'   # Add new key-value pair
  ```

- **Dictionary Methods**:

  ```python
  keys = person.keys()        # dict_keys(['name', 'age', 'city', 'country'])
  values = person.values()    # dict_values(['Alice', 31, 'New York', 'USA'])
  items = person.items()      # dict_items([('name', 'Alice'), ...])
  ```

---

## **Operators**

### **1. Arithmetic Operators**

- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `//` Floor Division
- `%` Modulus
- `**` Exponentiation

**Example**:

```python
a = 10
b = 3

print(a + b)   # 13
print(a - b)   # 7
print(a * b)   # 30
print(a / b)   # 3.333...
print(a // b)  # 3
print(a % b)   # 1
print(a ** b)  # 1000
```

### **2. Comparison Operators**

- `==` Equal to
- `!=` Not equal to
- `>` Greater than
- `<` Less than
- `>=` Greater than or equal to
- `<=` Less than or equal to

**Example**:

```python
x = 5
y = 10

print(x == y)  # False
print(x != y)  # True
print(x < y)   # True
print(x > y)   # False
```

### **3. Logical Operators**

- `and` Logical AND
- `or` Logical OR
- `not` Logical NOT

**Example**:

```python
a = True
b = False

print(a and b)  # False
print(a or b)   # True
print(not a)    # False
```

### **4. Assignment Operators**

- `=` Assign
- `+=` Add and assign
- `-=` Subtract and assign
- `*=` Multiply and assign
- `/=` Divide and assign
- `//=` Floor divide and assign
- `%=` Modulus and assign
- `**=` Exponentiate and assign

**Example**:

```python
x = 5
x += 3  # Equivalent to x = x + 3
print(x)  # Output: 8
```

### **5. Membership Operators**

- `in`: Returns `True` if a value is found in a sequence.
- `not in`: Returns `True` if a value is not found in a sequence.

**Example**:

```python
fruits = ['apple', 'banana', 'cherry']
print('banana' in fruits)     # True
print('orange' not in fruits) # True
```

### **6. Identity Operators**

- `is`: Returns `True` if both variables point to the same object.
- `is not`: Returns `True` if they do not point to the same object.

**Example**:

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)   # True
print(a is c)   # False
print(a == c)   # True
```

---

## **Type Conversion**

Convert between data types using built-in functions.

- **Numeric Conversions**:

  ```python
  int('123')     # 123
  float('3.14')  # 3.14
  str(100)       # '100'
  ```

- **Collection Conversions**:

  ```python
  list((1, 2, 3))       # [1, 2, 3]
  tuple([1, 2, 3])      # (1, 2, 3)
  set([1, 2, 2, 3])     # {1, 2, 3}
  dict([('a', 1), ('b', 2)])  # {'a': 1, 'b': 2}
  ```

---

## **Exception Handling**

Handle errors gracefully using `try`, `except`, `else`, and `finally` blocks.

```python
try:
    # Code that may raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Code to execute if exception occurs
    print("Cannot divide by zero!")
else:
    # Code to execute if no exception
    print("Division successful.")
finally:
    # Code that always executes
    print("Operation complete.")
```

---

# Python Basics Exam

Please select the correct answer(s) for each question by marking the checkbox next to it.

---

## **1. Which symbol is used to write a single-line comment in Python?**

- [ ] `//`
- [ ] `<!-- -->`
- [x] `#`
- [ ] `/* */`

---

## **2. How do you define a multi-line comment in Python?**

- [ ] Using `#` at the beginning of each line
- [ ] Enclosing the text within `/* */`
- [x] Enclosing the text within triple quotes `'''` or `"""`
- [ ] Using `//` at the start of each line

---

## **3. Which of the following is a valid variable name in Python?**

- [ ] `2nd_variable`
- [x] `_variable`
- [ ] `variable-name`
- [ ] `variable name`

---

## **4. What will be the output of the following code?**

```python
if 5 > 3:
    print("Five is greater than three.")
```

- [x] `Five is greater than three.`
- [ ] No output
- [ ] `IndentationError`
- [ ] `SyntaxError`

---

## **5. Which of these is the correct way to start a function definition in Python?**

- [ ] `function my_function():`
- [x] `def my_function():`
- [ ] `define my_function():`
- [ ] `fun my_function():`

---

## **6. How do you import the `math` module in Python?**

- [ ] `include math`
- [x] `import math`
- [ ] `using math`
- [ ] `require 'math'`

---

## **7. What data type is the object below?**

```python
[1, 2, 3, 4]
```

- [ ] Tuple
- [ ] Dictionary
- [x] List
- [ ] Set

---

## **8. What is the output of the following code?**

```python
print(type((1, 2, 3)))
```

- [x] `<class 'tuple'>`
- [ ] `<class 'list'>`
- [ ] `<class 'set'>`
- [ ] `<class 'dict'>`

---

## **9. Which operator is used for exponentiation in Python?**

- [ ] `^`
- [x] `**`
- [ ] `exp()`
- [ ] `%%`

---

## **10. What will be the result of the following code?**

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)
print(a is c)
```

- [ ] `True` followed by `True`
- [x] `True` followed by `False`
- [ ] `False` followed by `True`
- [ ] `False` followed by `False`

---

## **11. How do you handle exceptions in Python?**

- [ ] Using `try` and `catch` blocks
- [x] Using `try` and `except` blocks
- [ ] Using `if` and `else` statements
- [ ] Using `begin` and `rescue` blocks

---

## **12. Which of the following is NOT a valid Python data type?**

- [ ] `int`
- [ ] `str`
- [x] `real`
- [ ] `bool`

---

## **13. What is the output of the following code?**

```python
print("Hello" + str(5))
```

- [ ] `Hello5`
- [ ] `Hello 5`
- [x] `Hello5`
- [ ] `TypeError`

---

## **14. Which keyword is used to begin a loop that iterates over a sequence in Python?**

- [x] `for`
- [ ] `while`
- [ ] `loop`
- [ ] `iterate`

---

## **15. What will be the output of the following code?**

```python
for i in range(1, 5):
    if i == 3:
        continue
    print(i)
```

- [ ] `1 2`
- [ ] `1 2 3 4`
- [x] `1 2 4`
- [ ] `1 2 3`

---

## **16. How do you convert the string `'123'` into an integer in Python?**

- [ ] `int = '123'`
- [x] `int('123')`
- [ ] `str(123)`
- [ ] `float('123')`

---

## **17. Which of the following statements is true about lists and tuples?**

- [ ] Lists are immutable; tuples are mutable.
- [x] Lists are mutable; tuples are immutable.
- [ ] Both lists and tuples are mutable.
- [ ] Both lists and tuples are immutable.

---

## **18. What does the `len()` function do in Python?**

- [x] Returns the number of items in an object
- [ ] Calculates the length of a number
- [ ] Counts the number of function definitions
- [ ] Determines the data type of an object

---

## **19. Which of the following is a logical operator in Python?**

- [ ] `&`
- [ ] `|`
- [x] `and`
- [ ] `not in`

---

## **20. What will be the output of the following code?**

```python
def add(a, b=2):
    return a + b

print(add(3))
```

- [ ] `4`
- [ ] `3`
- [x] `5`
- [ ] `TypeError`

---

## **21. How do you start a conditional statement in Python?**

- [ ] `when condition:`
- [x] `if condition:`
- [ ] `for condition:`
- [ ] `def condition:`

---

## **22. Which of the following is used to create an empty set in Python?**

- [ ] `empty_set = {}`
- [x] `empty_set = set()`
- [ ] `empty_set = []`
- [ ] `empty_set = ()`

---

## **23. What is the purpose of the `pass` statement in Python?**

- [ ] Terminates the loop
- [ ] Skips the current iteration
- [x] Acts as a null operation; a placeholder
- [ ] Raises an exception

---

## **24. How do you write a comment that spans multiple lines in Python?**

- [ ] Using backslashes at the end of each line
- [ ] Enclosing the comment in `[]`
- [x] Enclosing the comment in triple quotes `'''` or `"""`
- [ ] Starting each line with `##`

---

## **25. What will be the result of the following code?**

```python
x = 10
y = 3
print(x % y)
```

- [ ] `3`
- [ ] `0`
- [x] `1`
- [ ] `10`

---

## **26. Which function is used to get user input in Python 3?**

- [ ] `raw_input()`
- [x] `input()`
- [ ] `get_input()`
- [ ] `scan()`

---

## **27. How do you check the data type of a variable `x` in Python?**

- [ ] `typeof x`
- [x] `type(x)`
- [ ] `dataType(x)`
- [ ] `class(x)`

---

## **28. What is the output of the following code?**

```python
print(bool(0), bool(1))
```

- [ ] `False False`
- [ ] `True False`
- [x] `False True`
- [ ] `True True`

---

## **29. Which of the following is the correct way to open a file for reading in Python?**

- [ ] `open('file.txt', 'w')`
- [x] `open('file.txt', 'r')`
- [ ] `open('file.txt', 'rw')`
- [ ] `open('file.txt', 'a')`

---

## **30. What will be the output of the following code?**

```python
print(2 ** 3 ** 2)
```

- [ ] `64`
- [x] `512`
- [ ] `256`
- [ ] `4096`

---
