A virtual file system (VFS) is an interface for combining multiple [[file system]]s together, allowing for all the file systems on the computer to be contained within a single tree.

## Mounting
File systems get mounted onto the virtual file system, and the OS handles integrating them together, so that apps in user-land don't need to worry about the differences.
