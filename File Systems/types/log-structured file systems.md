## Motivation
- Cheaper and cheaper to download lots of RAM
- As such, more and more caching used
- [[inode file system]]s not very optimised for lots of small files, since each file takes a ton of operations

## Solution
Have a log-based file system, which sequentially writes all the changes to the disk in-order, making the updates sequential.

- Performing lots of small write operations is **🔥 BLAZINGLY FAST 🔥**
- Read operations are **❄️ FREEZINGLY SLOW ❄️**

Hence we use a map of locations:
- Translate an inode number and translate it to 