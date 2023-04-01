Extended File System 2

[[inode]]-based [[file system]], evolved from the Minix filesystem.

## Features
- Configurable block size (set at file system creation)
- Performance optimisations to improve locality, compared to BSD's FFS

## Problems
Consistency checker needed to run on start-up, since there was a risk of FS corruption if there was an unclean unmount (eg a crash).
