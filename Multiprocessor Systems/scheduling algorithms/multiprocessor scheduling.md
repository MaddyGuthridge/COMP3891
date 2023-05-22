There are many strategies to bring [[scheduling algorithm|scheduling algorithms]] to [[multiprocessor system|multiprocessor systems]].

## Single shared ready queue
Just uses a single scheduling system and a global [[lock]].

### Pros
- Simple
- Automatic load balancing

### Cons
- Lock contention on the ready queue becomes a [[bottleneck]], especially when
- Processes are assigned to a random [[CPU]] each time, meaning they're more likely to get cache misses
- Some CPUs may have different performance, for example on 12th-gen Intel processors, the [hybrid architecture](https://www.intel.com/content/www/us/en/developer/articles/technical/hybrid-architecture.html) means there are both performance and efficiency cores, and the [[operating system|OS]] needs to assign processes to all of them decisively to get the best performance.


# Affinity scheduling
We try to run a process on the same core that it ran on last time.

## Multiple queue multiprocessor scheduling
- Each [[CPU]] has its own [[ready queue]].
- A corase-grained algorithm distributes the work to CPUs to avoid having a central data structure.
- A fine-grained scheduler is run for each CPU and tries to select from its own queue.
- If no work is available it "steals work" from another CPU by running one of its tasks instead (ensuring that if tasks were poorly assigned we don't leave some [[process|processes]] starved).

### Pros
- No lock-contention for already-assigned processes
- Load balancing from coarse-grained algorithm
- Automatic affinity to a [[CPU]] to avoid [[CPU cache|cache]] misses.
