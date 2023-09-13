- Some [[syscall|syscalls]] give us a pointer
- We can't trust the software to give us valid data - what if they try to corrupt the [[kernel]] memory and get a privilege escalation or something

## Available helper functions

```c
/**
 * Safely copy memory at a pointer from user-space into kernel-space
 * 
 * Args:
 * - usersrc: pointer in user-space
 * - dest: pointer in kernel-space
 * - len: length of data to copy
 * 
 * Returns 0 on success
 */
int copyin(const userptr_t usersrc, void *dest, size_t len);

/**
 * Safely copy memory at a pointer from kernel-space out to user-space
 * 
 * Args:
 * - src: pointer in kernel-space
 * - userdest: pointer in user-space
 * - len: length of data to copy
 * 
 * Returns 0 on success
 */
int copyout(const void *src, userptr_t *userdest, size_t len);

/**
 * Safely copy a string from user-space into kernel-space until the null 
 * terminator, or until the end of the buffer is reached
 * 
 * Args:
 * - usersrc: pointer in user-space
 * - dest: pointer in kernel-space
 * - len: max length to copy
 * - got: pointer, changed to size of data that actually got read
 * 
 * Returns 0 on success
 */
int copyinstr(const userptr_t usersrc, void *dest, size_t len, size_t *got);

/**
 * Safely copy a string from kernel-space out to user-space until the null 
 * terminator, or until the end of the buffer is reached 
 * 
 * Args:
 * - src: pointer in kernel-space
 * - userdest: pointer in user-space
 * - len: max length to copy
 * - got: pointer, changed to size of data that actually got read
 * 
 * Returns 0 on success
 */
int copyoutstr(const void *src, userptr_t *userdest, size_t len, size_t *got);
```

These functions are standard in BSD kernels. Other kernels likely have similar functions.