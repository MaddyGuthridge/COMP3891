Opens a file, creating it if it doesn't exist.

Returns the 

## In user-land
```c
int open(const char *filename, int flags);
int open(const char *filename, int flags, mode_t mode);
```

## In kernel-land
```c
int sys_open(const char *filename, int flags);
int sys_open(const char *filename, int flags, mode_t mode);
```

# Flags

TODO