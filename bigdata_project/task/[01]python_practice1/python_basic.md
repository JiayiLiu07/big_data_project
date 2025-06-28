## Operators

### **1. Arithmetic Operators**
算术运算符: 加、减、乘、除、取模、幂运算、取整除
- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `%` (Modulus)
- `**` (Exponentiation)
- `//` (Floor Division)

---

### **2. Comparison Operators**
比较运算符: 等于、不等于、大于、小于、大于等于、小于等于
- `==` (Equal to)
- `!=` (Not equal to)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

---

### **3. Logical Operators**
逻辑运算符: 与、或、非
- `and` (Logical AND)
- `or` (Logical OR)
- `not` (Logical NOT)

---

### **4. Assignment Operators**
赋值运算符: 简单赋值、加赋值、减赋值、乘赋值、
除赋值、取模赋值、幂赋值、取整除赋值
- `=` (Simple assignment)
- `+=` (Add and assign)
- `-=` (Subtract and assign)
- `*=` (Multiply and assign)
- `/=` (Divide and assign)
- `%=` (Modulus and assign)
- `**=` (Exponentiation and assign)
- `//=` (Floor division and assign)

---

### **5. Bitwise Operators(Optional)**
位运算符 (可选): 按位与、按位或、按位异或、按位非、左移、右移
- `&` (Bitwise AND)
- `|` (Bitwise OR)
- `^` (Bitwise XOR)
- `~` (Bitwise NOT)
- `<<` (Bitwise left shift)
- `>>` (Bitwise right shift)

---

### **6. Membership Operators**
成员运算符: 在、不在
- `in` (Checks if a value is in a sequence)
- `not in` (Checks if a value is not in a sequence)

---

### **7. Identity Operators**
身份运算符: 是、不是
- `is` (Checks if two objects are the same object in memory)
- `is not` (Checks if two objects are not the same object in memory)

## basic data type
基本数据类型
### **1. Strings**
字符串: 用于存储文本，不可变，支持拼接、重复、切片、长度获取、格式化等操作
A **string** is a sequence of characters used to store text. Strings in Python are **immutable**, meaning you cannot modify a string once it is created. Instead, you can create new strings based on existing ones.

#### **Creating Strings**
```python
s1 = "Hello, World!"  # Double quotes
s2 = 'Python is fun.'  # Single quotes
s3 = """This is a
multi-line string."""  # Triple quotes for multi-line strings
```

#### **String Operations**
1. **Concatenation**
   ```python
   s1 = "Hello"
   s2 = "World"
   result = s1 + " " + s2  # Concatenate strings using the `+` operator
   print(result)  # Output: Hello World
   ```

2. **Repetition**
   ```python
   s = "Python"
   print(s * 3)  # Output: PythonPythonPython
   ```

3. **Slicing**
   ```python
   s = "Python"
   print(s[0])  # Output: P
   print(s[1:4])  # Output: yth (characters from index 1 to 3)
   print(s[:3])  # Output: Pyt (characters from start to index 2)
   print(s[3:])  # Output: hon (characters from index 3 to end)
   ```

4. **String Length**
   ```python
   s = "Hello"
   print(len(s))  # Output: 5
   ```

5. **String Methods**
   - **Case Conversion**
     ```python
     s = "hello"
     print(s.upper())  # Output: HELLO
     print(s.capitalize())  # Output: Hello
     ```

   - **Finding and Replacing**
     ```python
     s = "hello world"
     print(s.find("world"))  # Output: 6 (index where "world" starts)
     print(s.replace("world", "Python"))  # Output: hello Python
     ```

   - **Splitting and Joining**
     ```python
     s = "apple,banana,cherry"
     fruits = s.split(",")  # Split string by comma
     print(fruits)  # Output: ['apple', 'banana', 'cherry']

     joined = ",".join(fruits)  # Join list of strings with a comma
     print(joined)  # Output: apple,banana,cherry
     ```

   - **Stripping Whitespace**
     ```python
     s = "   hello world   "
     print(s.strip())  # Output: hello world (removes leading and trailing whitespace)
     ```

6. **Formatted Strings**
   - **Using `%` Formatting**
     ```python
     name = "Alice"
     age = 25
     print("My name is %s and I am %d years old." % (name, age))
     ```

   - **Using `str.format()`**
     ```python
     print("My name is {} and I am {} years old.".format(name, age))
     ```

   - **Using f-strings (Python 3.6+)**
     ```python
     print(f"My name is {name} and I am {age} years old.")
     ```

---

### **2. Lists**
列表: 可变序列，支持访问、切片、修改、添加、删除、列表推导式等操作
A **list** is a mutable sequence of elements that can store multiple items (of different types). Lists are ordered, meaning the elements have a specific order that can be changed.

#### **Creating Lists**
```python
my_list = [1, 2, 3, 4]  # List of integers
fruits = ["apple", "banana", "cherry"]  # List of strings
mixed_list = [1, "hello", 3.14, True]  # List with mixed data types
```

#### **List Operations**
1. **Accessing Elements**
   ```python
   fruits = ["apple", "banana", "cherry"]
   print(fruits[0])  # Output: apple
   print(fruits[-1])  # Output: cherry (negative indexing starts from the end)
   ```

2. **Slicing**
   ```python
   numbers = [0, 1, 2, 3, 4, 5]
   print(numbers[2:5])  # Output: [2, 3, 4]
   print(numbers[:3])  # Output: [0, 1, 2]
   print(numbers[3:])  # Output: [3, 4, 5]
   ```

3. **Modifying Elements**
   ```python
   fruits = ["apple", "banana", "cherry"]
   fruits[1] = "orange"  # Modify the element at index 1
   print(fruits)  # Output: ['apple', 'orange', 'cherry']
   ```

4. **Adding Elements**
   ```python
   fruits = ["apple", "banana"]
   fruits.append("cherry")  # Add an element to the end of the list
   print(fruits)  # Output: ['apple', 'banana', 'cherry']

   fruits.extend(["orange", "grape"])  # Add multiple elements
   print(fruits)  # Output: ['apple', 'banana', 'cherry', 'orange', 'grape']
   ```

5. **Removing Elements**
   ```python
   fruits = ["apple", "banana", "cherry"]
   fruits.remove("banana")  # Remove an element by value
   print(fruits)  # Output: ['apple', 'cherry']

   del fruits[1]  # Remove an element by index
   print(fruits)  # Output: ['apple']
   ```

6. **List Comprehensions**
   ```python
   squares = [x**2 for x in range(5)]  # Create a list of squares
   print(squares)  # Output: [0, 1, 4, 9, 16]

   even_squares = [x**2 for x in range(10) if x % 2 == 0]  # With a condition
   print(even_squares)  # Output: [0, 4, 16, 36, 64]
   ```

7. **List Methods**
   - **Sorting**
     ```python
     numbers = [3, 1, 4, 1, 5, 9]
     numbers.sort()  # Sort the list in place
     print(numbers)  # Output: [1, 1, 3, 4, 5, 9]

     sorted_numbers = sorted(numbers)  # Return a new sorted list
     print(sorted_numbers)  # Output: [1, 1, 3, 4, 5, 9]
     ```

   - **Reversing**
     ```python
     numbers.reverse()
     print(numbers)  # Output: [9, 5, 4, 3, 1, 1]
     ```

   - **Finding Elements**
     ```python
     print(numbers.index(4))  # Output: 2 (index of the element)
     print(numbers.count(1))  # Output: 2 (number of occurrences)
     ```

---

### **3. Dictionaries**
字典: 可变键值对集合，支持访问、修改、添加、删除等操作
A **dictionary** is a mutable collection of key-value pairs. Each key must be unique and immutable (e.g., strings, numbers, tuples). Dictionaries are unordered (before Python 3.7) but maintain insertion order in Python 3.7+.

#### **Creating Dictionaries**
```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}  # Using curly braces
another_dict = dict(name="Bob", age=30, city="Los Angeles")  # Using the dict() function
```

#### **Dictionary Operations**
1. **Accessing Values**
   ```python
   my_dict = {"name": "Alice", "age": 25, "city": "New York"}
   print(my_dict["name"])  # Output: Alice
   print(my_dict.get("age"))  # Output: 25 (using the get method)
   ```

2. **Modifying Values**
   ```python
   my_dict["age"] = 26  # Modify the value associated with a key
   print(my_dict)  # Output: {'name': 'Alice', 'age': 26, 'city': 'New York'}
   ```

3. **Adding Key-Value Pairs**
   ```python
   my_dict["email"] = "alice@example.com"  # Add a new key-value pair
   print(my_dict)  # Output: {'name': 'Alice', 'age': 26, 'city': 'New York', 'email': 'alice@example.com'}
   ```

4. **Removing Key-Value Pairs**
   ```python
   del my_dict["city"]  # Remove a key-value pair by key
   print(my_dict)  # Output

## Control flow 
控制流
### **1. Conditional Statements (`if`, `elif`, `else`)**
条件语句: if、elif、else，根据条件执行不同的代码块
Conditional statements allow you to execute different code blocks based on certain conditions.

#### Syntax:
```python
if condition1:
    # Code block 1 (executed if condition1 is True)
elif condition2:
    # Code block 2 (executed if condition2 is True)
else:
    # Code block 3 (executed if none of the conditions are True)
```

#### Example:
```python
age = 20

if age < 18:
    print("You are a minor.")
elif age >= 18 and age < 65:
    print("You are an adult.")
else:
    print("You are a senior citizen.")
```

**Output:**
```
You are an adult.
```

---

### **2. Loops**
循环: for 循环遍历序列，while 循环根据条件重复执行代码
Loops allow you to repeat a block of code multiple times. Python has two main types of loops: `for` loops and `while` loops.

#### **a. `for` Loop**
A `for` loop iterates over a sequence (such as a list, tuple, string, or range) and executes a block of code for each item in the sequence.

##### Syntax:
```python
for item in sequence:
    # Code block (executed for each item in the sequence)
```

##### Example:
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

##### Using `range()`:
```python
for i in range(5):  # Iterates from 0 to 4
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

#### **b. `while` Loop**
A `while` loop repeatedly executes a block of code as long as a condition remains `True`.

##### Syntax:
```python
while condition:
    # Code block (executed as long as the condition is True)
```

##### Example:
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

---

### **3. Loop Control Statements**
循环控制语句: break、continue、pass，控制循环的执行流程
Python provides statements to control the flow within loops, such as `break`, `continue`, and `pass`.

#### **a. `break`**
The `break` statement is used to exit the loop prematurely when a certain condition is met.

##### Example:
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

#### **b. `continue`**
The `continue` statement skips the current iteration of the loop and moves to the next iteration.

##### Example:
```python
for i in range(10):
    if i % 2 == 0:
        continue
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

#### **c. `pass`**
The `pass` statement is a placeholder used when a statement is required syntactically, but you do not want any code to execute.

##### Example:
```python
for i in range(5):
    if i == 3:
        pass  # Placeholder for future code
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

---

### **4. `try` and `except` Blocks**
异常处理: try、except、else、finally，处理代码中可能出现的异常
These blocks are used for exception handling to manage errors gracefully. They allow you to execute code that might raise an exception and handle it without crashing the program.

#### Syntax:
```python
try:
    # Code that might raise an exception
except SomeException as error:
    # Code to handle the exception
else:
    # Code that runs if no exception is raised
finally:
    # Code that runs regardless of whether an exception occurred
```

#### Example:
```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
else:
    print("No error occurred.")
finally:
    print("This will always run.")
```

**Output:**
```
Error: division by zero
This will always run.
```

---

### **5. `match` Statement (Python 3.10+)**
match 语句 (Python 3.10): 模式匹配，根据不同模式执行不同的代码块
The `match` statement is a pattern-matching construct that allows you to compare a value against multiple patterns and execute different code blocks based on the match.

#### Syntax:
```python
match value:
    case pattern1:
        # Code block 1
    case pattern2:
        # Code block 2
    case _:
        # Default case (optional)
```

#### Example:
```python
score = 85

match score:
    case score if score >= 90:
        print("Grade: A")
    case score if score >= 80:
        print("Grade: B")
    case score if score >= 70:
        print("Grade: C")
    case _:
        print("Grade: F")
```

**Output:**
```
Grade: B
```

## Function
函数
### **1. Basic Function Definition and Usage**
基本定义和用法: 使用 def 关键字定义，支持参数和返回值
A function in Python is defined using the `def` keyword, followed by the function name and a pair of parentheses `()`. You can optionally include parameters inside the parentheses. The function body is indented and can include any valid Python code.

#### Syntax:
```python
def function_name(parameters):
    # Function body
    # Code to be executed
    return value  # Optional
```

#### Example:
```python
def greet(name):
    """Print a greeting message."""
    print(f"Hello, {name}!")

# Calling the function
greet("Alice")
```

**Output:**
```
Hello, Alice!
```

---

### **2. Parameters and Arguments**
参数和参数: 支持位置参数、关键字参数、默认参数、可变参数
Functions can accept input values called **parameters**. When you call a function, you pass values to these parameters, which are then referred to as **arguments**.

#### **a. Positional Arguments**
These are the most common type of arguments. The order in which you pass them matters.

```python
def add(a, b):
    return a + b

result = add(3, 5)  # 3 and 5 are positional arguments
print(result)  # Output: 8
```

#### **b. Keyword Arguments**
You can also pass arguments by specifying the parameter names. This makes the code more readable and allows you to pass arguments in any order.

```python
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type} named {pet_name}.")

# Using keyword arguments
describe_pet(animal_type="hamster", pet_name="Harry")
describe_pet(pet_name="Harry", animal_type="hamster")
```

**Output:**
```
I have a hamster named Harry.
I have a hamster named Harry.
```

#### **c. Default Arguments**
You can provide default values for parameters. If an argument is not provided when calling the function, the default value is used.

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")  # Uses the default greeting
greet("Bob", greeting="Hi")
```

**Output:**
```
Hello, Alice!
Hi, Bob!
```

#### **d. Variable-Length Arguments (`*args` and `**kwargs`)**
Sometimes you might want a function to accept an arbitrary number of arguments.

- `*args` allows you to pass a variable number of positional arguments as a tuple.
- `**kwargs` allows you to pass a variable number of keyword arguments as a dictionary.

```python
def sum_numbers(*args):
    total = 0
    for num in args:
        total += num
    return total

def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Using *args
print(sum_numbers(1, 2, 3, 4))  # Output: 10

# Using **kwargs
print_info(name="Alice", age=25, city="New York")
```

**Output:**
```
10
name: Alice
age: 25
city: New York
```

---

### **3. Return Values**
返回值: 使用 return 语句返回值
Functions can return values using the `return` statement. If you don't explicitly return a value, the function returns `None` by default.

```python
def multiply(a, b):
    return a * b

result = multiply(4, 5)
print(result)  # Output: 20
```

---

### **4. Scope of Variables**
变量作用域: 变量有局部作用域和全局作用域
Variables defined inside a function are local to that function and cannot be accessed outside it. However, you can access global variables inside a function, but you need to use the `global` keyword if you want to modify them.

#### Example:
```python
x = 10  # Global variable

def my_function():
    global x
    x = 20  # Modifying the global variable
    y = 5   # Local variable

my_function()
print(x)  # Output: 20
# print(y)  # This would raise an error because y is local to my_function
```

---

### **5. Lambda Functions**
匿名函数: 使用 lambda 关键字定义匿名函数
Lambda functions are small anonymous functions defined with the `lambda` keyword. They are useful for simple operations and can be used in places where a function object is required.

```python
# Regular function
def square(x):
    return x * x

# Lambda function
square_lambda = lambda x: x * x

print(square(5))  # Output: 25
print(square_lambda(5))  # Output: 25
```

---

### **6. Function Annotations**
函数注解: 为函数参数和返回值添加类型提示和描述
Python allows you to add type hints and descriptions to function parameters and return values. These annotations do not enforce type checking but are useful for documentation and tools like type checkers.

```python
def add(a: int, b: int) -> int:
    """Return the sum of two integers."""
    return a + b

result = add(3, 4)
print(result)  # Output: 7
```

---

### **7. Recursive Functions**
递归函数: 函数调用自身，用于解决递归问题
A function can call itself. This is called recursion. Recursive functions are useful for solving problems that can be broken down into smaller, similar problems.

#### Example: Factorial
```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```

---

### **8. Higher-Order Functions**
高阶函数: 函数作为参数或返回值，例如 map、filter、reduce
Functions in Python are first-class objects, meaning they can be treated like any other object. You can pass functions as arguments to other functions, return functions from functions, or store functions in data structures.

#### Example: Function as an Argument
```python
def greet(name):
    return f"Hello, {name}!"

def farewell(name):
    return f"Goodbye, {name}!"

def process_message(func, name):
    return func(name)

print(process_message(greet, "Alice"))  # Output: Hello, Alice!
print(process_message(farewell, "Bob"))  # Output: Goodbye, Bob!
```

---

### **9. Closures**
闭包: 记住外部函数作用域中的变量
A closure is a function object that remembers values in its enclosing lexical scope even when the program flow is no longer in that scope.

#### Example:
```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(10)
print(closure(5))  # Output: 15
```

---

### **10. Docstrings**
文档字符串: 为函数添加文档说明
Docstrings are used to document functions. They are enclosed in triple quotes and should provide a brief description of what the function does, its parameters, and its return value.

```python
def add(a, b):
    """
    Return the sum of two numbers.

    Parameters:
    a (int): The first number.
    b (int): The second number.

    Returns:
    int: The sum of a and b.
    """
    return a + b

print(add.__doc__)
```

**Output:**
```
Return the sum of two numbers.

Parameters:
a (int): The first number.
b (int): The second number.

Returns:
int: The sum of a and b.
```

