
---


File handling is a crucial aspect of programming that allows you to store data permanently. Python provides a simple yet powerful interface for working with files. This guide will cover everything you need to know about file handling in Python, complete with examples and best practices.

## Table of Contents

1. [[#1. Introduction to File Handling]]
2. [[#2. Opening and Closing Files]]
3. [[#3. File Modes]]
4. [[#4. Reading from Files]]
5. [[#5. Writing to Files]]
6. [[#6. File Methods]]
7. [[#7. The `with` Statement]]
8. [[#8. Working with Binary Files]]
9. [[#9. Handling Exceptions]]
10. [[#10. File Paths and Directories]]
11. [[#11. Advanced File Operations]]
12. [[#12. Best Practices]]


## 1. Introduction to File Handling

Files are used to store data permanently on a storage device. Python provides built-in functions and methods for file operations such as reading, writing, and appending data.

**Types of Files:**

- **Text Files:** Contain human-readable characters.
- **Binary Files:** Contain data in binary form, readable by computers.

## 2. Opening and Closing Files

Before performing any operation on a file, you need to open it using the `open()` function, which returns a file object.

**Syntax:**

```python
file_object = open(file_name, mode)
```

- `file_name`: Name or path of the file.
- `mode`: Mode in which the file is opened.

**Example:**

```python
file = open('example.txt', 'r')  # Open a file for reading
```

**Closing a File:**

Always close a file after completing operations to free system resources.

```python
file.close()
```

## 3. File Modes

The mode parameter in the `open()` function specifies the purpose of opening the file.

| Mode | Description                                          |
|------|------------------------------------------------------|
| `'r'`   | Read mode (default). Opens a file for reading.       |
| `'w'`   | Write mode. Creates a new file or truncates existing.|
| `'a'`   | Append mode. Writes data at the end of the file.     |
| `'r+'`  | Read and write mode. File must exist.                |
| `'w+'`  | Write and read mode. Creates a new file or truncates.|
| `'a+'`  | Append and read mode. Creates file if it doesn't exist.|
| `'b'`   | Binary mode. Used with other modes like `'rb'`.      |
| `'t'`   | Text mode (default). Used with other modes like `'rt'`.|

**Examples:**

- `'rb'`: Read binary file.
- `'w+'`: Write and read a text file.

## 4. Reading from Files

### 4.1 `read()`

Reads the entire file or specified number of characters.

```python
file = open('example.txt', 'r')
content = file.read()
print(content)
file.close()
```

### 4.2 `readline()`

Reads one line at a time.

```python
file = open('example.txt', 'r')
line = file.readline()
while line:
    print(line, end='')
    line = file.readline()
file.close()
```

### 4.3 `readlines()`

Returns a list of all lines.

```python
file = open('example.txt', 'r')
lines = file.readlines()
for line in lines:
    print(line, end='')
file.close()
```

### 4.4 Iterating Over a File Object

```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line, end='')
```

## 5. Writing to Files

### 5.1 `write()`

Writes a string to the file.

```python
file = open('example.txt', 'w')
file.write('Hello, World!')
file.close()
```

### 5.2 `writelines()`

Writes a list of strings.

```python
lines = ['First line\n', 'Second line\n', 'Third line\n']
file = open('example.txt', 'w')
file.writelines(lines)
file.close()
```

### 5.3 Appending to Files

```python
file = open('example.txt', 'a')
file.write('Appending a new line.\n')
file.close()
```

## 6. File Methods

### 6.1 `seek()`

Moves the file cursor to a specified position.

```python
file = open('example.txt', 'r')
file.seek(10)  # Move to the 10th byte
```

### 6.2 `tell()`

Returns the current position of the file cursor.

```python
position = file.tell()
print(f'Current position: {position}')
```

### 6.3 `flush()`

Flushes the internal buffer to the file.

```python
file.flush()
```

## 7. The `with` Statement

Using the `with` statement automatically handles closing the file, even if exceptions occur.

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
# File is automatically closed here
```

## 8. Working with Binary Files

Binary files store data in binary format.

### 8.1 Reading Binary Files

```python
with open('image.png', 'rb') as binary_file:
    data = binary_file.read()
```

### 8.2 Writing Binary Files

```python
with open('copy_image.png', 'wb') as binary_file:
    binary_file.write(data)
```

## 9. Handling Exceptions

Always handle exceptions to prevent your program from crashing.

```python
try:
    with open('nonexistent.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print('File not found.')
except Exception as e:
    print(f'An error occurred: {e}')
```

## 10. File Paths and Directories

### 10.1 Absolute and Relative Paths

- **Absolute Path:** Full path from the root directory.
- **Relative Path:** Path relative to the current working directory.

```python
# Absolute path
file = open('/Users/username/Documents/example.txt', 'r')

# Relative path
file = open('example.txt', 'r')
```

### 10.2 Using `os` Module

```python
import os

current_dir = os.getcwd()
print(f'Current Directory: {current_dir}')

# Changing directory
os.chdir('/path/to/directory')
```

### 10.3 Checking if a File Exists

```python
import os

if os.path.exists('example.txt'):
    print('File exists.')
else:
    print('File does not exist.')
```

## 11. Advanced File Operations

### 11.1 Deleting a File

```python
import os

os.remove('example.txt')
```

### 11.2 Renaming a File

```python
import os

os.rename('old_name.txt', 'new_name.txt')
```

### 11.3 Copying Files

```python
import shutil

shutil.copy('source.txt', 'destination.txt')
```

### 11.4 File Encoding

Specify encoding when dealing with text files containing special characters.

```python
with open('example.txt', 'r', encoding='utf-8') as file:
    content = file.read()
```

## 12. Best Practices

- **Use the `with` Statement:** Automatically handles closing files.
- **Handle Exceptions:** Use `try-except` blocks.
- **Specify Encoding:** Especially important for text files with special characters.
- **Avoid Hardcoding Paths:** Use `os.path` for building paths.
- **Read Large Files Efficiently:** Read in chunks or iterate over lines.

**Example of Efficient Reading:**

```python
def read_large_file(file_path):
    with open(file_path, 'r') as file:
        for line in file:
            process(line)  # Replace with your processing function
```


---


# Python File Handling Exam Answers

Below are the answers to the 30 multiple-choice questions on Python file handling. Each correct answer is indicated with a checked box. Explanations are provided for clarity.

---

## **Multiple Choice Questions**

**1.** Which of the following modes opens a file for writing and truncates the file to zero length?

- [ ] a) `'r'`
- [ ] b) `'a'`
- [x] c) `'w'`
- [ ] d) `'r+'`

**Explanation:** The `'w'` mode opens a file for writing and truncates it to zero length if it already exists.

---

**2.** What does the `readlines()` method return when called on a file object?

- [ ] a) A string containing the entire file content
- [x] b) A list of all lines in the file
- [ ] c) An iterator over the lines in the file
- [ ] d) The next line in the file as a string

**Explanation:** The `readlines()` method returns a list where each element is a line from the file.

---

**3.** Which method would you use to move the file cursor to a specific position?

- [ ] a) `tell()`
- [x] b) `seek()`
- [ ] c) `move()`
- [ ] d) `cursor()`

**Explanation:** The `seek()` method is used to move the file cursor to a specific position.

---

**4.** What is the default mode when opening a file using `open()` without specifying a mode?

- [ ] a) `'w'`
- [x] b) `'r'`
- [ ] c) `'a'`
- [ ] d) `'r+'`

**Explanation:** The default mode is `'r'`, which stands for read mode.

---

**5.** Which of the following statements correctly opens a file named `'data.bin'` for binary reading?

- [x] a) `open('data.bin', 'rb')`
- [ ] b) `open('data.bin', 'br')`
- [ ] c) `open('data.bin', 'r')`
- [ ] d) `open('data.bin', 'wb')`

**Explanation:** `'rb'` opens the file in binary read mode.

---

**6.** What is the purpose of the `flush()` method in file handling?

- [ ] a) Close the file
- [ ] b) Clear the internal buffer
- [ ] c) Move the cursor to the beginning
- [x] d) Write data from the buffer to the file

**Explanation:** The `flush()` method forces the write of data from the buffer to the file.

---

**7.** When using the `with` statement for file handling, which method is automatically called upon exiting the block?

- [ ] a) `open()`
- [x] b) `close()`
- [ ] c) `flush()`
- [ ] d) `read()`

**Explanation:** The `with` statement ensures that `close()` is called automatically.

---

**8.** Which module would you import to work with file paths and directories?

- [ ] a) `sys`
- [x] b) `os`
- [ ] c) `math`
- [ ] d) `time`

**Explanation:** The `os` module provides functions for interacting with the operating system, including file paths and directories.

---

**9.** What does the `'a+'` mode do when opening a file?

- [ ] a) Opens a file for reading only
- [x] b) Opens a file for appending and reading
- [ ] c) Opens a file for writing only
- [ ] d) Opens a file for reading and writing, truncating the file first

**Explanation:** `'a+'` opens the file for both appending and reading.

---

**10.** Which function would you use to check if a file exists at a given path?

- [ ] a) `os.isfile()`
- [ ] b) `os.path.exists()`
- [ ] c) `os.check()`
- [x] d) `os.path.isfile()`

**Explanation:** `os.path.isfile()` checks if a given path is a file and exists.

---

**11.** The `write()` method can only write which type of data to a file?

- [ ] a) Integers
- [x] b) Strings
- [ ] c) Bytes
- [ ] d) Floats

**Explanation:** The `write()` method writes strings to a text file. For binary files, you would use bytes.

---

**12.** Using `open('file.txt', 'w')` will result in what action if `'file.txt'` does not exist?

- [ ] a) Raise a `FileNotFoundError`
- [x] b) Create a new file named `'file.txt'`
- [ ] c) Append data to `'file.txt'`
- [ ] d) Open the file in read-only mode

**Explanation:** The `'w'` mode creates a new file if it doesn't exist.

---

**13.** The `read()` method without arguments reads:

- [ ] a) The next line of the file
- [ ] b) A specified number of bytes
- [x] c) The entire file content
- [ ] d) The last line of the file

**Explanation:** Without arguments, `read()` reads the entire file content.

---

**14.** Binary files must be opened with modes that include `'b'`, such as `'rb'` or `'wb'`. What does the `'b'` stand for?

- [ ] a) Buffer
- [x] b) Binary
- [ ] c) Backup
- [ ] d) Bitwise

**Explanation:** The `'b'` in file modes stands for binary.

---

**15.** The `tell()` method returns:

- [ ] a) The size of the file
- [x] b) The current position of the file cursor
- [ ] c) The line number
- [ ] d) The encoding of the file

**Explanation:** `tell()` returns the current position of the file cursor in bytes.

---

**16.** What happens if you try to write to a file opened in read-only mode `'r'`?

- [ ] a) Data is written successfully
- [ ] b) The file gets truncated
- [ ] c) A `ValueError` is raised
- [x] d) An `UnsupportedOperation` error is raised

**Explanation:** Writing to a file opened in `'r'` mode raises an `io.UnsupportedOperation` error.

---

**17.** Which method would you use to read one line at a time from a file?

- [ ] a) `read()`
- [x] b) `readline()`
- [ ] c) `readlines()`
- [ ] d) `readchar()`

**Explanation:** `readline()` reads one line at a time.

---

**18.** To ensure a file is properly closed after its suite finishes, which statement is recommended?

- [ ] a) `try-except` block
- [x] b) `with` statement
- [ ] c) `finally` block
- [ ] d) `def` statement

**Explanation:** The `with` statement ensures the file is closed automatically.

---

**19.** Which of the following modes will NOT create a file if it does not exist?

- [ ] a) `'w'`
- [ ] b) `'a'`
- [x] c) `'r'`
- [ ] d) `'w+'`

**Explanation:** The `'r'` mode requires the file to exist; otherwise, it raises an error.

---

**20.** How can you read a file's content as a list of lines without the newline characters?

- [x] a) Use `file.read().splitlines()`
- [ ] b) Use `file.readlines()`
- [ ] c) Use `file.readline()`
- [ ] d) Use `file.read()`

**Explanation:** `splitlines()` splits the content into lines and removes newline characters.

---

**21.** What is the correct way to open a file for both reading and writing without truncating it?

- [ ] a) `open('file.txt', 'w+')`
- [x] b) `open('file.txt', 'r+')`
- [ ] c) `open('file.txt', 'a+')`
- [ ] d) `open('file.txt', 'rw')`

**Explanation:** `'r+'` opens the file for reading and writing without truncating it.

---

**22.** Which function is used to delete a file in Python?

- [x] a) `os.remove()`
- [ ] b) `os.delete()`
- [ ] c) `os.unlink()`
- [ ] d) `os.erase()`

**Explanation:** `os.remove()` deletes a file.

---

**23.** To read a binary file as text, you should:

- [ ] a) Open it with mode `'r'`
- [ ] b) Open it with mode `'rb'`
- [x] c) Open it with mode `'r'` and specify encoding
- [ ] d) You cannot read binary files as text

**Explanation:** Opening with `'r'` and specifying the correct encoding allows you to read the file as text.

---

**24.** If you need to write Unicode characters to a file, you should:

- [ ] a) Use binary mode `'wb'`
- [x] b) Specify the encoding in `open()`
- [ ] c) Use the `encode()` method on strings
- [ ] d) Write the characters directly without any special handling

**Explanation:** Specifying the encoding ensures Unicode characters are handled correctly.

---

**25.** Which method can be used to read a specific number of characters from a file?

- [ ] a) `readchars(n)`
- [x] b) `read(n)`
- [ ] c) `readline(n)`
- [ ] d) `readbytes(n)`

**Explanation:** `read(n)` reads `n` characters from the file.

---

**26.** What does the `'x'` mode do when opening a file?

- [x] a) Opens a file for exclusive creation; fails if the file exists
- [ ] b) Opens a file for appending; creates it if it doesn't exist
- [ ] c) Opens a file for reading and writing
- [ ] d) Opens a file and truncates it to zero length

**Explanation:** The `'x'` mode is for exclusive creation; it raises an error if the file already exists.

---

**27.** How can you get the current working directory in Python?

- [x] a) `os.getcwd()`
- [ ] b) `os.curdir()`
- [ ] c) `os.pardir()`
- [ ] d) `os.getpwd()`

**Explanation:** `os.getcwd()` returns the current working directory.

---

**28.** Which of the following is a correct way to write multiple lines to a file?

- [ ] a) `file.write(lines)`
- [x] b) `file.writelines(lines)`
- [ ] c) `file.write(*lines)`
- [ ] d) `file.writeline(lines)`

**Explanation:** `writelines()` writes a list of strings to the file.

---

**29.** To copy a file from one location to another, which module can you use?

- [ ] a) `os`
- [ ] b) `sys`
- [x] c) `shutil`
- [ ] d) `fileutil`

**Explanation:** The `shutil` module provides functions for high-level file operations like copying.

---

**30.** Which of the following methods can be used to rename a file?

- [x] a) `os.rename()`
- [ ] b) `os.move()`
- [ ] c) `os.change()`
- [ ] d) `os.modify()`

**Explanation:** `os.rename()` is used to rename files or directories.

---
