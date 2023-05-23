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
- Use a linked list of free blocks on the disk (leads to randomness eventually causing block scattering)
- Keep a bitmap of free blocks and free inodes

## Implementing directories
- Directories stored like normal files
- The content of the file contains information about the children, including:
	- File name
	- Attributes
	- File inode number
Essentially a directory maps string names to inode numbers for all their child nodes.

## How inodes are stored

### System V file system
| Section     | Purpose                                                                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Boot block  | Code to bootstrap the [[operating system|OS]]                                                                                                                         |
| Super block | Attributes of the file system itself (number of inodes, start block of inode array, start of data blocks, free inode list, free data block list) |
| Inode array | Contains all the inodes - we can look up an inode using the start offset and the inode number                                                    |
| Data        | Data blocks                                                                                                                                      |

#### Problems
- Since inodes are at start and data is at end, there are long seek times for mechanical hard drives
- Only one super block - if it is corrupted, your entire file system is lost
- Using a linked list of free blocks, causing scattered nodes
- Same thing for directory inode listing - scattered nodes cause slowness
