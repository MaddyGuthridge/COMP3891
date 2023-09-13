An operating system (OS) is a collection of software that provides a layer of abstraction that allows other software to run independently of the machine hardware.

An OS is comprised of various components:

- The [[kernel]] is the core of the OS, handling requests from [[userland]] programs and translating them to actions on hardware, such as [[file system]] operations. This is most often done using [[syscall|system calls]].
	- The [[virtual file system]] is used to abstract various [[file system|file systems]] and bring together various [[disk|disks]], creating a global hierarchy of virtual files that can represent actual files, memory spaces, other processes, and pretty much anything else in the OS. The specific things represented by the file system depends on the OS - UNIX-like systems represent almost everything as a file, for example.
	- The [[virtual memory]] system is used to give each [[process]] its own unique address space, allowing them to run independently and share [[RAM]] efficiently.
	- The [[scheduling|task scheduler]] system is responsible for allowing multiple processes to run concurrently
	- [[drivers|Drivers]] are used to facilitate communication with physical hardware, helping the OS to run on multiple different kinds of devices.
- A collection of C header files is often provided to allow for code to be written in a generic way, where by replacing the header files, developers can target different operating systems. An example of this is [the C standard library (libc)](https://en.wikipedia.org/wiki/C_standard_library).
- A collection of [[userland]] programs that can be run by a user to interact with the system (for example a shell).