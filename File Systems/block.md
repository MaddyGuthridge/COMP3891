A block is a collection of bytes. Disks are split into blocks, and [[file system]]s track which files belong to which blocks.

## Block sizes

Most hard-drives use "sectors" usually 512 bytes. Block sizes can only be a power of those sector sizes.

```js
block_size = sector_size * 2 ** n
```
Where `n` is any integer.

## Types of blocks
- Data blocks, containing file data
- Disk blocks, containing data used to construct the file system tree (eg a [[file access table allocation|file access table]])