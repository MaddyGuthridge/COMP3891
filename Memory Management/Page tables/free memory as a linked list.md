The "classical" approach.

Store allocation info as a linked list of available "holes" in the memory, in order of increasing address.

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
- Fast-fit algorithm to find first suitable free region (linked list traversal)
	- Allocations biased towards start of memory
	- Larger blocks available at end of memory