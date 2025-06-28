# conTable of contents
- 如何上传本地文件到github
- 字符编码
- 数据类型

## **如何上传本地文件到github**

#### **打开git**

- **cd ~**:回到home目录
- **ll**：忘记了目标文件夹在哪儿(big_data)就用此指令 
![alt text](<S02find Documents.png>)
- **cd big_data/project**：此处是目标文件夹，为了复制到这同级文件夹下 用`.`

    **示例**：在此文件夹打开该文件夹 `cd ./`( / 可有可无)




- **cp -r ~/Desktop/bigdata_project/note .**  复制本地的文件夹到目标文件夹下:  

- **git status** : 随时查看状态
![alt text](<S02Uncommitted changes.png>)
红红的字显示未提交/为存储的修改

- **git add .** : 这个命令会将当前目录及其子目录中的所有更改的文件添加到暂存区。
【git add：将更改的文件添加到暂存区。】
【如果只想添加特定的文件，可以指定文件名：git add file1.txt file2.txt】

- **git status** : 随时查看状态(没图)

- **git commit** : 提交更改。【会进到编辑器，就添加内容，比如：add self-learning note】
![alt text](<S02git commit.png>)

- **git status** : 随时查看状态
![alt text](<S02git commit_status.png>)

- **git push** ：传到远程
![alt text](<S02git push.png>)



## **字符编码**
是将字符集中的字符映射为计算机可以存储和传输的二进制数据的过程。

`ASCII` : 简单但局限，仅适用于英文。

- 使用7位表示128个字符。
- 仅支持英语，无法处理多语言字符。

`utf-8` : 兼容性强、灵活高效，适合多语言环境。
- 兼容ASCII，使用1到4个字节表示字符。

`utf-16` : 对BMP（基本多语言平面）字符高效，但有字节序问题，适用于特定平台和系统。
- 主要使用2个字节，必要时使用4个字节表示字符。
- 不如UTF-8通用。

## **数据类型**
    可变数据类型 不能作为 全局变量 
### 基础数据类型（这些都是关键字）
`int`

`bool`

`float`（python无double）

### 复合数据类型-集合体
`str`[字符串]->不可修改

`set`[集合]->可修改 无序 不重复

`list`[列表]->可修改

`dict`[字典]->可修改

`tuple`[元组]->不可修改

### 补充
1. 我总是记混淆：

`tuple （ ）`

`set    { }`

`dict   { ：}`

2. set和dict的key一样->一定是不可变类型

3. list和tuple很像->区别是：前者可修改，后者不可修改

4. 因为string不可修改，所以需要赋值->b=a.replace(" "," ")【后者取代前者】
  
   因为list可修改，所以可以直接c.append（）【用于向列表末尾添加元素】