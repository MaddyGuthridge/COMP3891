A file system is an abstraction used to represent data on a storage medium (eg a hard drive or a solid-state drive).

This abstraction provides

| In user-land                          | Under the hood                                                                              |
| ------------------------------------- | ------------------------------------------------------------------------------------------- |
| Uniform namespace                     | Assortment of drives, files, devices, and other things (or everything on UNIX-like systems) |
| Hierarchy                             | A flat address space (array of blocks)                                                      |
| Arbitrarily-sized files               | Fixed-size blocks                                                                           |
| Symbolic file names                   | Numeric block addresses                                                                     |
| Contiguous address space inside files | Files framented all over the disk                                                           |
| Access control                        | No access control                                                                           |

A file system can also provide tools for formatting, defragmentation, backup, consistency checking, and error correction.
