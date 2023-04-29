An inverted [[page table]] (IPT) has an entry for every [[frame]], rather than an entry for every [[page]]. This means that it can be stored globally, rather than having a different instance for each virtual [[address space]].

This means the memory overhead is fixed, since it is determined by the amount of memory in the system. Additionally, vast amounts of memory are saved since there is no need to allocate table rows that could never be filled due to [[physical memory]] limitations (running out of RAM).

Since an IPT maps frames and not pages, a separate data structure is needed to keep track of non-resident pages.

Note that this also makes [[memory sharing]] nearly impossible. As such, an improvement on the IPT is a [[hashed page table]].

## IPT structure

A frame table is used to store which frames belong with which pages. This is also used for [[page replacement]].
| frame index | PID | virtual page number | ctrl | next | comment                                                                                  |
| -----------:| ---:| -------------------:| ---- | ---- | ---------------------------------------------------------------------------------------- |
|           0 |     |                     |      |      | empty frames                                                                             |
|           1 |     |                     |      |      |                                                                                          |
|           2 |   1 |                0x1A |      |      | this frame has an entry                                                                  |
|           3 |   2 |                0x3C |      | 5    | another entry collided with this entry, so the next property is set                      |
|           4 |     |                     |      |      |                                                                                          |
|           5 |   4 |                0x3C |      |      | Even though the hash would have put it at index 3, it went here because of the collision |

Note that the `frame index` is not actually a property for the entry structure -- it is a property of the array of entries.

Because multiple processes might have addresses with the same page (or different addresses with the same hash), there is a risk of collisions. As such we also need to store what process owns each frame.

## Hash Anchor Table

Inverted page tables use an additional hash anchor table to calculate mappings from [[virtual memory]] to [[physical memory]], since otherwise look-ups would only be possible from frames to pages.
| hash | page table index | comments                                                                                                                             |     |
| ----:| ----------------:| ------------------------------------------------------------------------------------------------------------------------------------ | --- |
|    0 |                - | not assigned                                                                                                                         |     |
|    1 |                3 | look up index 3 in the table                                                                                                         |     |
|    2 |                - |                                                                                                                                      |     |
|    3 |                3 | maps to same page table index - a collision! Thankfully our page table can also track the PIDs that own each frame, so this is fine. |     |
|    4 |                2 |                                                                                                                                      |     |
