Various items are stored in memory

- Stack at top, grows down
- Heap has free space to grow up
- Text section (code) is read only
- Libraries (eg `libc`) can be shared between processes (see [[copy on write]])
- [[Kernel]] section is reserved, protected, and shared
- 0th [[page]] not used, because null pointers -- if someone dereferences null we want to crash immediately

## See also
[[R3000 address space layout]] for information on how this is implemented on the [[MIPS R3000]].
