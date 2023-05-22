Whenever there are multiple tasks, we need to decide which order to run them in, and what tasks to assign to which [[CPU|CPUs]].

- Multiple [[process|processes]]: choose between ready processes
- Multiple jobs (on a [batch system](https://en.wikipedia.org/wiki/Batch_processing)): choose between waiting jobs, although it's usually just the first one in the queue
- Multiple users: choose which processes to run from which users, and maybe prevent users from stepping on the toes of other users

There are many [[scheduling algorithm|algorithms]] that can be used to schedule tasks.

## When not to schedule

Scheduling isn't required for
- Simple systems (eg washing machines)
- Early computers (eg when batching)

Scheduling is a must-have for any kind of meaningful computer system these days.
