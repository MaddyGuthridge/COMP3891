An inverted [[page table]] (IPT) has an entry for every [[frame]], rather than an entry for every [[page]]. This means that it can be stored globally, rather than having a different instance for each virtual [[address space]].

It uses a hash anchor table to calculate mappings from [[virtual memory]] to [[physical memory]], since otherwise lookups would only be possible from frames to pages.

