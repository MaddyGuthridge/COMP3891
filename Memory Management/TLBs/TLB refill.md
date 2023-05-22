When a [[context switch]] occurs, or the [[translation look-aside buffer|TLB]] misses, a refill needs to be performed.

## Strategies for handling refills

The system for handling TLB misses depends on on the [[CPU]] [[architecture]].

### Hardware-loaded
TLB misses perform a [[page table]] lookup in hardware, then refill the table. This means the process is ***🔥 BLAZINGLY FAST 🔥***, but the [[kernel]] has very little control over it (you need to use the page table as designated by the [[CPU]]).

This technique is used by the x86 and ARM [[architecture|architectures]].

### Software-loaded
TLB misses generate a *TLB miss [[exception]]* which must be handled by the [[kernel]]. The kernel uses hardware instructions to load the new entries into the TLB. This means the kernel has much more control over how the page table is defined, but it's probably slower than a hardware-accelerated lookup.

This technique was used by the [[MIPS]] and Itanium architectures.
