An inverted [[page table]] (IPT) has an entry for every [[frame]], rather than an entry for every [[page]]. This means that it can be stored globally, rather than having a different instance for each virtual [[address space]].

This means the overhead is fixed, since it is determined b

## IPT structure

| frame index | PID | virtual page number | ctrl | next | comment                 |
| -----------:| ---:| -------------------:| ---- | ---- | ----------------------- |
|           0 |     |                     |      |      | empty frames            |
|           1 |     |                     |      |      |                         |
|           2 |   1 |                0x1A |      |      | this frame has an entry |
|           3 |   2 |                0x3C |      | 5    | another entry collided with this entry                        |

Because multiple processes might have addresses with the same page (or different addresses with the same hash), there is a risk of collisions - as such we also need to store what process owns each frame.

## Hash Anchor Table

Inverted page tables use an additional hash anchor table to calculate mappings from [[virtual memory]] to [[physical memory]], since otherwise look-ups would only be possible from frames to pages.
| hash | page table index | comments                                                                                                                             |     |
| ----:| ----------------:| ------------------------------------------------------------------------------------------------------------------------------------ | --- |
|    0 |                - | not assigned                                                                                                                         |     |
|    1 |                3 | look up index 3 in the table                                                                                                         |     |
|    2 |                - |                                                                                                                                      |     |
|    3 |                3 | maps to same page table index - a collision! Thankfully our page table can also track the PIDs that own each frame, so this is fine. |     |
|    4 |                2 |                                                                                                                                      |     |
