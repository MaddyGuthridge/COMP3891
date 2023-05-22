A file is a collection of arbitrary data. What it contains specifically is up to the programs interacting with it.

Only file type that the [[kernel]] needs to deal with is executables (eg `.exe` on Windows)

Some files aren't really files, especially on UNIX-y systems:

- Directories
- Symbolic links
- Device files 
	- Read/write to a device like it was a file
	- Block devices

## File attributes

Files also have metadata that can be useful

- Access
	- Owner
	- Read/write/execute permissions
- Times
	- Created
	- Modified
	- Accessed
- Size
- Locks (to prevent data races)
- And more, depending on OS