A [[syscall]] to write the the [[file]] at the given [[file descriptor]].

```c
ssize_t write(int fd, void *buf, size_t buflen);
```

See [[accessing program memory]] for information on how buffers are handled by the kernel.
