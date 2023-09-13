How it works on Linux, probably different for other systems.
- **FD table** - table of file descriptors per process
- **OF table** - table of open files, shared globally
- **VFS** - [[virtual file system]], bringing all the file systems together (eg mounting USB drives)
- **FS** - actual [[file system]], managing the file hierarchy of a particular device
- **Buffer cache** - a cache of the changes, see [[buffer cache]]
- **Disk scheduler**
- **Device driver**

## FD table
Apps are only given "[[file descriptor]]s", rather than actual file structures. That way, they can only modify the data using syscalls, which makes things more secure.

File descriptors are unique per-process, but are not equal between other processes.