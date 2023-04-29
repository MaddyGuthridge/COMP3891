A [[page table]] which uses a top-level page, which contains pointers to the second-level page tables. If a second-level page table doesn't exist, it isn't allocated.'

This works well for a 32-bit [[address space]], but isn't efficient enough for a 64-bit one. For that, use a [[three-level page table]]