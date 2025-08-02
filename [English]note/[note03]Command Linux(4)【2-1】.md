## 1. File Modification Permissions
### 1. Modifying File/Directory Permissions

`chmod`: Change file or directory permissions

**Syntax**: chmod [permissions] filename

**Examples**:
(read, 4), write (write, 2), and execute (execute, 1)
- chmod 755 file.txt: Set file permissions to rwxr-xr-x
- chmod u+x script.sh: Add execute permission for the user
- chmod g-w data.txt: Remove write permission for the group
- chmod a+r *.txt: Add read permission for all users

`chown`: Change the owner of a file or directory

**Syntax**: chown [user][:group] filename

**Examples**:
- chown user1 file.txt: Change the file owner to user1
- chown user1:group1 file.txt: Changes both the owner and group of a file or directory

`chgrp`: Changes the group of a file or directory

Syntax: chgrp groupname filename

Example: chgrp developers file.txt

## 2. File Operations

### 1. Creation and Deletion

`touch`: Creates an empty file or updates the timestamp of a file

Syntax: touch filename

Example: touch newfile.txt

`mkdir`: Creates a directory

Syntax: mkdir [options] directoryname

Example:
- mkdir newdir: Creates a single directory
- mkdir -p parent/child: Recursively creates multiple directories

`rm`: Removes a file or directory

Syntax: rm [options] file/directory

Example:
- rm file.txt: Removes a file
- rm -r dir: Recursively removes a directory and its contents
- rm -f file.txt: Force deletion without prompting

### 2. Copying and Moving

`cp`: Copy a file or directory

**Syntax**: cp [options] source destination

**Example**:
- cp file.txt /path/to/destination/: Copy a file to the destination directory
- cp -r sourcedir/ targetdir/: Recursively copy a directory

`mv`: Move or rename a file/directory

**Example**:
- mv oldname.txt newname.txt: Rename a file
- mv file.txt /path/to/destination/: Move a file to the destination directory

### 3. Viewing and Editing

`cat`: View file contents

**Syntax**: cat filename

**Example**: cat file.txt

`more / less`: View file contents in pages

**Syntax**: more filename or less filename

**Example**: less largefile.txt

`head / tail`: View the beginning or end of a file

Syntax: head [options] filename or tail [options] filename

Example:
- head -n 10 file.txt: View the first 10 lines
- tail -f logfile.log: View new log file content in real time

`nano / vim / vi`: Text editor

Example:
- nano file.txt: Edit a file using Nano
- vim file.txt: Edit a file using Vim

## 3. Process Management
### 1. Viewing Processes

`ps`: Displays the current process status

Common Options:
- -e or -A: Displays all processes
- -f: Displays full format
- -u user: Displays processes for a specified user

Example: ps aux | grep process_name

`top / htop`: Monitors system processes in real time

- top: Dynamically displays process information
- htop: A more interactive and user-friendly process monitoring tool (requires installation)

### 2. Terminating a Process

`​kill`: Send a signal to terminate a process

**Syntax**: kill [signal] PID

**Common Signals**:

-9: Forced termination

-15: Default termination signal

**Example**: kill -9 1234

`​pkill`: Terminate a process by name

**Syntax**: pkill process name

**Example**: pkill firefox

### 3. Background and Foreground Management

`​&`: Run a command in the background

**Example**: ./script.sh &

`​jobs`: View background jobs

**Example**: jobs

`​fg`: Bring a background job to the foreground

**Syntax**: fg [job number]

**Example**: fg 1

`​bg`: Continue a suspended task in the background

**Syntax**: bg [job number]

**Example**: bg 1

## 4. Text Processing
### 1. Basic Text Filtering

`​grep`: Search for a pattern in text

**Syntax**: grep [options] pattern filename

**Common Options**:
- -i: Ignore case
- -v: Inverse match
- -r or -R: Recursively search directories
- -n: Display matching line numbers

**Example**:
- grep "error" logfile.txt
- grep -r "TODO" /project/

`​sed`: Stream editor for text replacement and processing

**Basic Syntax**: sed [options] 'command' filename

**Common Commands**:
- s/old/new/g: Replace
- d: Delete matching lines

**Example**:
sed 's/foo/bar/g' file.txt: Replace all occurrences of foo with bar
sed '/^#/d' config.txt: Delete all occurrences of # Lines starting with

`​awk`: A powerful text processing tool suitable for processing structured data

**Basic Syntax**: awk 'pattern {action}' filename

**Example**:
- awk '{print $1, $3}' data.csv: Prints the first and third columns of each line
- awk '/pattern/ {print $0}' file.txt: Prints lines matching the pattern

### 2. Sorting and Duplicate Removal

`​sort`: Sorts text

**Common Options**:
- -n: Sort by numeric value
- -r: Sort in reverse order
- -k: Sort by a specific field

**Example**:
- sort file.txt
- sort -k2,2n data.csv: Sort by the second column value

`​uniq`: Removes consecutive duplicate lines

**Common Options**:
- -c: Counts duplicates
- -d: Displays only duplicate lines

**Example**:
- uniq file.txt
- sort file.txt | uniq -c

### 3. Text Statistics

`wc`: Counts the number of lines, words, and characters in a file

**Common Options**:
- -l: Counts the number of lines
- -w: Counts the number of words
- -c: Counts the number of characters

**Example****:
- wc file.txt
- wc -l file.txt: Displays only the number of lines

### 4. Text Search and Replace (Advanced)

`find`: Finds files and directories

**Common Options**:
- -name: Searches by name
- -type: Searches by type (file f or directory d)
- -exec: Executes a command on the found files

**Example**:
- find /path -name "*.txt"
- find . -type f -size +1M

`diff`: Compares the differences between two files

**Syntax**: diff file1 file2

**Example**: diff file1.txt file2.txt

`patch`: Apply a patch file

**Syntax**: patch original file < patch file

## Additional Notes
### 1. Numerical Notation in Permission Management:

Permissions are divided into `read (r=4)`, `write (w=2)`, and `execute (x=1)`

**Example**: chmod 755 is equivalent to `rwxr-xr-x`.

### 2. Signals in Process Management:
Common signals include `TERM (terminate), `KILL (forced termination),` and `HUP (hang up).

### 3. Combining Text Processing Tools:

The `pipeline (|)` allows you to chain multiple commands together to achieve complex data processing.
**Example**: grep "error" logfile.txt | awk '{print $1}' | sort | uniq -c