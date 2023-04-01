[[file|Files]] are allocated in "[[block]]s" on the disk.

## Contiguous allocation
All files are allocated in a contiguous collection of blocks
- Just need to track the starting block and file size
- Very speedy for sequential reads and writes
- Need to know the max file size at the time of allocation
- As files are deleted, you get lots of [[fragmentation]]

## Dynamic allocation
- Disk space allocated in portions as needed
- Allocation occurs in fixed-size blocks

### Pros
- No external fragmentation
- Does not require pre-allocation of disk space
### Cons
- Blocks can be partially filled (internal fragmentation)
- File blocks are scattered across the disk
- Complex metadata management