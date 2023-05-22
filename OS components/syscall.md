- Aka "trap" (since we trap execution)

System calls (usually shortened to *syscall*) are a way for userland code to communicate with the operating system. An OS will have a strictly-defined interface that a program can access by giving a syscall [[exception]] on the [[CPU]]. The [[kernel]] then assumes control of the processor, and performs the required action before returning control back to the [[process]].

## Some important syscalls
There are hundreds of them, but these are the ones that you might want to know:

- [[fork]] - create a new process
- `waitpid` - wait for a process with the given PID to exit
- `execve` - replace the current process with the given process
	- To start a new process, you should [[fork]] then `execve`
- `exit` - close the program
- [[open]] - create a new file or open an existing file
- [[reboot]] - reboot the system

To see more info on Linux syscalls, run `man syscall`

## Why not directly call functions in the Kernel?

Syscalls are more secure - kernel can ensure requests are legal, so there's no risk of stack corruption in the kernel.
