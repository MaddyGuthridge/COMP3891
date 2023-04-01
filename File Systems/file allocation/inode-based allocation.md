Use a separate table ([[inode]]) for each file.

- Only keep the table for open files in memory
- Offers fast random access for files

Used by almost all modern file systems.

## Writing an inode
- Super block
- Group descriptors
- Data block bitmap
- Inode table
- Data blocks

## Consistency checking
- We need to make sure everything is ok if we unexpectedly lost power

## Free-space management
Difficult to keep track of free space
- Use a linked list of free blocks on the disk
- Keep a bitmap of free blocks and free inodes

## Implementing directories
- Directories stored like normal files
- The content of the file contains information about the children, including:
	- File name
	- Attributes
	- File inode number
Essentially a directory maps string names to inode numbers for all their child nodes.
