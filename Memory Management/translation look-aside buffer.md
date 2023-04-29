Aka "memory management unit". Abbreviated to TLB.

Physical hardware used to translate [[virtual memory|virtual addresses]] to [[physical memory|physical addresses]], (or to locations on disk according to slides??).

## How it works

- Take virtual address
- Get offset and page number
- Look up page number in page table, and get frame number
- Frame number and offset are combined to get physical address
- If page number is absent, need to bring in page from disk (if it is in a [[page file]]), otherwise it's a segfault. This is known as a [[page fault]].