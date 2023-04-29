Abbreviated as *TLB*.

Physical hardware on a CPU to accelerate page table lookups, acting as a cache. Aka *memory management unit*. It contains recently-used [[page table]] entries (usually 64-128 entries according to slides, but `cpuid` says my laptop has over 1500 L2 entries 🤔).

## How it works

1. Take [[virtual memory|virtual address]]
2. Get offset and [[page]] number
3. Look up page in TLB
4. If it is present, it is a *TLB hit*, and we can access that memory directly
5. If it isn't, it is a *TLB miss*, and we need to search the full page table, then perform a [[TLB refill]].

## Properties

- [[Page]] number
- [[Frame]] number
- Whether the translation is valid (as boolean)
- Whether the page is writable (as boolean)
- And other [[architecture]]-specific properties (see [[R3000 TLB]] for more info on the [[sys-161]] implementation).

## Hardware vs software TLBs
The system for handling TLB misses depends on on the CPU [[architecture]].

### x86 and ARM (hardware-loaded)
TLB misses perform a page table lookup in hardware, then reload the table.
- This means the process is ***🔥 BLAZINGLY FAST 🔥***
- But the [[kernel]] has very little control over it (you need to use the page table as designated by the CPU)

### [[MIPS]] and Itanium (software-loaded)
TLB misses generate a *TLB miss [[exception]]* which must be handled by the [[kernel]]. The kernel uses hardware instructions to load the new entries into the TLB.
- This means the [[kernel]] has much more control over how the [[page table]] is defined
- But it's probably slower than a hardware-accelerated lookup

## TLBs and context switching
In order to make lookups as efficient as possible for [[process|processes]], TLB entries must either be process specific, or be tagged with an [[address space]] ID. Otherwise processes would be able to access memory belonging to other processes.

### Process-specific TLB entries
When a [[context switch]] occurs, the entire TLB needs to be flushed and [[TLB refill|refilled]]. This produces a high overhead for context switches, and was used on x86 CPUs (apparently not in modern ones though?).

### Address space ID tagging
Each TLB entry is tagged with an [[address space ID]].

## Performance
- Without a TLB, the number of [[physical memory]] lookups for a [[virtual memory]] lookup is 2
- With a TLB, if there is a 99% hit rate, [[physical memory]] lookups are reduced significantly, since the TLB allows a lookup to be done in one operation. $0.99 \times 1 + 0.01 \times 2 = 1.01$.

## See also
[[R3000 TLB]]: information on how the [[MIPS R3000]] implements a TLB.