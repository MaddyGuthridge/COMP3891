A page is a contiguous chunk of bits in [[virtual memory]], which is translated to a [[frame]] in [[physical memory]] by a [[page table]].

To calculate a page number, you can use a bitshift operation based on the size of the page.

Eg, for a 4 KB page, you could use `adderss >> 12`, since $log_