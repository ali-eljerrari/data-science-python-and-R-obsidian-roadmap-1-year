
---


Control structures are fundamental elements in programming that allow developers to control the flow of execution based on certain conditions or to repeat a block of code multiple times. This guide will cover loops and conditional statements, primarily using **Python** for examples due to its readability and widespread use.

## Table of Contents

1. [Introduction to Control Structures](#1-introduction)
2. [Conditional Statements](#2-conditional-statements)
   - [The `if` Statement](#2-1-if-statement)
   - [The `if-else` Statement](#2-2-if-else-statement)
   - [The `if-elif-else` Statement](#2-3-if-elif-else-statement)
   - [Nested Conditionals](#2-4-nested-conditionals)
   - [Conditional Expressions (Ternary Operator)](#2-5-conditional-expressions)
3. [Loops](#3-loops)
   - [The `for` Loop](#3-1-for-loop)
   - [The `while` Loop](#3-2-while-loop)
   - [Loop Control Statements](#3-3-loop-control-statements)
     - [`break`](#3-3-1-break)
     - [`continue`](#3-3-2-continue)
     - [`pass`](#3-3-3-pass)
   - [Nested Loops](#3-4-nested-loops)
   - [Looping Techniques](#3-5-looping-techniques)
4. [Examples and Use Cases](#4-examples)
5. [Best Practices](#5-best-practices)
6. [Conclusion](#6-conclusion)

---

<a name="1-introduction"></a>
## 1. Introduction to Control Structures

Control structures determine the order in which statements are executed in a program. They are essential for making decisions (conditionals) and performing repetitive tasks (loops).

- **Conditionals:** Execute code blocks based on whether a condition is true or false.
- **Loops:** Repeat a block of code multiple times until a condition is met.

---

<a name="2-conditional-statements"></a>
## 2. Conditional Statements

Conditional statements allow a program to execute certain pieces of code based on whether a condition is `True` or `False`.

<a name="2-1-if-statement"></a>
### 2.1 The `if` Statement

The simplest form of a conditional statement. If the condition evaluates to `True`, the indented block of code is executed.

**Syntax:**

```python
if condition:
    # code to execute if condition is True
```

**Example:**

```python
age = 18

if age >= 18:
    print("You are eligible to vote.")
```

**Output:**

```
You are eligible to vote.
```

<a name="2-2-if-else-statement"></a>
### 2.2 The `if-else` Statement

Provides an alternative block of code to execute if the condition is `False`.

**Syntax:**

```python
if condition:
    # code if condition is True
else:
    # code if condition is False
```

**Example:**

```python
age = 16

if age >= 18:
    print("You are eligible to vote.")
else:
    print("You are not eligible to vote.")
```

**Output:**

```
You are not eligible to vote.
```

<a name="2-3-if-elif-else-statement"></a>
### 2.3 The `if-elif-else` Statement

Allows checking multiple conditions sequentially.

**Syntax:**

```python
if condition1:
    # code if condition1 is True
elif condition2:
    # code if condition2 is True
elif condition3:
    # code if condition3 is True
else:
    # code if none of the above conditions are True
```

**Example:**

```python
score = 85

if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'
elif score >= 70:
    grade = 'C'
else:
    grade = 'F'

print(f"Your grade is {grade}.")
```

**Output:**

```
Your grade is B.
```

<a name="2-4-nested-conditionals"></a>
### 2.4 Nested Conditionals

Conditionals can be nested within each other to handle more complex logic.

**Example:**

```python
age = 20
citizen = True

if age >= 18:
    if citizen:
        print("You are eligible to vote.")
    else:
        print("You must be a citizen to vote.")
else:
    print("You are not old enough to vote.")
```

**Output:**

```
You are eligible to vote.
```

<a name="2-5-conditional-expressions"></a>
### 2.5 Conditional Expressions (Ternary Operator)

A concise way to write simple `if-else` statements.

**Syntax:**

```python
variable = value_if_true if condition else value_if_false
```

**Example:**

```python
age = 16
status = "Adult" if age >= 18 else "Minor"
print(status)
```

**Output:**

```
Minor
```

---

<a name="3-loops"></a>
## 3. Loops

Loops are used to execute a block of code repeatedly.

<a name="3-1-for-loop"></a>
### 3.1 The `for` Loop

Iterates over a sequence (such as a list, tuple, string, or range).

**Syntax:**

```python
for variable in sequence:
    # code to execute in each iteration
```

**Example: Iterating Over a List**

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```

**Output:**

```
apple
banana
cherry
```

**Example: Using `range()`**

```python
for i in range(5):
    print(i)
```

**Output:**

```
0
1
2
3
4
```

**Example: Iterating Over a String**

```python
for char in "Python":
    print(char)
```

**Output:**

```
P
y
t
h
o
n
```

<a name="3-2-while-loop"></a>
### 3.2 The `while` Loop

Repeats as long as a condition is `True`.

**Syntax:**

```python
while condition:
    # code to execute while condition is True
```

**Example:**

```python
count = 0

while count < 5:
    print(count)
    count += 1
```

**Output:**

```
0
1
2
3
4
```

<a name="3-3-loop-control-statements"></a>
### 3.3 Loop Control Statements

Modify the behavior of loops.

<a name="3-3-1-break"></a>
#### 3.3.1 `break`

Exits the nearest enclosing loop immediately.

**Example:**

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

**Output:**

```
0
1
2
3
4
```

<a name="3-3-2-continue"></a>
#### 3.3.2 `continue`

Skips the current iteration and moves to the next one.

**Example:**

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

**Output:**

```
0
1
3
4
```

<a name="3-3-3-pass"></a>
#### 3.3.3 `pass`

Does nothing; a placeholder when a statement is syntactically required but no action is needed.

**Example:**

```python
for i in range(5):
    if i == 2:
        pass  # Do nothing
    else:
        print(i)
```

**Output:**

```
0
1
3
4
```

<a name="3-4-nested-loops"></a>
### 3.4 Nested Loops

Loops inside other loops.

**Example: Multiplication Table**

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} * {j} = {i * j}")
```

**Output:**

```
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
2 * 1 = 2
2 * 2 = 4
2 * 3 = 6
3 * 1 = 3
3 * 2 = 6
3 * 3 = 9
```

<a name="3-5-looping-techniques"></a>
### 3.5 Looping Techniques

#### Enumerate

Iterate over a sequence and have access to both index and value.

**Example:**

```python
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
```

**Output:**

```
0: apple
1: banana
2: cherry
```

#### Zip

Iterate over two or more sequences simultaneously.

**Example:**

```python
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

for name, age in zip(names, ages):
    print(f"{name} is {age} years old.")
```

**Output:**

```
Alice is 25 years old.
Bob is 30 years old.
Charlie is 35 years old.
```

---

<a name="4-examples"></a>
## 4. Examples and Use Cases

### Example 1: Finding Prime Numbers

```python
for num in range(2, 20):
    is_prime = True
    for i in range(2, num):
        if num % i == 0:
            is_prime = False
            break
    if is_prime:
        print(f"{num} is a prime number.")
```

**Output:**

```
2 is a prime number.
3 is a prime number.
5 is a prime number.
7 is a prime number.
11 is a prime number.
13 is a prime number.
17 is a prime number.
19 is a prime number.
```

### Example 2: Password Validation

```python
password = input("Enter your password: ")

if len(password) < 8:
    print("Password must be at least 8 characters long.")
elif password.isdigit() or password.isalpha():
    print("Password must contain both letters and numbers.")
else:
    print("Password is valid.")
```

### Example 3: Summing Numbers Until Zero is Entered

```python
total = 0

while True:
    num = int(input("Enter a number (0 to stop): "))
    if num == 0:
        break
    total += num

print(f"The total sum is {total}.")
```

---

<a name="5-best-practices"></a>
## 5. Best Practices

- **Use Meaningful Variable Names:** Improves code readability.
  
  ```python
  for student in students:
      print(student)
  ```

- **Avoid Deep Nesting:** Can make code hard to read and maintain. Consider breaking code into functions or using logical operators.

- **Use `else` with Loops (Advanced):** In Python, loops can have an `else` clause that executes if the loop completes normally (no `break`).

  ```python
  for item in items:
      if condition(item):
          break
  else:
      print("No item met the condition.")
  ```

- **Limit Use of `break` and `continue`:** While they are useful, overusing them can make code harder to understand.

- **Consistent Indentation:** Essential in Python. Use 4 spaces per indentation level.

- **Comment Your Code:** Explain complex logic within loops and conditionals.

---

<a name="6-conclusion"></a>
## 6. Conclusion

Control structures are the backbone of any programming language, enabling complex decision-making and repetitive tasks. Mastering loops and conditionals allows you to write more efficient and effective code.

---

**Next Steps:**

- **Practice:** Implement various algorithms using loops and conditionals.
- **Explore Advanced Topics:**
  - **List Comprehensions:** Concise way to create lists.
  - **Generator Expressions:** For large datasets.
- **Learn Debugging Techniques:** Use debugging tools to step through loops and conditionals.


---

# Python Control Structures Exam

Please select the correct answer(s) for each question by marking the checkbox next to it.

---

## **1. What is the correct syntax for an `if` statement in Python?**

- [x] `if condition:`
- [ ] `if (condition)`
- [ ] `if condition then`
- [ ] `if condition { }`

---

## **2. What is the output of the following code?**

```python
x = 5
if x > 3:
    print("Greater")
else:
    print("Lesser")
```

- [x] `Greater`
- [ ] `Lesser`
- [ ] No output
- [ ] `SyntaxError`

---

## **3. How many times will "Hello" be printed in the following code?**

```python
for i in range(3):
    print("Hello")
```

- [ ] 2 times
- [x] 3 times
- [ ] 4 times
- [ ] 0 times

---

## **4. Which of the following is the correct way to start a `while` loop in Python?**

- [ ] `while (condition) {`
- [x] `while condition:`
- [ ] `while condition do`
- [ ] `loop while condition:`

---

## **5. What is the purpose of the `break` statement in loops?**

- [ ] Skips the current iteration
- [ ] Repeats the loop from the beginning
- [x] Exits the loop immediately
- [ ] Exits the program

---

## **6. What is the output of the following code?**

```python
for i in range(5):
    if i == 3:
        break
    print(i)
```

- [ ] `0 1 2 3 4`
- [ ] `0 1 2 3`
- [x] `0 1 2`
- [ ] `1 2 3`

---

## **7. How do you write an `if` statement that executes code only if `x` is both greater than 10 and less than 20?**

- [ ] `if x > 10 or x < 20:`
- [ ] `if x > 10 and < 20:`
- [x] `if x > 10 and x < 20:`
- [ ] `if 10 < x < 20:`

---

## **8. What keyword is used to skip the current iteration in a loop and continue with the next iteration?**

- [ ] `break`
- [x] `continue`
- [ ] `pass`
- [ ] `skip`

---

## **9. What is the output of the following code?**

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

- [ ] `1 2 3 4 5`
- [x] `0 1 2 3 4`
- [ ] `0 1 2 3 4 5`
- [ ] Infinite loop

---

## **10. Which of the following is a valid way to write an `else` clause for a loop that did not encounter a `break` statement?**

- [x] 

    ```python
    for item in collection:
        # loop body
    else:
        # else clause
    ```

- [ ] 

    ```python
    for item in collection:
        # loop body
    else if:
        # else clause
    ```

- [ ] 

    ```python
    for item in collection:
        # loop body
    if not break:
        # else clause
    ```

- [ ] 

    ```python
    for item in collection:
        # loop body
    else if not break:
        # else clause
    ```

---

## **11. What will be the output of the following code?**

```python
x = 10
if x > 5:
    print("A")
    if x > 8:
        print("B")
else:
    print("C")
```

- [ ] `A`
- [x] `A B`
- [ ] `C`
- [ ] `B`

---

## **12. Which of the following statements is true about the `pass` statement in Python?**

- [ ] It exits the loop
- [ ] It skips the current iteration
- [ ] It restarts the loop
- [x] It does nothing; it's a placeholder

---

## **13. What is the output of the following code?**

```python
for letter in 'Python':
    if letter == 'h':
        break
    print(letter)
```

- [ ] `P y t h o n`
- [x] `P y t`
- [ ] `P y t h`
- [ ] `P y`

---

## **14. How can you check if a number `n` is even using a conditional statement?**

- [x] `if n % 2 == 0:`
- [ ] `if n / 2:`
- [ ] `if n % 2 = 0:`
- [ ] `if n // 2 == 0:`

---

## **15. What is the output of the following code?**

```python
i = 1
while i < 4:
    print(i)
    i += 1
else:
    print("Done")
```

- [ ] `1 2 3`
- [x] `1 2 3 Done`
- [ ] `1 2 3 4 Done`
- [ ] `1 2 3 4`

---

## **16. Which of the following correctly demonstrates a nested `if` statement?**

- [ ] 

    ```python
    if condition1:
    if condition2:
        # code
    ```

- [x] 

    ```python
    if condition1:
        if condition2:
            # code
    ```

- [ ] 

    ```python
    if condition1 and condition2:
        # code
    ```

- [ ] 

    ```python
    if condition1:
        # code
        if condition2:
        # code
    ```

---

## **17. How do you write a conditional expression (ternary operator) in Python?**

- [ ] `condition ? value_if_true : value_if_false`
- [ ] `if condition then value_if_true else value_if_false`
- [x] `value_if_true if condition else value_if_false`
- [ ] `value_if_true when condition else value_if_false`

---

## **18. What is the output of the following code?**

```python
for i in range(1, 6):
    if i == 3:
        pass
        print("Pass executed")
    print(i)
```

- [ ] `1 2 Pass executed 3 4 5`
- [x] `1 2 Pass executed 3 4 5`
- [ ] `1 2 4 5`
- [ ] `1 2 3 Pass executed 4 5`

---

## **19. Which of the following loop structures will result in an infinite loop?**

- [ ] 

    ```python
    for i in range(10):
        print(i)
    ```

- [x] 

    ```python
    while True:
        print("Infinite")
    ```

- [ ] 

    ```python
    count = 5
    while count > 0:
        print(count)
        count -= 1
    ```

- [ ] 

    ```python
    for i in range(1, 5):
        if i == 3:
            break
        print(i)
    ```

---

## **20. What is the correct syntax for an `if` statement that checks multiple conditions using `elif`?**

- [ ] 

    ```python
    if condition1:
        # code
    elseif condition2:
        # code
    else:
        # code
    ```

- [x] 

    ```python
    if condition1:
        # code
    elif condition2:
        # code
    else:
        # code
    ```

- [ ] 

    ```python
    if condition1:
        # code
    else if condition2:
        # code
    else:
        # code
    ```

- [ ] 

    ```python
    if condition1:
        # code
    elif condition2
        # code
    else:
        # code
    ```

---

## **21. What will be the output of the following code?**

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

- [ ] 

    ```
    0 0
    1 1
    2 2
    ```

- [x] 

    ```
    0 0
    0 1
    1 0
    1 1
    2 0
    2 1
    ```

- [ ] 

    ```
    0 1
    1 0
    1 1
    2 0
    2 1
    ```

- [ ] 

    ```
    0 0
    1 0
    2 0
    ```

---

## **22. How do you write a loop that iterates over a list `my_list`?**

- [ ] `for i in len(my_list):`
- [x] `for item in my_list:`
- [ ] `for i to my_list.length():`
- [ ] `while i < len(my_list):`

---

## **23. What does the following code do?**

```python
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue
    print(i)
```

- [ ] Prints `1 2 3 4 5`
- [ ] Prints `1 2 3 4`
- [x] Prints `1 2 4 5`
- [ ] Prints `1 2 3 5`

---

## **24. Which of the following is NOT a valid loop control statement in Python?**

- [ ] `break`
- [ ] `continue`
- [x] `exit`
- [ ] `pass`

---

## **25. What will be the output of the following code?**

```python
for num in range(2, 5):
    for i in range(2, num):
        if num % i == 0:
            print(num, "is not a prime number")
            break
    else:
        print(num, "is a prime number")
```

- [ ] 

    ```
    2 is not a prime number
    3 is not a prime number
    4 is not a prime number
    ```

- [x] 

    ```
    2 is a prime number
    3 is a prime number
    4 is not a prime number
    ```

- [ ] 

    ```
    2 is a prime number
    3 is not a prime number
    4 is not a prime number
    ```

- [ ] 

    ```
    2 is not a prime number
    3 is a prime number
    4 is a prime number
    ```

---

## **26. How do you check multiple conditions in an `if` statement?**

- [ ] Using `&` and `|` operators
- [x] Using `and` and `or` operators
- [ ] Using `&&` and `||` operators
- [ ] By writing separate `if` statements

---

## **27. What is the output of the following code?**

```python
for x in range(1, 4):
    for y in range(1, 4):
        if x == y:
            continue
        print(f"x={x}, y={y}")
```

- [ ] 

    ```
    x=1, y=1
    x=2, y=2
    x=3, y=3
    ```

- [x] 

    ```
    x=1, y=2
    x=1, y=3
    x=2, y=1
    x=2, y=3
    x=3, y=1
    x=3, y=2
    ```

- [ ] 

    ```
    x=1, y=1
    x=1, y=2
    x=1, y=3
    x=2, y=1
    x=2, y=2
    x=2, y=3
    x=3, y=1
    x=3, y=2
    x=3, y=3
    ```

- [ ] 

    ```
    x=1, y=1
    x=2, y=2
    x=3, y=3
    ```

---

## **28. Which statement is used to exit a loop prematurely in Python?**

- [ ] `continue`
- [ ] `pass`
- [ ] `stop`
- [x] `break`

---

## **29. In a nested loop, which loop does the `break` statement affect?**

- [x] The innermost loop
- [ ] The outermost loop
- [ ] All loops
- [ ] It depends on where `break` is placed

---

## **30. What is the output of the following code?**

```python
for i in range(1, 4):
    for j in range(1, 4):
        if i == 2 and j == 2:
            break
        print(f"{i},{j}")
```

- [ ] 

    ```
    1,1
    1,2
    1,3
    2,1
    3,1
    3,2
    3,3
    ```

- [x] 

    ```
    1,1
    1,2
    1,3
    2,1
    3,1
    3,2
    3,3
    ```

- [ ] 

    ```
    1,1
    1,2
    1,3
    2,1
    2,2
    2,3
    3,1
    3,2
    3,3
    ```

- [ ] 

    ```
    1,1
    1,2
    1,3
    2,1
    2,2
    3,1
    3,2
    3,3
    ```

---
