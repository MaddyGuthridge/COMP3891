Opens a [[file]], creating it if it doesn't exist.

Returns a [[file descriptor]]. The OS must map between a [[process]]'s file descriptors and the corresponding [[vnode|vnodes]].

```c
int open(const char *filename, int flags);
int open(const char *filename, int flags, mode_t mode);
```

## Flags

TODO