An operating system needs to manage memory

- Allocate [[memory resources|resources]] for [[process]]es as required
- Deallocate resources when they are no-longer needed
- Manages the transfer of memory content between RAM and disk (eg a [[page file]])


## Forms of memory

1. Registers: they speedy, but not many of them
2. Cache: not as speedy but still much fast
3. Main memory: RAM, it's fast, at least compared to the rest
4. SSDs/HDDs: can't be operated on directly using the processor - OS needs to manipulate the data using a [[file system]]
5. Optical disk: like CDs and stuff, they slow and expensive
6. Magnetic tape: really slow, but damn there's a lot of it


## Kinds of memory management

Most modern operating systems implement a [[page table]] and/or a [[swap]] space. 

Some low-level or ancient one's don't (eg embedded devices). They might keep the OS in ROM.
