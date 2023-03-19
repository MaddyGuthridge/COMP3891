Fork a [[process]], splitting it in two, where both continue from where they left off.

This means we need to be smart with concurrency, yikes.

```c
pid_t fork(void);
```

The [[file descriptor|file descriptors]] in the parent will be the same as in the child, and the underlying file pointers will be shared.
