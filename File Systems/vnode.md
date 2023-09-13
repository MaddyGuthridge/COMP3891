Node on the [[virtual file system]]. A virtual representation of an [[inode]] on the disk.

## OS/161 implementation
```c
struct vnode {
	int vn_refcount; // Number of references to the vnode
	struct spinlock vn_countlock; // Lock to prevent data races
	struct fs *vn_fs; // Pointer to the file system of this file
	void *vn_data; // Pointer to the file data, only the file system knows what
	               // the data is specifically
	const struct vnode_ops *vn_ops; // Functions to operate on vnodes
}
```

## Vnode operations
Including, but not limited to
- `open`
- `close`
- `read`
- `write`
- `stat` - get attributes
- `seek`
- `create`
- `symlink`
- `mkdir`
- `remove`
- `rename`
