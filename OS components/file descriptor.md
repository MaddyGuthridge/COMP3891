An integer that lets a [[process]] track the [[file|files]] it has open.

Default file descriptors:
- `0` - `stdin`
- `1` - `stdout`
- `2` - `stderr`

New file descriptors are created when using the [[open]] syscall, and destroyed when using the [[close]] syscall.

File descriptors are unique to each process, but there could be duplication between processes.