An operating system is a collection of software that provides a layer of abstraction that allows other software to run independently of the machine hardware.

An OS is comprised of various components:

- The [[kernel]] is the core of the OS, handling requests from [[userland]] programs and translating them to actions on hardware, such as [[file system]] operations. This is most often done using [[syscall|system calls]].
	- The [[virtual file system]] is used to abstract various [[file system|file systems]], creating a global hierarchy of virtual files that can represent actual files, memory spaces, other processes, and pretty much anything else in the OS.
	- [[drivers|Drivers]] are used to facilitate communication with physical hardware