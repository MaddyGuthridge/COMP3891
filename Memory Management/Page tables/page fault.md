Referencing an invalid [[page]] triggers a page fault, an exception handled by the OS.

Two kinds of fault
- Illegal address: send `SIGSEGV` signal to process (at least on Linux)
- Page not resident
	- Get an empty frame
	- Load page from disk
	- Update [[page table]] (enter frame number, set valid bit, etc)
	- Restart the faulting instruction
