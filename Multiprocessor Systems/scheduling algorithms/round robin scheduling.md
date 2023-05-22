Round robin [[scheduling]] is an [[interactive scheduling|interactive]] [[scheduling algorithm]].

- Each process is given a time slice to run in.
- When the time slice expires, the next process [[preemption|preempts]] the current process, and so on
- The preempted process is placed at the end of the queue

## Implementation
- Ready queue
- Regular timer interrupt

## Pros
- Fair
- Easy to implement

## Cons
- Assumes all tasks are equal in priority

## Timeslice duration
We need to decide on a good timeslice duration.

- If it is **too short**, then we waste time switching between processes due to the overhead of [[context switch|context switching]].
- If it is **too long**, then we risk making the system unresponsive if the app handling a particular even has to wait too long in the queue.
