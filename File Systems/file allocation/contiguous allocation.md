All files are allocated in a contiguous collection of [[block|blocks]]
- Just need to track the starting block and file size
- Very speedy for sequential reads and writes
- Need to know the max file size at the time of allocation
- As files are deleted, you get lots of [[fragmentation]]

Used by CD-ROM file systems.