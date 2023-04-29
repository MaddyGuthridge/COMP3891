A [[page table]] which uses a top-level page, which contains pointers to the second-level page tables. If a second-level page table doesn't exist, it isn't allocated.

This works well for a 32-bit [[address space]]. Only needs 1024 entries per allocated second-level page

| | | | |
| -------- | --------- | ------------ | ------ |
| **bits**     | 10        | 10           | 12     |
| **category** | top-level | second-level | offset |

However, it isn't efficient enough for a 64-bit address space.  It needs 67,108,864 entries per allocated second-level page
|          |           |              |        |
| -------- | --------- | ------------ | ------ |
| **bits**     | 26        | 26           | 12     |
| **category** | top-level | second-level | offset | 

For 64-bit address spaces, use a [[multi-level page table]] instead.