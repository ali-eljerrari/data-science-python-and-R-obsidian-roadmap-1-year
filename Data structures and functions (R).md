
---


R is a powerful language and environment for statistical computing and graphics. Understanding its data structures and how to manipulate them with functions is essential for data analysis, statistical modeling, and programming in R. This guide covers the fundamental data structures in R and how to work with functions effectively.

## Table of Contents

1. [Introduction to R Data Structures](#1-introduction)
2. [Vectors](#2-vectors)
   - [Creating Vectors](#2-1-creating-vectors)
   - [Vector Operations](#2-2-vector-operations)
3. [Matrices](#3-matrices)
   - [Creating Matrices](#3-1-creating-matrices)
   - [Matrix Operations](#3-2-matrix-operations)
4. [Arrays](#4-arrays)
5. [Lists](#5-lists)
   - [Creating Lists](#5-1-creating-lists)
   - [Accessing List Elements](#5-2-accessing-list-elements)
6. [Data Frames](#6-data-frames)
   - [Creating Data Frames](#6-1-creating-data-frames)
   - [Manipulating Data Frames](#6-2-manipulating-data-frames)
7. [Factors](#7-factors)
   - [Creating Factors](#7-1-creating-factors)
   - [Factor Levels](#7-2-factor-levels)
8. [Functions in R](#8-functions-in-r)
   - [Creating Functions](#8-1-creating-functions)
   - [Function Arguments](#8-2-function-arguments)
   - [Returning Values](#8-3-returning-values)
   - [Default Arguments](#8-4-default-arguments)
   - [Anonymous Functions](#8-5-anonymous-functions)
9. [Control Structures](#9-control-structures)
   - [`if`, `else`, and `else if`](#9-1-if-else-else-if)
   - [`for` Loops](#9-2-for-loops)
   - [`while` Loops](#9-3-while-loops)
   - [`repeat` Loops](#9-4-repeat-loops)
10. [Apply Functions](#10-apply-functions)
    - [`apply()`](#10-1-apply)
    - [`lapply()` and `sapply()`](#10-2-lapply-sapply)
    - [`tapply()`](#10-3-tapply)
11. [Best Practices](#11-best-practices)
12. [Conclusion](#12-conclusion)

---

<a name="1-introduction"></a>
## 1. Introduction to R Data Structures

R has several built-in data structures, each serving different purposes. Understanding these structures is crucial for effective data manipulation and analysis.

**Primary Data Structures:**

- **Vectors**
- **Matrices**
- **Arrays**
- **Lists**
- **Data Frames**
- **Factors**

---

<a name="2-vectors"></a>
## 2. Vectors

Vectors are the most basic data structures in R. They are sequences of elements of the same basic type.

<a name="2-1-creating-vectors"></a>
### 2.1 Creating Vectors

- **Numeric Vector:**

  ```R
  num_vec <- c(1, 2, 3, 4, 5)
  ```

- **Character Vector:**

  ```R
  char_vec <- c("apple", "banana", "cherry")
  ```

- **Logical Vector:**

  ```R
  log_vec <- c(TRUE, FALSE, TRUE)
  ```

**Sequence Generation:**

- Using `:` operator:

  ```R
  seq_vec <- 1:10  # Creates a vector from 1 to 10
  ```

- Using `seq()` function:

  ```R
  seq_vec <- seq(from = 1, to = 10, by = 2)  # 1, 3, 5, 7, 9
  ```

- Using `rep()` function:

  ```R
  rep_vec <- rep(5, times = 3)  # 5, 5, 5
  ```

<a name="2-2-vector-operations"></a>
### 2.2 Vector Operations

- **Element-wise Operations:**

  ```R
  vec1 <- c(1, 2, 3)
  vec2 <- c(4, 5, 6)
  sum_vec <- vec1 + vec2  # 5, 7, 9
  ```

- **Accessing Elements:**

  ```R
  vec <- c("a", "b", "c", "d", "e")
  elem <- vec[2]  # "b"
  ```

- **Slicing Vectors:**

  ```R
  sub_vec <- vec[2:4]  # "b", "c", "d"
  ```

- **Logical Indexing:**

  ```R
  num_vec <- c(10, 20, 30, 40, 50)
  filtered_vec <- num_vec[num_vec > 25]  # 30, 40, 50
  ```

---

<a name="3-matrices"></a>
## 3. Matrices

Matrices are two-dimensional arrays where each element has the same mode (numeric, character, etc.).

<a name="3-1-creating-matrices"></a>
### 3.1 Creating Matrices

- **Using `matrix()` Function:**

  ```R
  mat <- matrix(data = 1:6, nrow = 2, ncol = 3)
  ```

- **By Binding Vectors:**

  - **Row Binding (`rbind`):**

    ```R
    row1 <- c(1, 2, 3)
    row2 <- c(4, 5, 6)
    mat <- rbind(row1, row2)
    ```

  - **Column Binding (`cbind`):**

    ```R
    col1 <- c(1, 2)
    col2 <- c(3, 4)
    col3 <- c(5, 6)
    mat <- cbind(col1, col2, col3)
    ```

<a name="3-2-matrix-operations"></a>
### 3.2 Matrix Operations

- **Element Access:**

  ```R
  elem <- mat[1, 2]  # Access element at first row, second column
  ```

- **Subsetting:**

  ```R
  sub_mat <- mat[1:2, 2:3]  # Sub-matrix
  ```

- **Matrix Multiplication:**

  ```R
  mat1 <- matrix(1:4, nrow = 2)
  mat2 <- matrix(5:8, nrow = 2)
  prod_mat <- mat1 %*% mat2  # Matrix multiplication
  ```

- **Transpose:**

  ```R
  t_mat <- t(mat)  # Transpose of the matrix
  ```

---

<a name="4-arrays"></a>
## 4. Arrays

Arrays are multi-dimensional generalizations of matrices.

**Creating an Array:**

```R
arr <- array(data = 1:8, dim = c(2, 2, 2))
```

**Accessing Array Elements:**

```R
elem <- arr[1, 2, 2]  # Element in position [1, 2, 2]
```

---

<a name="5-lists"></a>
## 5. Lists

Lists are heterogeneous data structures that can contain elements of different types, including other lists.

<a name="5-1-creating-lists"></a>
### 5.1 Creating Lists

```R
my_list <- list(
  name = "John",
  age = 30,
  scores = c(85, 90, 95),
  address = list(street = "Main St", city = "Anytown")
)
```

<a name="5-2-accessing-list-elements"></a>
### 5.2 Accessing List Elements

- **Using `$` Operator:**

  ```R
  name <- my_list$name  # "John"
  ```

- **Using Double Brackets `[[ ]]`:**

  ```R
  age <- my_list[[2]]  # 30
  city <- my_list$address$city  # "Anytown"
  ```

- **Using Single Brackets `[ ]`:**

  ```R
  sub_list <- my_list[1:2]  # Returns a list with first two elements
  ```

---

<a name="6-data-frames"></a>
## 6. Data Frames

Data frames are table-like structures where each column can contain different types of data, similar to SQL tables or spreadsheets.

<a name="6-1-creating-data-frames"></a>
### 6.1 Creating Data Frames

- **From Vectors:**

  ```R
  names <- c("Alice", "Bob", "Charlie")
  ages <- c(25, 30, 35)
  df <- data.frame(Name = names, Age = ages)
  ```

- **Reading from Files:**

  ```R
  df <- read.csv("data.csv")
  ```

<a name="6-2-manipulating-data-frames"></a>
### 6.2 Manipulating Data Frames

- **Accessing Columns:**

  ```R
  df$Name  # Returns the 'Name' column
  ```

- **Subsetting Rows and Columns:**

  ```R
  sub_df <- df[1:2, ]  # First two rows
  sub_df <- df[, c("Name", "Age")]  # Specific columns
  ```

- **Adding New Columns:**

  ```R
  df$Salary <- c(50000, 60000, 70000)
  ```

- **Filtering Rows:**

  ```R
  high_earners <- df[df$Salary > 55000, ]
  ```

---

<a name="7-factors"></a>
## 7. Factors

Factors are used to represent categorical data.

<a name="7-1-creating-factors"></a>
### 7.1 Creating Factors

```R
colors <- c("red", "green", "blue", "green", "red")
factor_colors <- factor(colors)
```

<a name="7-2-factor-levels"></a>
### 7.2 Factor Levels

- **Viewing Levels:**

  ```R
  levels(factor_colors)  # "blue", "green", "red"
  ```

- **Changing Levels:**

  ```R
  levels(factor_colors) <- c("Blue", "Green", "Red")
  ```

---

<a name="8-functions-in-r"></a>
## 8. Functions in R

Functions are first-class objects in R. They can be created, stored in variables, and passed as arguments.

<a name="8-1-creating-functions"></a>
### 8.1 Creating Functions

```R
add_numbers <- function(a, b) {
  return(a + b)
}
```

<a name="8-2-function-arguments"></a>
### 8.2 Function Arguments

- **Positional Arguments:**

  ```R
  result <- add_numbers(5, 3)  # 8
  ```

- **Named Arguments:**

  ```R
  result <- add_numbers(a = 5, b = 3)
  ```

<a name="8-3-returning-values"></a>
### 8.3 Returning Values

- **Using `return()`:**

  ```R
  square <- function(x) {
    return(x * x)
  }
  ```

- **Implicit Return:**

  ```R
  square <- function(x) {
    x * x  # Last expression is returned
  }
  ```

<a name="8-4-default-arguments"></a>
### 8.4 Default Arguments

```R
greet <- function(name = "World") {
  paste("Hello,", name)
}

greet()          # "Hello, World"
greet("Alice")   # "Hello, Alice"
```

<a name="8-5-anonymous-functions"></a>
### 8.5 Anonymous Functions

Used primarily in apply functions.

```R
sapply(1:5, function(x) x^2)  # Squares of numbers 1 to 5
```

---

<a name="9-control-structures"></a>
## 9. Control Structures

Control structures allow you to control the flow of execution.

<a name="9-1-if-else-else-if"></a>
### 9.1 `if`, `else`, and `else if`

```R
x <- 10

if (x > 0) {
  print("Positive")
} else if (x == 0) {
  print("Zero")
} else {
  print("Negative")
}
```

<a name="9-2-for-loops"></a>
### 9.2 `for` Loops

```R
for (i in 1:5) {
  print(i)
}
```

<a name="9-3-while-loops"></a>
### 9.3 `while` Loops

```R
count <- 1
while (count <= 5) {
  print(count)
  count <- count + 1
}
```

<a name="9-4-repeat-loops"></a>
### 9.4 `repeat` Loops

```R
count <- 1
repeat {
  print(count)
  count <- count + 1
  if (count > 5) {
    break
  }
}
```

---

<a name="10-apply-functions"></a>
## 10. Apply Functions

Apply functions are used to apply a function over elements of a data structure.

<a name="10-1-apply"></a>
### 10.1 `apply()`

Used on matrices or arrays.

```R
mat <- matrix(1:9, nrow = 3)
row_sums <- apply(mat, 1, sum)  # Sum over rows
col_sums <- apply(mat, 2, sum)  # Sum over columns
```

<a name="10-2-lapply-sapply"></a>
### 10.2 `lapply()` and `sapply()`

- **`lapply()`:** Returns a list.

  ```R
  num_list <- list(a = 1:5, b = 6:10)
  lapply(num_list, mean)  # Returns a list of means
  ```

- **`sapply()`:** Simplifies the result (vector or matrix).

  ```R
  sapply(num_list, mean)  # Returns a vector of means
  ```

<a name="10-3-tapply"></a>
### 10.3 `tapply()`

Applies a function over subsets defined by a factor.

```R
ages <- c(25, 30, 35, 40, 45)
groups <- factor(c("A", "B", "A", "B", "A"))
group_means <- tapply(ages, groups, mean)
```

---

<a name="11-best-practices"></a>
## 11. Best Practices

- **Vectorization:** Prefer vectorized operations over loops for better performance.
- **Clear Function Names:** Use descriptive names for functions and variables.
- **Document Your Code:** Use comments and Roxygen for functions.
- **Avoid Global Variables:** Keep variables within the scope of functions when possible.
- **Error Handling:** Use `tryCatch()` to handle exceptions.

---

<a name="12-conclusion"></a>
## 12. Conclusion

Understanding R's data structures and how to manipulate them with functions is foundational for effective data analysis. By mastering vectors, matrices, arrays, lists, data frames, and factors, along with control structures and apply functions, you can write efficient and robust R code.

**Next Steps:**

- Practice by working on real datasets.
- Explore advanced topics like object-oriented programming in R (S3, S4, R6).
- Learn about packages like `dplyr` and `data.table` for data manipulation.

---

# Data Structures and Functions in R: Exam with Answers

Below are 30 multiple-choice questions on Data Structures and Functions in R. Each question has four options, and the correct answer is indicated with a checked checkbox. Explanations are provided for clarity.

---

## **Multiple Choice Questions**

**1.** Which of the following functions is used to create a vector in R?

- [ ] a) `matrix()`
- [x] b) `c()`
- [ ] c) `list()`
- [ ] d) `data.frame()`

**Explanation:** The `c()` function (concatenate) is used to create vectors in R.

---

**2.** What is the output of the following R code?

```R
x <- 1:5
y <- x * 2
print(y)
```

- [ ] a) `1 2 3 4 5`
- [x] b) `2 4 6 8 10`
- [ ] c) `1 4 9 16 25`
- [ ] d) `Error`

**Explanation:** The vector `x` is multiplied element-wise by 2, resulting in `2 4 6 8 10`.

---

**3.** Which function is used to create a data frame in R?

- [ ] a) `matrix()`
- [ ] b) `list()`
- [ ] c) `c()`
- [x] d) `data.frame()`

**Explanation:** The `data.frame()` function is used to create data frames.

---

**4.** How do you access the third element of a vector `v` in R?

- [ ] a) `v{3}`
- [x] b) `v[3]`
- [ ] c) `v(3)`
- [ ] d) `v[[3]]`

**Explanation:** `v[3]` accesses the third element of the vector `v`.

---

**5.** What is the primary difference between a matrix and a data frame in R?

- [ ] a) Matrices can only contain numeric data
- [ ] b) Data frames can only contain character data
- [x] c) Matrices contain elements of the same type; data frames can have different types
- [ ] d) There is no difference

**Explanation:** Matrices are homogeneous, while data frames can have columns of different data types.

---

**6.** Which function would you use to apply a function to each element of a list in R, returning a list?

- [ ] a) `apply()`
- [ ] b) `sapply()`
- [x] c) `lapply()`
- [ ] d) `tapply()`

**Explanation:** `lapply()` applies a function over a list and returns a list.

---

**7.** How do you create a sequence of numbers from 1 to 10 in R?

- [ ] a) `seq(10)`
- [x] b) `1:10`
- [ ] c) `c(1,10)`
- [ ] d) `sequence(10)`

**Explanation:** `1:10` creates a sequence from 1 to 10.

---

**8.** Which of the following is used to combine two data frames vertically (adding rows) in R?

- [ ] a) `cbind()`
- [x] b) `rbind()`
- [ ] c) `merge()`
- [ ] d) `append()`

**Explanation:** `rbind()` binds data frames by rows.

---

**9.** In R, which data structure would you use to store heterogeneous data types?

- [ ] a) Vector
- [ ] b) Matrix
- [x] c) List
- [ ] d) Array

**Explanation:** Lists can store elements of different types.

---

**10.** What will be the result of the following code?

```R
x <- c(1, 2, NA, 4)
mean(x)
```

- [ ] a) `2.5`
- [ ] b) `NA`
- [x] c) `NA` (Need to handle missing values)
- [ ] d) `Error`

**Explanation:** The presence of `NA` results in `NA`. Use `mean(x, na.rm = TRUE)` to calculate the mean ignoring `NA`.

---

**11.** How do you access the "age" column in a data frame `df`?

- [x] a) `df$age`
- [ ] b) `df[age]`
- [ ] c) `df["age"]`
- [ ] d) `df[[age]]`

**Explanation:** `df$age` accesses the "age" column.

---

**12.** Which function is used to read a CSV file into R?

- [ ] a) `read.table()`
- [x] b) `read.csv()`
- [ ] c) `read.xlsx()`
- [ ] d) `load()`

**Explanation:** `read.csv()` reads a CSV file into a data frame.

---

**13.** What is the output of the following code?

```R
rep(1:3, times = 2)
```

- [ ] a) `1 1 2 2 3 3`
- [x] b) `1 2 3 1 2 3`
- [ ] c) `1 1 1 2 2 2 3 3 3`
- [ ] d) `Error`

**Explanation:** Repeats the sequence `1 2 3` two times.

---

**14.** Which function would you use to sort a vector `v` in ascending order?

- [ ] a) `order(v)`
- [x] b) `sort(v)`
- [ ] c) `rank(v)`
- [ ] d) `sequence(v)`

**Explanation:** `sort(v)` returns the sorted vector.

---

**15.** How do you create a matrix with 2 rows and 3 columns filled with zeros?

- [ ] a) `matrix(0, nrow = 3, ncol = 2)`
- [x] b) `matrix(0, nrow = 2, ncol = 3)`
- [ ] c) `zeros(2,3)`
- [ ] d) `array(0, dim = c(2,3))`

**Explanation:** `matrix(0, nrow = 2, ncol = 3)` creates the required matrix.

---

**16.** Which function is used to apply a function over the margins of an array or matrix?

- [x] a) `apply()`
- [ ] b) `lapply()`
- [ ] c) `sapply()`
- [ ] d) `tapply()`

**Explanation:** `apply()` is used for applying functions over array or matrix margins.

---

**17.** What will `length(list(a = 1, b = 2:4, c = "text"))` return?

- [ ] a) `3`
- [x] b) `3`
- [ ] c) `4`
- [ ] d) `Error`

**Explanation:** The list has three elements.

---

**18.** In R, which of the following is TRUE about factors?

- [ ] a) They are used to store numerical data
- [ ] b) They cannot be ordered
- [x] c) They are used to handle categorical data
- [ ] d) They are the same as character vectors

**Explanation:** Factors are used for categorical data.

---

**19.** How do you define a function in R?

- [ ] a) `def function_name() {}`
- [x] b) `function_name <- function() {}`
- [ ] c) `function function_name() {}`
- [ ] d) `fun function_name() {}`

**Explanation:** Functions are defined using the `<- function()` syntax.

---

**20.** What does the `str()` function do when applied to an object in R?

- [ ] a) Converts it to a string
- [ ] b) Prints its structure
- [x] c) Displays the internal structure of an R object
- [ ] d) Summarizes statistical information

**Explanation:** `str()` compactly displays the internal structure of an object.

---

**21.** Which of the following is a valid way to create a numeric vector of zeros with length 5?

- [x] a) `numeric(5)`
- [ ] b) `zeros(5)`
- [ ] c) `rep(0, times = 6)`
- [ ] d) `array(0, dim = 5)`

**Explanation:** `numeric(5)` creates a numeric vector of zeros with length 5.

---

**22.** In a data frame `df`, how do you filter rows where the "age" column is greater than 30?

- [ ] a) `df[df$age < 30, ]`
- [x] b) `df[df$age > 30, ]`
- [ ] c) `subset(df, age < 30)`
- [ ] d) `df[age > 30]`

**Explanation:** `df[df$age > 30, ]` filters rows where "age" is greater than 30.

---

**23.** What is the purpose of the `return()` function in R?

- [ ] a) To exit a loop
- [x] b) To specify the value to be returned by a function
- [ ] c) To print the value of a variable
- [ ] d) To restart a function

**Explanation:** `return()` specifies the value to return from a function.

---

**24.** Which function would you use to combine two vectors `v1` and `v2` as columns in a data frame?

- [ ] a) `rbind(v1, v2)`
- [x] b) `data.frame(v1, v2)`
- [ ] c) `cbind(v1, v2)`
- [ ] d) `merge(v1, v2)`

**Explanation:** `data.frame(v1, v2)` combines vectors as columns.

---

**25.** How do you create an anonymous function in R?

- [ ] a) `function_name <- function(x) { x + 1 }`
- [ ] b) `anonymous_function(x) { x + 1 }`
- [x] c) `function(x) { x + 1 }`
- [ ] d) `fun(x) { x + 1 }`

**Explanation:** `function(x) { x + 1 }` defines an anonymous function.

---

**26.** What is the output of `class(c(1, 2, 3))` in R?

- [ ] a) `"array"`
- [ ] b) `"matrix"`
- [x] c) `"numeric"`
- [ ] d) `"vector"`

**Explanation:** The class of a numeric vector is `"numeric"`.

---

**27.** Which of the following control structures is NOT available in R?

- [ ] a) `if...else`
- [ ] b) `for` loop
- [ ] c) `while` loop
- [x] d) `switch` case

**Explanation:** While R has a `switch()` function, it does not have a `switch` case control structure like in other languages.

---

**28.** How do you remove missing values (`NA`) from a vector `v`?

- [ ] a) `v[!is.na(v)]`
- [x] b) `v <- v[!is.na(v)]`
- [ ] c) `remove.na(v)`
- [ ] d) `omit.na(v)`

**Explanation:** `v <- v[!is.na(v)]` removes `NA` values from `v`.

---

**29.** What is the purpose of the `args()` function in R?

- [ ] a) To execute a function
- [x] b) To display the arguments of a function
- [ ] c) To list all functions in the environment
- [ ] d) To return the values of a function

**Explanation:** `args()` displays the arguments of a function.

---

**30.** Which function is used to write a data frame `df` to a CSV file?

- [ ] a) `write()`
- [ ] b) `save.csv()`
- [x] c) `write.csv(df, "filename.csv")`
- [ ] d) `export.csv(df)`

**Explanation:** `write.csv()` writes a data frame to a CSV file.

---

