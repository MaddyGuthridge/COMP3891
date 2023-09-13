Virtual memory is the address space per-[[process]] -- each process is given it's own unique address space which is mapped to [[physical memory]], usually using a [[page table]].

Virtual memory addresses consist of a [[page]] number, and an offset. The page number is used to translate to a [[frame]] in physical memory, and the offset is maintained to find the location in that frame.