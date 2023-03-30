Stands for index node. Each inode has information about the given file, and its children (if it is a directory). 

Writing an inode:
- Super block
- Group descriptors
- Data block bitmap
- Inode table
- Data blocks

## Consistency checking
- We need to make sure everything is ok if we unexpectedly lost power
