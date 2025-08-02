# Python Lambda 表达式教程

## 一、什么是 Lambda 表达式

Lambda 表达式是一种简洁的匿名函数表示方式。它可以在一行代码内定义一个简单的函数，通常用于一些简单的操作，比如排序、过滤等场景。

### （一）Lambda 表达式的基本语法
Lambda 表达式的基本语法是：
```python
lambda 参数列表: 表达式
```
- **参数列表**：可以有多个参数，用逗号分隔。
- **表达式**：是一个简单的操作，表达式的结果就是这个 lambda 函数的返回值。

### （二）Lambda 表达式与普通函数的对比

#### 1. 普通函数的定义
普通函数使用`def`关键字定义，可以包含多条语句，执行复杂的逻辑。
```python
def add(x, y):
    return x + y

result = add(3, 4)
print(result)  # 输出：7
```

#### 2. Lambda 表达式的定义
Lambda 表达式是一种匿名函数，定义在一行内，通常用于简单的操作。
```python
add = lambda x, y: x + y
result = add(3, 4)
print(result)  # 输出：7
```

### （三）Lambda 表达式的特点
1. **简洁**：Lambda 表达式可以在一行内定义函数，代码更简洁。
2. **匿名**：Lambda 表达式没有函数名，是一种匿名函数。
3. **限制**：Lambda 表达式只能包含一个表达式，不能有多条语句，不能执行复杂的逻辑。

## 二、Lambda 表达式的使用场景

### （一）作为函数的参数
许多 Python 内置函数（如`map()`、`filter()`、`sorted()`等）可以接受一个函数作为参数，Lambda 表达式在这里非常方便。

#### 1. 使用`map()`函数
`map()`函数会对可迭代对象中的每个元素应用一个函数。使用 Lambda 表达式可以快速实现对元素的简单操作。

**样例代码**：
```python
numbers = [1, 2, 3, 4, 5]

# 使用普通函数
def square(x):
    return x ** 2

squared = list(map(square, numbers))
print(squared)  # 输出：[1, 4, 9, 16, 25]
```

**使用 Lambda 表达式**：
```python
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # 输出：[1, 4, 9, 16, 25]
```

**对比**：
- **普通函数**：需要定义一个单独的函数`square`。
- **Lambda 表达式**：直接在`map()`函数中定义一个简单的操作，代码更简洁。

#### 2. 使用`filter()`函数
`filter()`函数会根据一个函数来过滤可迭代对象中的元素，只有函数返回`True`的元素才会被保留下来。

**样例代码**：
```python
numbers = [1, 2, 3, 4, 5]

# 使用普通函数
def is_even(x):
    return x % 2 == 0

even_numbers = list(filter(is_even, numbers))
print(even_numbers)  # 输出：[2, 4]
```

**使用 Lambda 表达式**：
```python
numbers = [1, 2, 3, 4, 5]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # 输出：[2, 4]
```

**对比**：
- **普通函数**：需要定义一个单独的函数`is_even`。
- **Lambda 表达式**：直接在`filter()`函数中定义一个简单的条件，代码更简洁。

#### 3. 使用`sorted()`函数
`sorted()`函数可以对可迭代对象进行排序，通过`key`参数可以指定一个函数来决定排序的依据。

**样例代码**：
```python
people = [("Alice", 25), ("Bob", 20), ("Charlie", 30)]
# people 是一个包含多个元组的列表
# 使用普通函数
def get_age(person):
    return person[1]
# return person[1] 表示返回该元组的第二个元素，即年龄
sorted_people = sorted(people, key=get_age)
# key=get_age 指定了排序的依据是每个元素的年龄（即元组的第二个元素）
print(sorted_people)  # 输出：[('Bob', 20), ('Alice', 25), ('Charlie', 30)]
```

**使用 Lambda 表达式**：
```python
people = [("Alice", 25), ("Bob", 20), ("Charlie", 30)]
sorted_people = sorted(people, key=lambda x: x[1])
print(sorted_people)  # 输出：[('Bob', 20), ('Alice', 25), ('Charlie', 30)]
```

**对比**：
- **普通函数**：需要定义一个单独的函数`get_age`。
- **Lambda 表达式**：直接在`sorted()`函数中定义一个简单的操作，代码更简洁。

### （二）作为函数返回值
Lambda 表达式也可以作为函数的返回值，这样可以动态地生成函数。

**样例代码**：
```python
# 使用普通函数
def power(n):
    def inner(x):
        return x ** n
    return inner

square = power(2)
cube = power(3)
print(square(5))  # 输出：25
print(cube(5))    # 输出：125
```

**使用 Lambda 表达式**：
```python
def power(n):
    return lambda x: x ** n

square = power(2)
cube = power(3)
print(square(5))  # 输出：25
print(cube(5))    # 输出：125
```

**对比**：
- **普通函数**：需要定义一个内部函数`inner`。
- **Lambda 表达式**：直接返回一个 lambda 函数，代码更简洁。

## 三、Lambda 表达式的限制
虽然 Lambda 表达式很强大，但它也有一些限制：
1. **只能包含一个表达式**：Lambda 表达式不能包含复杂的逻辑，不能有多条语句。
2. **可读性问题**：对于复杂的逻辑，使用 Lambda 表达式可能会使代码难以理解。在这种情况下，使用普通函数可能更合适。

## 四、课后题目

### 题目 1
给定一个字符串列表`["apple", "banana", "cherry", "date"]`，使用 Lambda 表达式和`filter()`函数筛选出长度大于 5 的字符串。
- 答
```python
lst=["apple", "banana", "cherry", "date"]
str_number = list(filter(lambda x : len(x) >5 ,lst))
print(str_number)
```

### 题目 2
定义一个函数`create_multiplier`，它接受一个参数`n`，并返回一个 lambda 函数，这个 lambda 函数接受一个参数`x`并返回`x`乘以`n`的结果。测试这个函数，分别创建乘以 2 和乘以 3 的 lambda 函数，并用它们计算 10 的结果。
- 答
```python
def create_multiplier(n):
    return lambda x :x*n 
square = create_multiplier(2)
cube = create_multiplier(3)
print(square(10))
print(cube(10))
```

### 题目 3
给定一个包含学生信息的列表`[{"name": "Alice", "score": 85}, {"name": "Bob", "score": 90}, {"name": "Charlie", "score": 75}]`，使用 Lambda 表达式和`sorted()`函数按照分数从高到低对学生进行排序。
- 答
```python
student_info=[{"name": "Alice", "score": 85}, {"name": "Bob", "score": 90}, {"name": "Charlie", "score": 75}]
sorted_student= sorted(student_info , key = lambda x: x["score"])
print(sorted_student)
```

## 五、课后题目答案

### 题目 1 答案
```python
fruits = ["apple", "banana", "cherry", "date"]
long_fruits = list(filter(lambda x: len(x) > 5, fruits))
print(long_fruits)  # 输出：['banana', 'cherry']
```

### 题目 2 答案
```python
def create_multiplier(n):
    return lambda x: x * n

double = create_multiplier(2)
triple = create_multiplier(3)
print(double(10))  # 输出：20
print(triple(10))  # 输出：30
```

### 题目 3 答案
```python
students = [{"name": "Alice", "score": 85}, {"name": "Bob", "score": 90}, {"name": "Charlie", "score": 75}]
sorted_students = sorted(students, key=lambda x: x["score"], reverse=True)
print(sorted_students)  # 输出：[{'name': 'Bob', 'score': 90}, {'name': 'Alice', 'score': 85}, {'name': 'Charlie', 'score': 75}]
```

