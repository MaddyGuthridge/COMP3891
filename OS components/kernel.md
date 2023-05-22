The core of an operating system, given full privileged-mode control over the [[CPU]] (see [[execution mode]]).

## Responsibilities

An OS kernel must
- Handle [[exception|exceptions]] such as [[syscall|syscalls]] and the like
- Interleave the execution of [[process|processes]] to maximise CPU utilisation (see [[scheduling]])
- Allocate resources to processes (memory, files, [[thread|threads]], etc)
- Support inter-process communication
- Support users (potentially):
	- Creation
	- Management of their processes
- Be able to load [[drivers]] in order to support other hardware, or interact with a [[BIOS]] to communicate with hardware.