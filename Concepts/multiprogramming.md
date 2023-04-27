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