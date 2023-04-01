[[file|Files]] are allocated in "blocks" on the disk. Each block is a collection of bytes (eg 1kb block size)

## Contiguous allocation
All files are allocated in a contiguous collection of blocks
- Just need to track the starting block and file size
- Very speedy for sequential reads and writes
- Need to know the max file size at the time of allocation
- As files are deleted, you get lots of [[fragmentation]]