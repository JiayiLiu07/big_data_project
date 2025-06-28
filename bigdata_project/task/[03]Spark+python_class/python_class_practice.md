# Python 类练习题：学生管理系统

## 题目要求

### 1. 定义 `Student` 类

- **属性**：
  - `name`：学生的姓名（字符串类型）。
  - `age`：学生的年龄（整数类型）。
  - `grades`：学生的成绩列表（列表类型，存储整数）。

- **方法**：
  - `__init__`：初始化方法，接收 `name` 和 `age` 作为参数，并将 `grades` 初始化为空列表。
  - `add_grade`：添加成绩到 `grades` 列表中。
  - `average_grade`：计算并返回学生的平均成绩（如果成绩列表为空，返回 0）。
  - `__str__`：返回学生的信息，格式为 `"姓名: {name}, 年龄: {age}, 平均成绩: {average}"`。

### 2. 定义 `StudentManager` 类

- **属性**：
  - `students`：存储所有学生的列表。

- **方法**：
  - `__init__`：初始化方法，将 `students` 初始化为空列表。
  - `add_student`：添加一个 `Student` 对象到 `students` 列表中。
  - `remove_student`：根据学生姓名移除一个学生。
  - `find_student`：根据学生姓名查找并返回学生对象，如果找不到返回 `None`。
  - `average_grade_all`：计算所有学生的平均成绩（如果没有任何学生，返回 0）。
  - `__str__`：返回所有学生的信息，每个学生的信息占一行。

## TODO
```python
class Student:
    def __init__(self, name, age):
        # TODO: please complete this method 
        self.name=name
        self.age=age
        self.grades = []

    def add_grade(self, grade):
        # TODO: please complete this method 
        self.grades.append(grade)
    def get_grades(self):
        return self.grades
    def average_grade(self):
        # TODO: please complete this method 
        return sum(self.get_grades())/len(self.grades)

    def __str__(self):
        #返回学生的信息，格式为 `"姓名: {name}, 年龄: {age}, 平均成绩: {average}"`。
        # TODO: please complete this method 
        return f"姓名: {self.name}, 年龄: {self.age}, 平均成绩: {self.average_grade()}"
                                                            # 在里面（def）都要有self，在外面不用

class StudentManager:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def remove_student(self, name):
        #根据学生姓名移除一个学生。
        # TODO: please complete this method 
        for student in self.students:
            if student.name == name:
                self.students.remove(student)
                

    def find_student(self, name):
        # 根据学生姓名查找并返回学生对象，如果找不到返回 `None`。
        # TODO: please complete this method 
        students_list=[]
        for student in self.students:
            if student.name == name:
                students_list.append(student)
        if len(students_list)== 0: # 此if和for在同一列是因为，假设我们需要返回的是[3,3]。第一种[3,3,4,4]:按照第一个if是会得到我们要的结果；
            #第二种：[4,4,3,3]:按照第一个if，4！=3，他就不会把4放在列表，此时列表里就没东西，列表长度为0，返回的是None。
            #但是[4,4,3,3]里是包含[3,3]的。也就是：我们应该遍历完整个目标列表，再去students_list判断是否为0。
            return None
        return students_list # return 和for在同一列上，因为 是要把列表中的内容打印完 才返回这一个完整的列表
  
    def average_grade_all(self):
        # 计算所有学生的平均成绩（如果没有任何学生，返回 0）。
        # TODO: please complete this method 
        if len(self.students)==0:
            return 0
        total_average_grade=[]       
        for student in self.students: # 遍历每一个学生（拿出来） 把他们的平均成绩放到total_average_grade列表里
            total_average_grade.append(student.average_grade()) # 在里面（def内）调用属性和方法都是用. 方法一般在后面都加上括号（）
        return sum(total_average_grade)/len(total_average_grade)

    def __str__(self):
        # TODO: please complete this method print all students name
        return 

# 测试代码
if __name__ == "__main__":
    manager = StudentManager()
    student1 = Student("张三", 20)
    student1.add_grade(85)
    student1.add_grade(90)
    student2 = Student("李四", 22)
    student2.add_grade(78)
    student2.add_grade(88)

    manager.add_student(student1)
    manager.add_student(student2)

    print(manager)
    print("所有学生的平均成绩:", manager.average_grade_all())

    manager.remove_student("张三")
    print(manager)
```

