The core of an operating system, given full privileged-mode control over the CPU (see [[execution mode]].

## Responsibilities

An OS kernel must
- Interleave the execution of [[process]]es to maximise CPU utilisation
- Allocate resources to processes (memory, files, [[thread]]s, etc)
- Support inter-process communication
- Support users (potentially):
	- Creation
	- Management of their processes