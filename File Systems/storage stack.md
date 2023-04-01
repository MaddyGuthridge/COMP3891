- **FD table** - table of file descriptors per process
- **OF table** - table of open files
- **VFS** - [[virtual file system]], bringing all the file systems together (eg mounting USB drives)
- **FS** - actual [[file system]], managing the file hierarchy of a particular device
- **Buffer cache**
- **Disk scheduler**
- **Device driver**


## FD table
Apps are only given "file descriptors", rather than actual file structures. That way, they can only modify the data using syscalls, which makes things more secure.
