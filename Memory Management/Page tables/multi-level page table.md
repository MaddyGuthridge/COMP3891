A multi-level [[page table]] is like a [[two-level page table]], but with multiple levels of nodes, rather than just 2.

These additional levels mean that the table can support 64-bit [[address space|address spaces]] more efficiently.

A multi-level page table is use on x86 and ARM [[architecture]] systems.

## Issues
Can require multiple jumps through memory due to the tree-like data structure. Hence use a [[translation look-aside buffer|TLB]] to accelerate it.
