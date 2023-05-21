A hashed page table is a [[page table]] that uses a hash table to map from [[virtual memory]] to [[physical memory]]. It acts as an improvement over [[inverted page table|inverted page tables]], and allows for efficient [[memory sharing]] by supporting more than one mapping to the same [[frame]].

This also allows for boot-time tuning, based on physical memory size, the amount of expected sharing, and requirements for hash collision avoidance. For example, if you only expect one process to use the majority of memory, you wouldn't need to optimise for sharing as much.

The length of the table should be a power-of-2 multiple of the number of frames of physical memory.

## Internal chaining layout
When internal chaining is used, a `next` property is used to give the `next` index to allow for a search to proceed when a hash collision occurs.
| *index* | PID | virtual page number | physical frame number | ctrl | next | comment                                                                                       |
| -----:| ---:| -------------------:| ---------------------:| ---- | ---- | --------------------------------------------------------------------------------------------- |
|     0 |     |                     |                       |      |      | empty frames                                                                                  |
|     1 |     |                     |                       |      |      |                                                                                               |
|     2 |   1 |                0x1A |                  0x10 |      |      | this frame has an entry                                                                       |
|     3 |   2 |                0x3C |                  0x32 |      | 5    | another entry collided with this entry, so the next property is set                           |
|     4 |     |                     |                       |      |      |                                                                                               |
|     5 |   4 |                0x3C |                  0x14 |      |      | Even though the hash would have put it at index 3, it went here because of the collision      |
|     6 |   3 |                0x5D |                  0xA2 |      |      | The frame is shared with a different process                                                  |
|     7 |   5 |                0x28 |                  0xA2 |      |      | Even though the frame numbers are equal, there is no need for the page numbers to be the same |

## External chaining layout
When external chaining is used, hash collisions are resolved by using an additional data structure such as a binary tree to store all of the entries at a particular index.

### Table layout

| *index* | \*frame_tree | comment                             |
| ------- | ------------ | ----------------------------------- |
| 0       | `NULL`       | No entry with this hash             |
| 1       | `0x52345`    | Link to a tree with all the entries |

### Tree structure
| property | description                      |
| -------- | -------------------------------- |
| left     | Element to the left in the tree  |
| right    | Element to the right in the tree |
|          |                                  |

## Lookup process
- Given virtual address
- Calculate the page number and offset
- Hash it to get the key
- Look up that key
- Get the page
- Calculate the physical address

## Performance

Each [[virtual memory]] reference lookup causes two [[physical memory]] accesses - one to fetch the page table, and one to fetch the actual data. The solution is to use a [[translation look-aside buffer|TLB]].
