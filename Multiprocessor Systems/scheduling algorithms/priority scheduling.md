We can improve on the [[round robin scheduling|round robin]] [[scheduling algorithm]] by assigning each task a priority. The [[scheduling|scheduler]] can then always prefer higher priority tasks over lower priority ones.

## Internal vs external priorities
- Internal priorities are determined by the [[operating system]] (eg if a process is I/O-bound or [[CPU]] bound)
- External priorities are provided by the user or system administrator (eg they chose it in their OS system monitor app)

## Algorithms
Priority scheduling is used by the multi-level round robin algorithm.

### Multi-level round robin
Uses a series of "queue headers" - one for each priority. Top priority queues are emptied before executing lower queues.

This means that low priority tasks can [[starvation|starve]]
