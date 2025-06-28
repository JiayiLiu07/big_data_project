### **题目：日志文件分析与报告生成**
**任务：**编写一个程序，完成以下任务：
1. 从一个日志文件中读取内容，日志文件的每一行包含一个日志条目，格式如下：
   ```
   [时间戳] [日志级别] [消息内容]
   ```
   例如：
   ```
   [2025-03-15 10:00:00] [INFO] This is an info message.
   [2025-03-15 10:01:00] [ERROR] This is an error message.
   ```
2. 统计每种日志级别（如`INFO`、`ERROR`等）出现的次数。
3. 找出所有`ERROR`级别的日志条目，并将它们保存到一个新的文件中。
4. 生成一个报告文件，包含以下内容：
   - 每种日志级别出现的次数。
   - 所有`ERROR`级别的日志条目。
   - 每个`ERROR`条目的详细信息，包括时间戳、日志级别和消息内容。
5. 打印统计结果和`ERROR`日志条目的数量。
6. 解析日志消息中的特定模式（如错误代码），并统计这些模式的出现次数。例如，假设日志消息中包含错误代码`[ErrorCode: 123]`，统计每个错误代码的出现次数。

**示例：**
假设日志文件`log.txt`内容如下：
```
[2025-03-15 10:00:00] [INFO] This is an info message.
[2025-03-15 10:01:00] [ERROR] This is an error message. [ErrorCode: 404]
[2025-03-15 10:02:00] [INFO] Another info message.
[2025-03-15 10:03:00] [ERROR] Another error message. [ErrorCode: 500]
[2025-03-15 10:04:00] [ERROR] Yet another error message. [ErrorCode: 404]
```
程序执行后，输出：
```
INFO: 2
ERROR: 3
ERROR log entries saved to error_log.txt
Report saved to report.txt
```
并且生成两个文件：
- `error_log.txt`，内容为：
  ```
  [2025-03-15 10:01:00] [ERROR] This is an error message. [ErrorCode: 404]
  [2025-03-15 10:03:00] [ERROR] Another error message. [ErrorCode: 500]
  [2025-03-15 10:04:00] [ERROR] Yet another error message. [ErrorCode: 404]
  ```
- `report.txt`，内容为：
  ```
  Log Analysis Report

  Log Level Counts:
  INFO: 2
  ERROR: 3

  ERROR Log Entries:
  [2025-03-15 10:01:00] [ERROR] This is an error message. [ErrorCode: 404]
  [2025-03-15 10:03:00] [ERROR] Another error message. [ErrorCode: 500]
  [2025-03-15 10:04:00] [ERROR] Yet another error message. [ErrorCode: 404]

  Error Code Counts:
  404: 2
  500: 1
  ```

**提示：**
- 使用文件操作读取和写入文件。
- 使用字符串分割和切片提取日志级别和消息内容。
- 使用字典统计日志级别和错误代码出现的次数。
- 使用正则表达式解析日志消息中的特定模式（如错误代码）。
- 使用格式化字符串生成报告文件。

**第一次作答：**
```python
# TODO5: extarct functions main(), process_single_line, generate_error_file, generate_error_report
import re
from collections import defaultdict

# 定义文件路径
log_path = r"C:\Users\86137\Desktop\bigdata_project\02\log.log" 
error_log_path = r"C:\Users\86137\Desktop\bigdata_project\02\error_log.txt"
report_path = r"C:\Users\86137\Desktop\bigdata_project\02\report.txt"

# 初始化变量
log_levels_count = defaultdict(int)
error_logs = []
error_codes_count = defaultdict(int)

# TODO6: modify pattern to fix the exact log file which offered in the previous requirement
# 正则表达式匹配日志条目
log_pattern = re.compile(r"(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}), (\w+)\s+(\S.*)")

# 读取日志文件并解析内容
# TODO7: try except else finally 
# TODO8: if elif else 
try:
    # file = open(log_path, 'r', encoding='utf-8')
    # file.close
    with open(log_path, 'r', encoding='utf-8') as file:
        for line in file:
            match = log_pattern.match(line.strip())
            if match:
                timestamp, log_level, message = match.groups()

                # 统计日志级别出现次数
                log_levels_count[log_level] += 1

                # 如果是 ERROR 级别，保存到 error_logs 并解析错误代码
                if log_level == "Error":  
                    error_logs.append(line.strip())
                    # 查找错误代码 [ErrorCode: XXX]
                    # raw
                    error_code_match = re.search(r"$ErrorCode: (\d+)$", message)
                    if error_code_match:
                        error_code = error_code_match.group(1)
                        error_codes_count[error_code] += 1
except FileNotFoundError:
    print(f"Error: Log file not found at {log_path}")
    exit(1)

# TODO1: 将所有 ERROR 日志写入新文件
pass

# 生成报告文件
with open(report_path, 'w', encoding='utf-8') as report_file:
    report_file.write("Log Analysis Report\n\n")
    report_file.write("Log Level Counts:\n")
    for level, count in log_levels_count.items():
        # TODO2: write level count level: count eg. INFO: 2
        pass
    
    report_file.write("\nERROR Log Entries:\n")
    for error_log in error_logs:
        # TODO3: write error_log
        pass
    
    report_file.write("\nError Code Counts:\n")
    for code, count in error_codes_count.items():
        # TODO4: write code count 
        pass

# 打印统计结果和 ERROR 日志条目的数量
print("Info:", log_levels_count.get("Info", 0))  
print("Error:", log_levels_count.get("Error", 0))
print(f"ERROR log entries saved to {error_log_path}")
print(f"Report saved to {report_path}")
```


**第二次作答：无结构化**
```python
# TODO5: extarct functions main(), process_single_line, generate_error_file, generate_error_report
import re
from collections import defaultdict

# 定义文件路径
log_path = r"C:\Users\86137\Desktop\bigdata_project\02\log.txt" 
error_log_path = r"C:\Users\86137\Desktop\bigdata_project\02\error_log.txt"
report_path = r"C:\Users\86137\Desktop\bigdata_project\02\report.txt"

# 初始化变量
log_levels_count = defaultdict(int)
error_logs = []
error_codes_count = defaultdict(int)

# TODO6: modify pattern to fix the exact log file which offered in the previous requirement
# 正则表达式匹配日志条目
log_pattern = re.compile(r"\[(\d{4}-\d{2}-\d{2} \d{6})\] \[(\w+)\] (.*)")

# 读取日志文件并解析内容
# TODO7: try except else finally 
# TODO8: if elif else 
try:
    file = open(log_path, 'r', encoding='utf-8')
    for line in file:
        match = log_pattern.match(line.strip())
        if match:
            timestamp, log_level, message = match.groups()
            log_levels_count[log_level.upper()] += 1

            # 如果是 ERROR 级别，保存到 error_logs 并解析错误代码
            if log_level.upper() == "ERROR":
                error_logs.append(line.strip())
                error_code_match = re.search(r"\[ErrorCode (\d+)\]", message)
                if error_code_match:
                    error_code = error_code_match.group(1)
                    error_codes_count[error_code] += 1
    file.close()
except FileNotFoundError:
    print(f"Error: Log file not found at {log_path}")
    exit(1)

# TODO1: 将所有 ERROR 日志写入新文件
error_file = open(error_log_path, 'w', encoding='utf-8')
for error_log in error_logs:
    print(error_log, file=error_file)
error_file.close()


# 生成报告文件
report_file = open(report_path, 'w', encoding='utf-8')
print("Log Analysis Report\n\n", file=report_file)
print("Log Level Counts:\n", file=report_file)
for level, count in log_levels_count.items():
    # TODO2: write level count level: count eg. INFO: 2
    print(f"{level}: {count}", file=report_file)
        
print("\nERROR Log Entries:\n", file=report_file)
# TODO3: write error_log
for error_log in error_logs:
    print(f"{error_log}", file=report_file)

print("\nError Codes Count:\n", file=report_file)
for code, count in error_codes_count.items():
    # TODO4: write code count 
    print(f"{code}: {count}", file=report_file)
report_file.close()



# 打印统计结果和 ERROR 日志条目的数量
print("INFO:", log_levels_count.get("INFO", 0))  
print("ERROR:", log_levels_count.get("ERROR", 0))
print(f"ERROR log entries saved to {error_log_path}")
print(f"Report saved to {report_path}")
```
**第二次作答：结构化**
```python
import re
from collections import defaultdict

log_path = r"C:\Users\86137\Desktop\bigdata_project\02\log.txt"
error_log_path = r"C:\Users\86137\Desktop\bigdata_project\02\error_log.txt"
report_path = r"C:\Users\86137\Desktop\bigdata_project\02\report.txt"

log_levels_count = defaultdict(int)
error_logs = []
error_codes_count = defaultdict(int)

log_pattern = re.compile(r"\[(\d{4}-\d{2}-\d{2} \d{6})\] \[(\w+)\] (.*)")

def process_single_line(line):
    match = log_pattern.match(line.strip())
    if match:
        timestamp, log_level, message = match.groups()
        log_levels_count[log_level.upper()] += 1

    
        if log_level.upper() == "ERROR":
            error_logs.append(line.strip())
            error_code_match = re.search(r"\[ErrorCode (\d+)\]", message)
            if error_code_match:
                error_code = error_code_match.group(1)
                error_codes_count[error_code] += 1

def main():
    try:
        file = open(log_path, 'r', encoding='utf-8')
        for line in file:
            process_single_line(line)
        file.close()
    except FileNotFoundError:
        print(f"Error: Log file not found at {log_path}")
        exit(1)

    generate_error_file(error_log_path)
    generate_error_report(report_path)

    print("INFO:", log_levels_count.get("INFO", 0))
    print("ERROR:", log_levels_count.get("ERROR", 0))
    print(f"ERROR log entries saved to {error_log_path}")
    print(f"Report saved to {report_path}")


def generate_error_file(error_log_path):
    error_file = open(error_log_path, 'w', encoding='utf-8')
    for error_log in error_logs:
        error_file.write(error_log + "\n")
    error_file.close()


def generate_error_report(report_path):
    report_file = open(report_path, 'w', encoding='utf-8')
    report_file.write("Log Analysis Report\n\n")
    report_file.write("Log Level Counts:\n")
    for level, count in log_levels_count.items():
        report_file.write(f"{level}: {count}\n")

    report_file.write("\nERROR Log Entries:\n")
    for error_log in error_logs:
        report_file.write(f"{error_log}\n")

    report_file.write("\nError Codes Count:\n")
    for code, count in error_codes_count.items():
        report_file.write(f"{code}: {count}\n")
    report_file.close()


if __name__ == "__main__":
    main()
```





## **笔记2：**
### 一、以自己的方式理解正则表达式

**1. 理解为什么要用正则表达式：（3个作用）**
- 查找：查找文本中的特定信息
- 验证：验证输入的数据（邮箱、电话）是否符合想要的格式 
- 替换：批量替换文本中的某些模式。


**2. 在字符串前面加 r 表示屏蔽了它原本的、特别的作用（raw）**
        
 比如 r '\n' 会让它变成两个字符，'\n' 原本的作用是换行

**3. re 模块来处理正则表达式**

import re

**4. 编译正则表达式**

- ​**re.compile()​** ：将正则表达式编译成一个模式对象，方便重复使用。
    
      pattern = re.compile(r'abc')

**5. 常用的匹配方法**
- ​**match()**：从字符串的开头开始匹配。

- ​**search()**：扫描整个字符串，返回第一个匹配的位置。

- ​**findall()**：返回所有匹配的子串，以列表形式。

- ​**finditer()**：返回一个迭代器，包含所有匹配的对象。

- ​**sub()**：替换匹配的子串。

**6. 基本语法和元字符**
- `.` ：匹配除换行符外的任意单个字符。
            
      pattern = re.compile(r'a.c')  
      # 匹配 "abc", "aac", "adc" 等

- `^`：匹配字符串的开头。

      pattern = re.compile(r'^abc')  
      # 匹配以 "abc" 开头的字符串

- `$`：匹配字符串的结尾。

      pattern = re.compile(r'abc$')  
      # 匹配以 "abc" 结尾的字符串

- `*` ：匹配前面的子表达式零次或多次。

      pattern = re.compile(r'ab*c')  
      # 匹配 "ac", "abc", "abbc", "abbbc" 等

- `+`：匹配前面的子表达式一次或多次。

      pattern = re.compile(r'ab+c')  
      # 匹配 "abc", "abbc", "abbbc" 等，但不匹配 "ac"

- `?`：匹配前面的子表达式零次或一次。

      pattern = re.compile(r'colou?r')  
      # 匹配 "color" 或 "colour"

- `{n}`：匹配前面的子表达式恰好 n 次。

      pattern = re.compile(r'a{3}')  
      # 只匹配 "aaa"

- `{n,}`：匹配前面的子表达式至少 n 次。

      pattern = re.compile(r'a{2,}')  
      # 匹配 "aa", "aaa", "aaaa", ...

- `{n,m}`：匹配前面的子表达式至少 n 次，至多 m 次。

      pattern = re.compile(r'a{2,4}')  
      # 匹配 "aa", "aaa", "aaaa"

- `[]`：定义一个字符集，匹配其中的任意一个字符。

      pattern = re.compile(r'[aeiou]')  
      # 匹配任意一个元音字母

- `|`：逻辑“或”，匹配左边或右边的表达式。

      pattern = re.compile(r'cat|dog')  
      # 匹配 "cat" 或 "dog"

- `\d`：匹配任意数字，等价于 [0-9]。

      pattern = re.compile(r'\d')  
      # 匹配任意一个数字

- `\w`：匹配任意字母、数字或下划线，等价于 [A-Za-z0-9_]。

      pattern = re.compile(r'\w')  
      # 匹配字母、数字或下划线

- `\s`：匹配任意空白字符，包括空格、制表符、换行符等。

      pattern = re.compile(r'\s')  
      # 匹配任意空白字符

**7. 举例**
- 示例 1：查找所有数字
```python
import re

text = "我的电话号码是123-456-7890。"
pattern = re.compile(r'\d+')  # 匹配一个或多个数字

matches = pattern.findall(text)
print(matches)  # 输出: ['123', '456', '7890']
```
- 示例 2：验证邮箱地址
```python
import re

email = "example.user@example.com"
pattern = re.compile(r'^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$')

if pattern.match(email):
    print("有效的邮箱地址")
else:
    print("无效的邮箱地址")
```
- 示例 3：替换文本中的特定模式
```python
import re

text = "苹果的价格是$5.99，香蕉的价格是$3.49。"
pattern = re.compile(r'\$\d+\.\d{2}')  # 匹配如 $5.99 的价格

# 将价格替换为 [价格]
new_text = pattern.sub('[价格]', text)
print(new_text)  # 输出: 苹果的价格是[价格]，香蕉的价格是[价格]。
```
- 示例 4：提取邮箱中的用户名和域名
```python
import re

email = "user.name@example.co.uk"
pattern = re.compile(r'([a-zA-Z0-9_.+-]+)@([a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+)')

match = pattern.match(email)
if match:
    username, domain = match.groups()
    print(f"用户名: {username}")  # 输出: 用户名: user.name
    print(f"域名: {domain}")      # 输出: 域名: example.co.uk
```


### 二: extarct functions main(), process_single_line, generate_error_file, generate_error_report(函数)
- `main()函数` ：指挥官。在这里调用其他函数来完成任务。函数调用时，需要传递必要的参数（例如文件名、错误列表等）。
- if __name__ == "__main__" : 表示当脚本直接运行时，才会执行main()函数。
- 每个函数只做一件事

### 三: try except else finally (异常处理的结构)
- `try` 块：可能会引发异常的代码
- `except` 块：try 块中的代码引发了异常，程序会跳转到 except 块来处理异常

      except 异常类型 as 异常变量:
      # 处理异常的代码
- `else` 块（可选）：try 块中的代码没有引发异常，程序会执行 else 块中的代码（else 块通常用于执行一些只有在没有异常发生时才需要执行的逻辑。）  
- `finally` 块（可选）:无论是否发生异常，finally 块中的代码都会被执行。(关闭文件、释放资源等)

### 四: if elif else (条件判断的语句结构)
- `if` 块:条件表达式的结果为 True，则执行 if 块中的代码。
- `elif` 块（可选，可以有多个）:前面的 if 或 elif 条件不满足，程序会继续检查下一个 elif 条件。如果某个 elif 条件为 True，则执行对应的代码块。
- `else` 块（可选，只能有一个）:如果前面的所有 if 和 elif 条件都不满足，则执行 else 块中的代码。

## **笔记1：**
### 1. 使用文件操作读取和写入文件
![alt text](image.png)



### 2. 使用字符串分割和切片提取日志级别和消息内容


```python
log_entry = "ERROR [500] Internal Server Error occurred"

# 按空格分割两次
parts = log_entry.split(' ', 2)  
# ['ERROR', '[500]', 'Internal Server Error occurred']

level = parts[0]  # 日志级别
details = ' '.join(parts[1:])  # 合并剩余部分

print(f"日志级别: {level}")      
# 输出: ERROR
print(f"详细信息: {details}")   
 # 输出: [500] Internal Server Error occurred
```

### 3. 使用字典统计日志级别和错误代码出现的次数
![alt text](image-1.png)
**补充**：
```python
error_codes[error_code] = error_codes.get(error_code, 0) + 1
```
1. 这段代码是Python语言中的字典操作:统计错误代码error_code出现的次数。[这是一个常见的统计方法，用于记录和更新不同错误代码的出现次数。]
2. 下面是对这段代码的详细解析：
- error_codes 是一个字典，它的键是error_code，值是error_code出现的次数。
- error_code 是一个变量，代表一个错误代码的值。
- error_codes.get(error_code, 0) 是字典的get方法，它的作用是：

如果error_code这个键存在于字典error_codes中，则返回对应的值;

如果error_code这个键不存在于字典error_codes中，则返回默认值0。
- 1 表示每次遇到这个error_code时，其计数增加1。
- error_codes[error_code] = ... 是将计算后的新值赋给字典error_codes中对应的键error_code。

3. 这段代码的含义是：

查看`字典error_codes`中是否已经有`error_code这个键`的记录，如果有，则取出其值，并在原有基础上加1；如果没有，则从0开始计数，并加1。
最后将新的计数结果更新到`字典error_codes`中。


### 4. 使用格式化字符串生成报告文件
![alt text](image-2.png)
![alt text](image-3.png)
- **f** 在字符串前缀表示这是一个格式化字符串。
- **"Log Level Counts:\n"** 是字符串的一部分，它将直接被包含在最终的字符串中。**\n** 是一个换行符，表示在输出时这里将开始新的一行。
- **{log_counts}** 是一个占位符，它将被**变量 log_counts** 的值替换。**log_counts 是一个字典**，所以当它被替换时，它将被转换为一个字符串，显示字典的键值对。
- **"\n\n"** 是两个连续的换行符，用于在报告的不同部分之间添加空行，以便于阅读。
- **"Error Codes:\n"** 同样是字符串的一部分，后面跟着一个换行符。
- **{error_codes}** 是另一个占位符，将被**变量 error_codes** 的值替换。同样，**error_codes 是一个字典**，其内容将被转换为字符串并插入到报告中。