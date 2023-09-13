Emulated [[file system]], which allows us to store data in [[sys-161]] by mapping the file system on the host machine to be accessible to [[os-161]].

## OS 161 Root

The file system is mounted from `.../cs3231/root` on the host machine.

- /
	- bin
		- cat
		- cp
		- false
		- ls
		- sh
		- true
	- include
		- kern
			- mips
		- sys
		- test
	- lib
	- man
		- bin
		- libc
		- syscall
	- sbin
	- testbin
		- asst2
