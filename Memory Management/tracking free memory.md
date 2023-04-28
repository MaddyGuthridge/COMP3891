The "classical" approach is to use a linked list.

Store allocation info as a linked list of available "holes" in the [[physical memory|memory]], in order of increasing address.

```c
/** A node in our linked list */
struct memory_hole_node {
	/** Address of this hole of free space in memory */
    paddr_t address;
    /** Size of the hole */
    size_t size;
    /** Pointer to the next hole in memory */
    struct memory_hole_node *link;
}
```

- Makes it easy to merge holes together (coalescing)

## Algorithms for finding unallocated space

***Fast-fit algorithm*** to find first suitable free region (linked list traversal)
- Allocations biased towards start of memory
- Larger blocks available at end of memory

***Next-fit algorithm*** to continue searching from the point of the last successful allocation
- Allocations more evenly distributed
- Seems like this makes it faster *BUT NO* since it breaks up the larger free space at the end of memory
***Best-fit algorithm*** to find free space that best matches the request size (the smallest hole that still fits)
- Since the nodes are in order of address, we need to iterate over all of them, meaning that this is very slow
- The holes it leaves are often less usable (since they are smaller)
- Really not a good idea
***Worst-fit algorithm*** to allocate everything in the worst-fitting hole
- Still iterates over the whole list of holes (very slow)
- Doesn't even reduce fragmentation

There are many other approaches, all with weird names. No particular allocators are the "industry standard".
- "Lazy buddy"
- "Slab" (optimised for a small number of known-size objects)