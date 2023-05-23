A page table is a bunch of "pages" of memory, used to map between [[page|pages]] in [[virtual memory]] and [[frame|frames]] in [[physical memory]].

Since the translations are done on-the-fly, the physical memory used by a process doesn't need to be contiguous, even if the virtual memory is. The physical organisation of memory is abstracted away - user-land programmers only need to deal with virtual addresses (I am jealous).

Paging offers no external fragmentation, and only small amounts of internal fragmentation (in last page)

An older system was "segmentation", but it isn't used much these days.

## Per-process or global?

Standard page tables (such as a [[multi-level page table]]) are stored per-process, but [[inverted page table|inverted page tables]] and [[hashed page table|hashed page tables]] are stored globally, because they map [[frame|frames]] to [[page|pages]] (rather than pages to frames).

## Page table entry

Typically, a page table entry has a bunch of properties:

- **present/absent**: whether the page is in-use
- **protection**: whether the page is readable/writable/executable
- **modified**: whether the page has been changed from its initial state
- **caching disabled**: for some devices (eg a memory-mapped frame buffer) it is important to always update the actual buffer, and not just the cache.
- **referenced**
- **page frame number**: the [[frame]] that the page maps to

## How big does it need to be?

If we have
- `32`-bit virtual addresses
- `4` KB frame size
- number of pages: $n = \frac{2^{32}}{4096} = 1048576$ entries

This is wayyyyyyy too many entries, which is wasteful as for most programs will only use a fraction of that space. As such we need to choose a data structure that lets us ignore empty values, but can still look up frames efficiently.

## Page table data structures

### Data structures that adapt to sparsity
- [[two-level page table]]
- [[multi-level page table]]

### Data structures which only represent resident pages
- [[inverted page table]]
- [[hashed page table]]

### Using VM techniques for page tables
Causes chicken-egg problems if poorly designed. You need to be very careful to avoid infinite page faults.
- [[virtual linear page table]]
