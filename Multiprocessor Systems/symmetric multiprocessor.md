Symmetric multiprocessing describes when the [[kernel]] is run on all [[CPU|CPUs]], and the [[process|processes]] and [[memory resources]] are shared between all cores, including for kernel execution. This offers massive performance benefits, but means that our kernel needs to use proper [[synchronisation primitive]] to avoid disaster.

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
We can't disable interrupts like we could before