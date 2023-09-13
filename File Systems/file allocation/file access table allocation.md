- Keep a map of the entire [[file system]]
- Table entries contain the number of the next [[block]] of the [[file]] (still a linked list)
- Last block of a file, and empty blocks are marked with specific values
- Table is replicated in memory (makes linked list traversal much faster than [[linked list allocation]])

Used in old computers (eg FAT16, FAT32)

#### Pros and cons
- Table requires lots of memory allocation

### FAT file systems
- Keep two copies of the table for redundancy
