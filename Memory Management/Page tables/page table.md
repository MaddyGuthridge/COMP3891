A page table is a bunch of "pages" of memory, used to map between [[page|pages]] in [[virtual memory]] and [[frame|frames]] in [[physical memory]].

Since the translations are done on-the-fly, the physical memory used by a process doesn't need to be contiguous, even if the virtual memory is. The physical organisation of memory is abstracted away - userland programmers only need to deal with virtual addresses (I am jealous).

Paging offers no external fragmentation, and only small amounts of internal fragmentation (in last page)

An older system was "segmentation", but it isn't used much these days.

## Per-process or global?

The lectures say that a page table is per-process (meaning each process has its own independent page table). But the assignment required us to make a global page table which all processes share.
#### TODO: FIGURE OUT WHY

## Page table entry

Typically, a page table entry has a bunch of properties:

- **present/absent**: whether the page is in-use
- **protection**: whether the page is readable/writable/executable