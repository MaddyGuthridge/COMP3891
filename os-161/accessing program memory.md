- Some [[syscall|syscalls]] give us a pointer
- We can't trust the software to give us valid data - what if they try to corrupt the [[kernel]] memory and get a privilege escalation or something

## Available helper functions
```c
/**
 * Safely copy a pointer from user-space into kernel-space
 * 
 * 
 * /
int copyin(const userptr_t usersrc, void *dest, size_t len);

/**
 * Safely copy a pointer from kernel-space into user-space
 */
int copyout(const void *src, userptr_t *userdest, size_t len);

/**
 * Safely copy a string from user-space into kernel-space until the null 
 * terminator, or until the end of the buffer is reached
 */
int copyinstr(const userptr_t usersrc, void *dest, size_t len, size_t *got);

/**
 * Safely copy a string from kernel-space into user-space until the null 
 * terminator, or until the end of the buffer is reached 
 */
int copyoutstr(const void *src, userptr_t *userdest, size_t len, size_t *got);

```