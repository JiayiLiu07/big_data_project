# Table of contents
- How to upload local files to GitHub
- Character encoding
- Data type

## **How to upload local files to GitHub**

#### **Opening Git**

- **cd ~**: Return to the home directory
- **ll**: Use this command if you forgot where the target folder (big_data) is.

![alt text](<S02find Documents.png>)
- **cd big_data/project**: This is the target folder. To copy to the same folder, use `.`

**Example**: Open the folder in this folder using `cd ./` (the / is optional)

- **cp -r ~/Desktop/bigdata_project/note .**: Copy the local folder to the target folder:

- **git status**: Check the status at any time
![alt text](<S02Uncommitted changes.png>)
Red text indicates uncommitted/unstored changes

- **git add .**: This command adds all changed files in the current directory and its subdirectories to the staging area.
[git add: Adds changed files to the staging area.]
[To add only specific files, specify the filenames: git add file1.txt file2.txt]

- **git status**: Check the status at any time (not pictured)

- **git commit**: Commit changes. [This will bring you to the editor, where you can add content, such as: add self-learning note]
![alt text](<S02git commit.png>)

- **git status**: Check the status at any time
![alt text](<S02git commit_status.png>)

- **git push**: Push to the remote server
![alt text](<S02git push.png>)

## **Character encoding**
This is the process of mapping characters in a character set into binary data that computers can store and transmit.

`ASCII`: Simple but limited, only applicable to English.

- Uses 7 bits to represent 128 characters.
- Supports only English and cannot handle multilingual characters.

`utf-8`: Highly compatible, flexible, and efficient, suitable for multilingual environments.
- Compatible with ASCII, using 1 to 4 bytes to represent characters.

`utf-16`: Efficient for BMP (Basic Multilingual Plane) characters, but has byte order issues and is suitable for specific platforms and systems.
- Mainly uses 2 bytes, but may use 4 bytes when necessary to represent characters.
- Not as versatile as UTF-8.

## **Data Types**
Mutable data types cannot be used as global variables
### Basic Data Types (These are all keywords)
`int`

`bool`

`float` (Python does not have double)

### Composite Data Types - Collections
`str` [String] -> Immutable

`set` [Set] -> Modifiable, unordered, non-duplicate

`list` [List] -> Modifiable

`dict` [Dictionary] -> Modifiable

`tuple` [Tuple] -> Immutable

### Supplementary Notes
1. I always get confused:

`tuple()`

`set {}`

`dict{:}`

2. Set and dict keys are the same -> they must be immutable

3. List and tuple are very similar -> the difference is: the former is modifiable, the latter is not

4. Because strings are immutable, assignment is required -> b = a.replace(" "," ") [the latter replaces the former]

Because the list is modifiable, you can directly c.append() [used to add elements to the end of the list]