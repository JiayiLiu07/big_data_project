# Table of contents
- 1. Hard Links
- 2. Soft Links
- 3. Differences between Soft and Hard Links
## 1. Hard Links

ln data.txt data_hardlink # Create a Hard Link

- This can be considered a pointer to the file's inode. The system does not reassign an inode for it. Each time a hard link is added, the file's link count increases by one.
- There is no hierarchy between hard links. Deleting a hard link simply removes the associated information from the directory's data block and reduces the file's link count by one. The inode is not deleted from the inode table unless only one link remains.

![alt text](<02hard links.png>)

Note: The ls -il command displays both a file's inode number and detailed information.

## 2. Soft Links

ln -s data.txt data_symlink # Create a soft link

- This is equivalent to a shortcut in Windows. That is, if you create a soft link to a directory, it's simply a shortcut to the directory at a specific location. The operating system will directly find the file in the actual directory by searching for the shortcut.

![alt text](<02soft links.png>)

Conclusion: A soft link is not the same inode as the original file, the number of links does not increase, and even the size is different.

## 3. The Difference Between Soft and Hard Links

1. Essentiality:
- Hard links: The same inode, just with different names. - Soft links: They are different files with different inodes.

2. Cross-partition links

- Hard links cannot be created across partitions or devices, but soft links can.

3. Directories

- Hard links cannot create directory hard links, but soft links can.

4. Relationships

- Hard links are independent of each other, not primary or secondary.

- Soft links are dependent on the original file. If the original file is deleted, the soft link becomes unavailable.

5. Number of links

- Deleting or adding hard links will affect the number of links, but adding or removing hard links will not, as they have different inodes.

6. Relative paths

- When creating a hard link, the original file path is relative to the current path.

- When creating a soft link, the original file path is relative to the path of the soft link.

7. File type

- If the hard link type matches the original file type, a soft link will display as a symbolic link.

8. Creation method

- Creating a hard link: ln [original file] [hard link]
- Creating a soft link: ln -s [original file] [soft link]