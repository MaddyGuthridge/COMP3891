Abbreviated as *TLB*.

Physical hardware on a CPU to accelerate page table lookups, acting as a cache. Aka *memory management unit*. It contains recently-used [[page table]] entries (usually 64-128 entries according to slides, but `cpuid` says my laptop has over 1500 L2 entries 🤔).

## How it works

1. Take [[virtual memory|virtual address]]
2. Get offset and [[page]] number
3. Look up page in TLB
4. If it is present, it is a *TLB hit*, and we can access that memory directly
5. If it isn't, it is a *TLB miss*, and we need to search the full page table

## Properties

- [[Page]] number
- [[Frame]] number
- Whether the translation is valid (as boolean)
- Whether the page is writable (as boolean)

## Hardware vs software TLBs
The system for handling TLB misses depends on on the CPU [[architecture]].

- On x86 and ARM architectures, TLB misses perform a page table lookup, then reload the table
- On [[MIPS]] and Itanium architectures, TLB misses generate a TLB miss [[exception]] which must be handled by the [[kernel]]. The kernel uses hardware instructions to load the TLB.