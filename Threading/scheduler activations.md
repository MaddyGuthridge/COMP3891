## Topaz threads
Kernel-level threads
- Preemptive multi-threading -- the [[operating system|OS]] controls which threads run at what time

## Original FastThrds
User-level threads
- Cooperative multi-threading -- the program controls its own threads
- Means that syscalls are blocking (although perhaps [[upcalls]] can be used?)