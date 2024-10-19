
---

## **1. Conditionals**

Conditionals are used to perform different computations or actions depending on whether a specific Boolean condition evaluates to `True` or `False`.

### **1.1 The `if` Statement**

The `if` statement is used to test a condition. If the condition is `True`, the indented code block is executed.

**Syntax:**

```python
if condition:
    # Code block to execute if condition is True
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

### **1.2 The `if-else` Statement**

The `if-else` statement provides an alternative code block to execute when the condition is `False`.

**Syntax:**

```python
if condition:
    # Code block if condition is True
else:
    # Code block if condition is False
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

### **1.3 The `if-elif-else` Statement**

The `if-elif-else` statement allows you to check multiple conditions sequentially.

**Syntax:**

```python
if condition1:
    # Code block if condition1 is True
elif condition2:
    # Code block if condition2 is True
elif condition3:
    # Code block if condition3 is True
else:
    # Code block if all conditions are False
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
elif score >= 60:
    grade = 'D'
else:
    grade = 'F'

print(f"Your grade is {grade}.")
```

**Output:**

```
Your grade is B.
```

### **1.4 Nested Conditionals**

You can place conditional statements inside other conditional statements.

**Example:**

```python
num = 10

if num > 0:
    print("Positive number")
    if num % 2 == 0:
        print("Even number")
    else:
        print("Odd number")
else:
    print("Negative number")
```

**Output:**

```
Positive number
Even number
```

### **1.5 Conditional Expressions (Ternary Operator)**

A conditional expression evaluates a condition in a single line of code.

**Syntax:**

```python
value_if_true if condition else value_if_false
```

**Example:**

```python
age = 20
status = "Adult" if age >= 18 else "Minor"
print(status)
```

**Output:**

```
Adult
```

---

## **2. Loops**

Loops are used to execute a block of code repeatedly. Python provides two types of loops:

- **`for` loops**: Iterate over a sequence (e.g., list, tuple, string).
- **`while` loops**: Execute as long as a condition is `True`.

### **2.1 The `for` Loop**

The `for` loop is used for iterating over a sequence.

**Syntax:**

```python
for variable in sequence:
    # Code block to execute
```

**Example: Iterating Over a List**

```python
fruits = ['apple', 'banana', 'cherry']
for fruit in fruits:
    print(fruit)
```

**Output:**

```
apple
banana
cherry
```

**Example: Using `range()` Function**

The `range()` function generates a sequence of numbers.

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

**Example: Specifying Start, Stop, and Step in `range()`**

```python
for i in range(1, 10, 2):
    print(i)
```

**Output:**

```
1
3
5
7
9
```

**Example: Iterating Over a String**

```python
text = "Python"
for char in text:
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

### **2.2 The `while` Loop**

The `while` loop continues to execute as long as the condition remains `True`.

**Syntax:**

```python
while condition:
    # Code block to execute
```

**Example:**

```python
count = 0
while count < 5:
    print("Count is:", count)
    count += 1  # Increment count
```

**Output:**

```
Count is: 0
Count is: 1
Count is: 2
Count is: 3
Count is: 4
```

**Caution:** Ensure that the condition eventually becomes `False` to avoid infinite loops.

### **2.3 Loop Control Statements**

Python provides control statements to alter the flow of loops:

- **`break`**: Exits the loop immediately.
- **`continue`**: Skips the current iteration and moves to the next one.
- **`pass`**: Does nothing; acts as a placeholder.

#### **2.3.1 The `break` Statement**

**Example:**

```python
for i in range(1, 10):
    if i == 5:
        break
    print(i)
```

**Output:**

```
1
2
3
4
```

#### **2.3.2 The `continue` Statement**

**Example:**

```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
```

**Output:**

```
1
2
4
5
```

#### **2.3.3 The `pass` Statement**

Used when a statement is required syntactically but no action is needed.

**Example:**

```python
for i in range(5):
    pass  # TODO: implement this later
```

### **2.4 Nested Loops**

Loops can be nested within other loops.

**Example: Multiplication Table**

```python
for i in range(1, 4):
    for j in range(1, 4):
        product = i * j
        print(f"{i} x {j} = {product}")
    print("---")
```

**Output:**

```
1 x 1 = 1
1 x 2 = 2
1 x 3 = 3
---
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
---
3 x 1 = 3
3 x 2 = 6
3 x 3 = 9
---
```

---

## **3. Practical Examples**

### **3.1 Finding Prime Numbers**

**Using `for` Loop and `else` Clause:**

The `else` clause in a loop executes when the loop completes normally (no `break`).

```python
for num in range(2, 10):
    for i in range(2, num):
        if num % i == 0:
            break
    else:
        print(num, "is a prime number")
```

**Output:**

```
2 is a prime number
3 is a prime number
5 is a prime number
7 is a prime number
```

### **3.2 Simple Login Simulation**

```python
attempts = 3
password = "secret"

while attempts > 0:
    user_input = input("Enter your password: ")
    if user_input == password:
        print("Access granted.")
        break
    else:
        attempts -= 1
        print(f"Incorrect password. {attempts} attempts left.")
else:
    print("Access denied.")
```

**Sample Output:**

```
Enter your password: guess
Incorrect password. 2 attempts left.
Enter your password: secret
Access granted.
```

### **3.3 Calculating Factorial**

**Using `while` Loop:**

```python
num = 5
result = 1
i = 1

while i <= num:
    result *= i
    i += 1

print(f"The factorial of {num} is {result}.")
```

**Output:**

```
The factorial of 5 is 120.
```

**Using `for` Loop:**

```python
num = 5
result = 1

for i in range(1, num + 1):
    result *= i

print(f"The factorial of {num} is {result}.")
```

---

## **4. Best Practices**

- **Avoid Infinite Loops:** Ensure that the loop's condition will eventually become `False`.

  ```python
  # Bad: Infinite loop
  while True:
      pass  # This loop will run forever

  # Good: Condition that becomes False
  count = 10
  while count > 0:
      count -= 1
  ```

- **Use Descriptive Variable Names:** Improves code readability.

  ```python
  # Less clear
  for i in range(10):
      print(i)

  # More clear
  for student_number in range(1, 11):
      print(f"Student {student_number}")
  ```

- **Keep Code DRY (Don't Repeat Yourself):** Use loops to avoid code repetition.

  ```python
  # Repetitive code
  print("Student 1")
  print("Student 2")
  print("Student 3")

  # Better with a loop
  for i in range(1, 4):
      print(f"Student {i}")
  ```

- **Proper Indentation:** Python uses indentation to define code blocks.

  ```python
  # Correct indentation
  if condition:
      # Code block

  # Incorrect indentation will raise an error
  if condition:
  # Code block (IndentationError)
  ```

- **Use `else` with Loops When Appropriate:** The `else` block executes after the loop finishes normally.

  ```python
  for item in collection:
      if search_condition:
          break
  else:
      print("Item not found.")
  ```

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
