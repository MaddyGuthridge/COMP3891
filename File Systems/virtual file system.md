A virtual file system (VFS) is an interface for combining multiple [[file system]]s together, allowing for all the file systems on the computer to be contained within a single tree. Each file is given a [[vnode]], which is used to represent that file in the overall system.

## Mounting
File systems get mounted onto the virtual file system, and the OS handles integrating them together, so that apps in user-land don't need to worry about the differences.

## File system representation
```c
// In OS/161
struct fs {
    int (*fs_sync, struct fs *); // Sync all content to the disk
    const char *(*fs_getvolname)(struct fs *); // Get the name of the volume
    struct vnode *(*fs_getroot)(struct fs *); // Return the root vnode of the fs
    int (*fs_unmount)(struct fs *); // Unmount the file system
	void *fs_data; // Any other data used by this specific file system type
}
```