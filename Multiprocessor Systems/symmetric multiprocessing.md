Symmetric multiprocessing (SMP) describes when the [[kernel]] is run on all [[CPU|CPUs]], and the [[process|processes]] and [[memory resources]] are shared between all cores, including for kernel execution. This offers massive performance benefits, but means that our kernel needs to use proper [[synchronisation primitive]] to avoid disaster.

## Strategies

- A global "big lock" for the [[kernel]]. This means that if performance is compute-bound we'll still get good performance. However, if we are limited by kernel performance, this quickly becomes a bottleneck.
- Locks for each component of the [[kernel]]. For example, we could have a lock for the [[virtual file system]], and another for the [[virtual memory]] subsystem. If a single subsystem is hit too hard, we still get the bottleneck.
- Data-based locks, where individual pieces of data are locked as required.

### Case study: Linux

- Kernel 1.x was uniprocessor
- Kernel 2.0 used a big lock
- Kernel 2.2 still used a big lock, but with interrupt handling locks
- Kernel 2.4 added subsystem locks
- Kernel 2.6 had most code out of the big lock, using data-based locks instead.

## Ensuring synchronisation
We can't disable interrupts like we can in uniprocessor systems, since that doesn't stop other CPUs from executing in parallel.

Instead we need dedicated hardware to facilitate concurrency.

- Can't directly use a "test and set" instruction, since memory could also be accessed by other cores.
- However, we could use it if we can block access to the [[bus]] for the duration of the instruction.
	- But that's sloooowwww, especially due to [[spin lock|spin locks]] using busy waiting when there is lock contention
	- This causes the [[bus]] bandwidth to be wasted
- Instead, we could read the lock over and over until it changes, then we could run the test and set.
	- With a cache, this means that it'll work without clogging up the [[bus]]
	```c
	start:
	  while (lock == 1);
	  r = TSL(lock);
	  if (r == 1) {
		goto start;
	  }
	  // We now own the lock
	```

## To spin or to block

On a uniprocessor, you should always block (switch to another task), since spinning wastes CPU that could be used by another task.

On SMP systems, it's less clear, since the lock may be held by a different CPU - if that's the case a [[context switch]] might be slower than just waiting.
