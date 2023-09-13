A [[syscall]] to read from a [[file]] with the given [[file descriptor]].

```c
ssize_t read(int fd, const void *buf, size_t nbytes);
```

See [[accessing program memory]] for information on how buffers are handled by the [[kernel]].

## Under the hood

Calls a `VOP_READ(vn, uio)` operation on the file system