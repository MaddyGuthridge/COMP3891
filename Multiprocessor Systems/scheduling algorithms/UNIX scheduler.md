In a traditional UNIX system, [[scheduling]] priorities are calculated using the following expression:

## $priority = CPU + nice + base$

Where

#### $CPU$
The number of clock ticks this [[process]] has consumed recently. This means that if a process uses more [[CPU]], it is given a lower priority, preventing it from hogging resources. This helps prevent [[starvation]] by ensuring that CPU-heavy processes gradually get lower and lower priorities, giving other processes a turn.

#### $nice$
A static value given by the user to increase or decrease its priority (eg `-4` increases the priority by `4`). A higher "niceness" means the [[process]] is more nice to other processes, and therefore yields its processing power to them more often.

On UNIX-like systems, you can run `nice -n [number] program *args` to assign a new process a niceness value.

#### $base$
A dynamic priority modifier based on the status of the process.

- `-4` waiting for disk IO
- `-3` waiting for disk buffer
- `-2` waiting for terminal input
- `-1` waiting for terminal output
- `0` waiting for child to exist

This helps ensure that processes that are IO-bound are given higher priority to keep them responsive.
