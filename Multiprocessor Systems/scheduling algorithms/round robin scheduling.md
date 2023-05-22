Round robin [[scheduling]] is an [[interactive scheduling|interactive]] [[scheduling algorithm]].

- Each process is given a time slice to run in.
- When the time slice expires, the next process preempts the current process, and so on
- The preempted process is placed at the end of the queue

## Implementation
- Ready queue
- Regular timer interrupt
