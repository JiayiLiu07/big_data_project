### **题目1：字符串操作与列表推导式**
**任务：**编写一个函数`extract_vowels`，接收一个字符串列表作为输入，返回一个新的列表，包含每个字符串中所有元音字母（a, e, i, o, u）的集合。要求忽略大小写。

**示例：**
```python
print(extract_vowels(["Hello", "Python", "Programming"]))  
# 输出：[{'e', 'o'}, {'o'}, {'o', 'i', 'a'}]
```

**提示：**
- 使用字符串操作提取元音。
- 使用列表推导式和集合推导式完成任务。

**作答：**
```python
def extract_vowels(string_list):
    vowels = 'aAeEiIoOuU'
    result=[]
    
    for i in string_list:
        vowel_set = set()
        for char in string.lower():
             if char in vowels:
                vowel_set.add(char)
        result.append(vowel_set)
      
    return result

print(extract_vowels(["Hello", "Python", "Programming"]))
```



### **题目2：字典推导式与异常处理**
**任务：**编写一个函数`create_dict`，接收两个列表作为输入：`keys`和`values`。函数返回一个字典，其中`keys`作为键，`values`作为值。如果两个列表长度不一致，抛出`ValueError`异常。

**示例：**
```python
print(create_dict(["a", "b", "c"], [1, 2, 3]))  
# 输出：{'a': 1, 'b': 2, 'c': 3}

try:
    print(create_dict(["a", "b"], [1, 2, 3]))
except ValueError as e:
    print(e)  # 输出：Keys and values must have the same length.
```

**提示：** 
- 使用字典推导式创建字典。
- 使用异常处理确保两个列表长度一致。

**作答：**
```python
def create_dict(keys, values):
    if len(keys) != len(values):
        raise ValueError("Keys and values must have the same length.")
    return {k: v for k, v in zip(keys, values)}

try:
    print(create_dict(["a", "b"], [1, 2, 3]))   
except ValueError as e:
    print(e)



```
**笔记：**
- zip(keys, values) 生成一个迭代器，该迭代器产生元组，每个元组包含 keys 和 values 中对应位置的元素。
- 在字典推导式中，for k, v in zip(keys, values) 遍历这个迭代器，每次迭代都会得到一个元组 (k, v)。
- k 和 v 分别代表元组中的第一个元素（键）和第二个元素（值）。
- 字典推导式 {k: v ...} 使用这些键值对来构建一个新的字典。









### **题目3：控制流与字符串操作**
**任务：**编写一个函数`format_text`，接收一个字符串作为输入，返回一个格式化后的字符串。格式化规则如下：
1. 将字符串中的所有字母转换为小写。
2. 将字符串中的每个单词的首字母大写。
3. 如果字符串为空，返回`"Empty string"`。

**示例：**
```python
print(format_text("hello world"))  # 输出：Hello World
print(format_text(""))  # 输出：Empty string
```

**提示：**
- 使用字符串方法完成大小写转换和首字母大写。
- 使用控制流处理空字符串的情况。

**作答：**
```python

def format_text(strings):
    if text == "":
        return "Empty string"
    strings=strings.lower()

    word=strings.split()
    word_list=[]
    for i in word:
        word_list.append(i.capitalize())

    format_strings = ' '.join(word_list)
    
    return format_strings

print(format_text("hello world"))  # 输出：Hello World
print(format_text(""))  # 输出：Empty string
```

**笔记：**
**text.split()**：
这部分代码将原始文本 text 按空格分割成一个单词列表。例如，如果 text 是 "hello world"，那么 text.split() 将返回 ['hello', 'world']。
​**word.capitalize()**：
这是一个列表推导式，用于遍历分割后的单词列表，并对每个单词调用 capitalize() 方法。capitalize() 方法将单词的首字母转换为大写，其余字母转换为小写。例如，"hello".capitalize() 将返回 "Hello"。
​**' '.join(...)**：
这部分代码将经过处理的单词列表重新组合成一个字符串。' '.join() 方法使用指定的分隔符（这里是空格 ' '）将列表中的元素连接起来。例如，' '.join(['Hello', 'World']) 将返回 "Hello World"。


### **题目4：Lambda表达式与列表推导式**
**任务：**编写一个函数`apply_function`，接收一个数字列表和一个函数作为输入，返回一个新的列表，其中每个元素是原列表元素经过函数处理后的结果。要求使用lambda表达式和列表推导式。

**示例：**
```python
numbers = [1, 2, 3, 4, 5]
print(apply_function(numbers, lambda x: x ** 2))  # 输出：[1, 4, 9, 16, 25]
print(apply_function(numbers, lambda x: x + 10))  # 输出：[11, 12, 13, 14, 15]
```

**提示：**
- 使用lambda表达式定义简单的函数。
- 使用列表推导式对列表元素进行处理。

**作答：**
```python
def apply_function(numbers, func):
    return [func(x) for x in numbers]
    
print(apply_function(numbers, lambda x: x ** 2))
print(apply_function(numbers, lambda x: x + 10))



```

### **题目5：集合推导式与异常处理**
**任务：**编写一个函数`unique_values`，接收一个列表作为输入，返回一个集合，包含列表中所有唯一值的平方。如果输入列表包含非数字类型（如字符串或列表），抛出`TypeError`异常。

**示例：**
```python
print(unique_values([1, 2, 2, 3, 4]))  # 输出：{1, 4, 9, 16}
print(unique_values([1, -1, 2, -2]))  # 输出：{1, 4}

try:
    print(unique_values([1, "a", 3]))
except TypeError as e:
    print(e)  # 输出：All elements must be numbers.
```

**提示：**
- 使用集合推导式提取唯一值并计算平方。
- 使用异常处理确保输入列表只包含数字。

**作答：**
```python
def unique_values(lists):
    try:
        return {x**2 for x in lists}
    except TypeError:
        raise TypeError("All elements must be numbers.")



print(unique_values([1, 2, 2, 3, 4]))  # 输出：{1, 4, 9, 16}
print(unique_values([1, -1, 2, -2]))  # 输出：{1, 4}

try:
    print(unique_values([1, "a", 3]))
except TypeError as e:
    print(e)  # 输出：All elements must be numbers.


```


**笔记：**
**TypeError**
TypeError 是 Python 中的一种内置异常类型，它表示在执行操作时遇到了不适当的类型。当某个操作或函数的参数类型不正确时，Python 解释器会抛出 TypeError 异常。
- 只有数字才能进行数学运算,所以如果集合推导式在尝试对非数字元素进行平方操作时会引发 TypeError。