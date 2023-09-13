A [[syscall]] which copies a [[file descriptor]] to another given file descriptor number. The new file descriptor shares the old file descriptor's [[file]] object.

Used to do IO redirection and the like (as in COMP1521 Shuck Shell).