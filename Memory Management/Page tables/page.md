A page is a contiguous chunk of bits in [[virtual memory]], which is translated to a [[frame]] in [[physical memory]] by a [[page table]].

To calculate a page number, you can use a bitshift operation based on the size of the page. For example, for a 4 KB page, you could use `address >> 12`, since $log_2(4096) = 12$

## Offset

An offset is used within a page number to determine how far within the page to look. It can be calculated given the page size using a binary and operation. For example, for a 4 KN page, you could use `address & 0xFFF`, since `0xFFF` is 12 bits of binary 1s (`0b1111_1111_1111`), where $12 = log_2(4096)$.
