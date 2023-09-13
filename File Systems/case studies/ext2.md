Extended File System 2

[[inode]]-based [[file system]], which evolved from the Minix filesystem.

## Features
- Configurable block size (set at file system creation)
- Performance optimisations to improve locality, compared to BSD's FFS

## Problems
Consistency checker needed to run on start-up, since there was a risk of FS corruption if there was an unclean unmount (eg a crash).

## Block representation
- First 12 [[block]]s stored directly in inode
- From then, there is a single indirect block number, which references a block containing more block numbers
	- This is only enough for `268 KiB` of space though for a `1Kb` block size with `4b` block numbers
- If we need more space, we can additionally use a double indirect, which is a block containing the block numbers of single indirect blocks
- And if you somehow need even more space, you can also use a triple indirect, which is a block containing the block numbers of double indirect blocks

## Access patterns
Assuming inode already in memory

### Read 1 byte
**Best**: 1 access (reading data block)
**Worst**: 4 accesses (triple indirection, then reading data block)

### Write 1 byte
**Best**: 1 access (writing data block)
**Worst**: 4 accesses (triple indirection, then writing data block)
