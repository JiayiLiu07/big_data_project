# **python class and object**

### 1. 类（Class）
类 是一个代码模板，用来定义一组具有相同属性（变量）和方法（函数）的对象。

定义类的语法:
```python
class 类名:
    def __init__(self, 参数1, 参数2, ...): # 构造器
        # 初始化属性
        self.属性1 = 参数1
        self.属性2 = 参数2
        ...
    
    def 方法名(self, 参数1, 参数2, ...):
        # 方法的实现
        ...
```
- `class` 是定义类的关键字。
- 类名 是给类起的名字，通常以**大写字母开头**。
-  `__init__ `是一个特殊方法，称为构造方法，用于初始化类的属性。
- `self` 是一个指向当前对象的引用，用于访问类的属性和方法。

示例：定义一个Student类
```python
class Student:
    def __init__(self,id,name,mark):
        self.id=id     # 定义一个属性 id
        self.name=name # 定义一个属性 name
        self.mark=mark # 定义一个属性 mark

    def show_info(self,id,name,mark): # 定义一个方法 show_info
        print(f"id:{self.id}")
        print(f"name:{self.name}")
        print(f"mark:{self.mark}")

    def update_mark(self,new_mark): # 定义一个方法 update_mark
        self.mark=new_mark
```
示例：定义一个Person类
```python
class Person:
    def __init__(self, name, age):
        self.name = name  # 定义一个属性 name
        self.age = age    # 定义一个属性 age

    def greet(self):  # 定义一个方法 greet
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")
```




### 2. 对象（Object）
对象 是根据类创建的具体实例。类是“蓝图”，对象是根据这个蓝图建造的“房子”。每个对象都有自己的属性值，但共享类的方法。

创建对象的语法：
```python
对象名 = 类名(参数1, 参数2, ...)
```

示例：创建Person类的对象
```python
# 创建一个 Person 对象
person1 = Person("Alice", 30)

# 访问对象的属性
print(person1.name)  # 输出: Alice
print(person1.age)   # 输出: 30

# 调用对象的方法
person1.greet()  # 输出: Hello, my name is Alice and I am 30 years old.
```

### 3. 方法（Method）
方法（Method） 是定义在类中的函数。它与普通的函数类似，但有一个特殊之处：方法的第一个参数通常是 self，它代表类的实例（对象）。通过 self，方法可以访问类的属性和其他方法。

**(1) 方法的类型**

在 Python 中，方法主要有以下几种类型：
- 实例方法（Instance Method）
- 类方法（Class Method）
- 静态方法（Static Method）
![alt text](06method.png)

**(2) 实例方法（Instance Method）**
![alt text](<06instance method.png>)

**(3) 类方法（Class Method）**
![alt text](<06class method.png>)

**(4) 静态方法（Static Method）**
![alt text](<06static method.png>)