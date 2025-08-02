## 一、文件修改权限
### 1. 修改文件/目录权限

​`chmod`：更改文件或目录的权限

​**语法​**：chmod [权限] 文件名

​**示例​**：
（read，4）、写（write，2）和执行（execute，1）
- chmod 755 file.txt：设置文件权限为 rwxr-xr-x
- chmod u+x script.sh：为用户添加执行权限
- chmod g-w data.txt：移除组的写权限
- chmod a+r *.txt：为所有用户添加读权限

`chown`：更改文件或目录的所有者

​**语法​**：chown [用户][:组] 文件名

​**示例​**：
- chown user1 file.txt：将文件所有者改为 user1
- chown user1:group1 file.txt：同时更改所有者和组

`chgrp`：更改文件或目录的所属组

​**语法​**：chgrp 组名 文件名

​**示例​**：chgrp developers file.txt

## 二、文件操作

### ​1. 创建与删除

`touch`：创建空文件或更新文件时间戳

​**语法​**：touch 文件名

​**示例​**：touch newfile.txt

`mkdir`：创建目录

​**语法​**：mkdir [选项] 目录名

​**示例​**：
- mkdir newdir：创建单层目录
- mkdir -p parent/child：递归创建多级目录

`rm`：删除文件或目录

​**语法​**：rm [选项] 文件/目录

​**示例​**：
- rm file.txt：删除文件
- rm -r dir：递归删除目录及其内容
- rm -f file.txt：强制删除，不提示

### ​2. 复制与移动

​`cp`：复制文件或目录

​**语法​**：cp [选项] 源 目标

​**示例​**：
- cp file.txt /path/to/destination/：复制文件到目标目录
- cp -r sourcedir/ targetdir/：递归复制目录

​`mv`：移动或重命名文件/目录


​**示例​**：
- mv oldname.txt newname.txt：重命名文件
- mv file.txt /path/to/destination/：移动文件到目标目录

### ​3. 查看与编辑

`cat`：查看文件内容

​**语法​**：cat 文件名

​**示例​**：cat file.txt

`more / less`：分页查看文件内容

​**语法​**：more 文件名 或 less 文件名

​**示例​**：less largefile.txt

`head / tail`：查看文件开头或结尾部分

​**语法​**：head [选项] 文件名 或 tail [选项] 文件名

​**示例​**：
- head -n 10 file.txt：查看前10行
- tail -f logfile.log：实时查看日志文件新增内容

`nano / vim / vi`：文本编辑器

​**示例​**：
- nano file.txt：使用 Nano 编辑文件
- vim file.txt：使用 Vim 编辑文件

## 三、进程管理
### ​1. 查看进程

​`ps`：显示当前进程状态

**常用选项**：
- -e 或 -A：显示所有进程
- -f：显示完整格式
- -u 用户：显示指定用户的进程

**示例**：ps aux | grep process_name

`​top / htop`：实时监控系统进程

- top：动态显示进程信息
- htop：交互式更友好的进程查看工具（需安装）

### ​2. 终止进程

`​kill`：发送信号终止进程

**语法**：kill [信号] PID

**常用信号**：
- 9：强制终止
- 15：默认终止信号

**示例**：kill -9 1234

`​pkill`：根据名称终止进程

**语法**：pkill 进程名

**示例**：pkill firefox

### ​3. 后台与前台管理

​`&`：将命令放入后台运行

**示例**：./script.sh &

`​jobs`：查看后台任务

**示例**：jobs

`​fg`：将后台任务调至前台

**语法**：fg [作业号]

**示例**：fg 1

`​bg`：在后台继续运行暂停的任务

**语法**：bg [作业号]

**示例**：bg 1



## 四、文本处理
### ​1. 基本文本过滤

`​grep`：搜索文本中的模式

**语法**：grep [选项] 模式 文件名

**常用选项**：
- -i：忽略大小写
- -v：反向匹配
- -r 或 -R：递归搜索目录
- -n：显示匹配行号

**示例**：
- grep "error" logfile.txt
- grep -r "TODO" /project/

`​sed`：流编辑器，用于文本替换和处理

**基本语法**：sed [选项] '命令' 文件名

**常用命令**：
- s/旧/新/g：替换
- d：删除匹配行

**示例**：
sed 's/foo/bar/g' file.txt：将所有 foo 替换为 bar
sed '/^#/d' config.txt：删除以 # 开头的行

`​awk`：强大的文本处理工具，适合处理结构化数据

**基本语法**：awk '模式 {动作}' 文件名

**示例**：
- awk '{print $1, $3}' data.csv：打印每行的第1和第3列
- awk '/pattern/ {print $0}' file.txt：打印匹配模式的行

### ​2. 排序与去重

`​sort`：对文本进行排序

**常用选项**：
- -n：按数值排序
- -r：逆序
- -k：指定排序字段

**示例**：
- sort file.txt
- sort -k2,2n data.csv：按第二列数值排序

​`uniq`：去除连续重复行

**常用选项**：
- -c：计数重复次数
- -d：仅显示重复行

**示例**：
- uniq file.txt
- sort file.txt | uniq -c

### ​3. 文本统计

​`wc`：统计文件的行数、单词数和字符数

**常用选项**：
- -l：行数
- -w：单词数
- -c：字符数

**示例****：
- wc file.txt
- wc -l file.txt：仅显示行数

### ​4. 文本查找与替换（高级）​

​`find`：查找文件和目录

**常用选项**：
- -name：按名称查找
- -type：按类型查找（文件 f 或目录 d）
- -exec：对找到的文件执行命令

**示例**：
- find /path -name "*.txt"
- find . -type f -size +1M

​`diff`：比较两个文件的差异

**语法**：diff 文件1 文件2

**示例**：diff file1.txt file2.txt

`​patch`：应用补丁文件

**语法**：patch 原文件 < 补丁文件

## ​补充说明
### 1.​权限管理中的数字表示法：

权限分为`读（r=4）`、`写（w=2）`、`执行（x=1）`

**示例**：chmod 755 等同于 rwxr-xr-x。

### 2.​进程管理中的信号：
常用信号包括 `TERM（终止）`、`KILL（强制终止）`、`HUP（挂起）`等。

### 3.​文本处理工具的组合使用：

通过`管道（|）`可以将多个命令串联，实现复杂的数据处理。
**示例**：grep "error" logfile.txt | awk '{print $1}' | sort | uniq -c