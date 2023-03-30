## Motivation
- In the 90s it was becoming cheaper and cheaper to download lots of RAM
- As such, more and more caching used
- [[inode file system]]s not very optimised for lots of small files, since each file takes a ton of operations.

## Solution
Have a log-based file system, which sequentially writes all the changes to the disk in-order, making the updates sequential.

- Performing lots of small write operations is **🔥 BLAZINGLY FAST 🔥**

Hence we use a map of locations:
- Translate an [[inode]] number and translate it to the block number

To prevent data loss if we lose the map, we write the map to two places, so that there is always at least one version that is reliable.

## Issues
- Read operations are **❄️ FREEZINGLY SLOW ❄️**
- Need to reclaim space, which requires a cleaner
	- Use a "reach-ability" analysis to find deleted nodes
- You can then go and fill the data:
	- "Thread" the new data between the old data
		- Slow to write since we need to jump the write head
	- "Copy and compact" the new data backwards so that it can make more contiguous space
		- Slow to create since we need to rewrite so much data

## Data recovery
- Checkpoints are regularly created, with information about the table
- We can just read through the written data past the last checkpoint and apply the changes