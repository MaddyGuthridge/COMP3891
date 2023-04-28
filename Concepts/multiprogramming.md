Designing operating system to allow multiple processes to run at once.

Most modern operating systems implement a [[page table]] and/or a [[swap]] space to achieve this.

## Dividing up memory

- Static partitioning
	- Partition memory for processes at boot time
- Dynamic partitioning
	- More flexible, since processes only take the resources they need
	- Processes still need to say how much memory they need ahead of time
- Dynamic allocation
	- Allocate memory on-the-fly
	- Essentially `malloc()`

## Tracking who can access memory

It's important to ensure [[process]]es can't access each other's memory. There are several strategies for this.

### Base and Limit registers
Track the "base" (lowest address) and "limit" (width of address space) for processes inside the CPU. Memory addresses are automatically adjusted by the CPU to fit within the limit starting from the base.

```python
def translate_base_and_limit(cpu, address):
    if address > cpu.limit_register:
	    raise Exception("segfault")
	return address + base
```

This technique was used in old mainframes, but isn't used since it requires dynamic partitioning of physical memory (rather than dynamic allocation), which was limiting.

Base and limit registers are need to be recalculated:
- Load time
- Relocation ([[memory compaction]])
- On context switch