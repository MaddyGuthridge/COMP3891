Use a separate table for each file.

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