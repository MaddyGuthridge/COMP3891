Symmetric multiprocessing describes when the [[kernel]] is run on all [[CPU|CPUs]], and the [[process|processes]] and [[memory resources]] are shared between all cores, including for kernel execution. This offers massive performance benefits, but means that our kernel needs to use proper [[synchronisation primitive]] to avoid disaster.

## Strategies

- A global "big lock" for the [[kernel]]. This means that if performance is compute-bound we'll still get good performance. However, if we are limited by kernel performance, this quickly becomes a bottleneck.
- Locks for each component of the [[kernel]]