When a [[syscall]] is given, a mode switch is performed to change the [[execution mode]] from user mode to kernel mode.

## Switch to kernel mode
1. Processor mode is switched to kernel mode
2. User stack pointer is saved, kernel stack pointer initialised
3. User [[program counter]] saved and [[kernel]] program counter set to kernel entrypoint (interrupt handler).

Kernel entry is strictly enforced to the designated syscall interface.

## Switch to user mode
1. User program counter is loaded and restored
2. User stack pointer is loaded and restored
3. Processor mode is switched to user mode
