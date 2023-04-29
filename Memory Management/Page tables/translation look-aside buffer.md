Abbreviated as *TLB*.

Physical hardware on a CPU to accelerate page table lookups, acting as a cache. Aka *memory management unit*. It contains recently-used [[page table]] entries.

## How it works

1. Take [[virtual memory|virtual address]]
2. Get offset and [[page]] number
3. Look up page in TLB
4. If it is present, it is a *TLB hit*, and we can access that memory directly
5. If it isn't, it is a *TLB miss*, and we need to search the full page table

Note that this lookup is often done by hardware - the only thing the [[kernel]] needs to handle is refreshing the contents.

## Properties

- [[Page]] number
- [[Frame]] number
- Whether the translation is valid (as boolean)
- Whether the page is writable (as boolean)

## Hardware vs software TLBs
