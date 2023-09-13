The [[MIPS R3000]] uses a *✨ unique ✨* layout for its memory.

| virtual address | physical address (v is the virtual address)       | size         | name    | purpose                                                                                                                                | cached                    |
| --------------- | ------------------------------------------------- | ------------ | ------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| `0xFFFFFFFF`    |                                                   |              |         |                                                                                                                                        |                           |
|                 | [[translation look-aside buffer\|TLB]] translated | undetermined | `kseg2` | TLB-translated kernel space - used if a [[page table]] is required in [[kernel]] space.                                                |                           |
| `0xC0000000`    |                                                   |              |         |                                                                                                                                        |                           |
|                 | `v - 0xA0000000` (TLB not used)                   | 512 MB       | `kseg1` | Used to access devices (eg frame buffers, etc) and boot ROM, since it is uncached.                                                     | no                        |
| `0xA0000000`    |                                                   |              |         |                                                                                                                                        |                           |
|                 | `v - 0x80000000` (TLB not used)                   | 512 MB       | `kseg0` | Main kernel memory. At a predefined location to avoid TLB refills in the kernel                                                        | yes                       |
| `0x80000000`    |                                                   |              |         |                                                                                                                                        |                           |
|                 | [[translation look-aside buffer\|TLB]] translated | undetermined | `kuseg` | Application space. Used to store programs. This means applications can only use up to 2 GB of RAM (kinda like in old Windows versions) | depends on `n` bit in TLB |
| `0x00000000`    |                                                   |              |         |                                                                                                                                        |                           |

Note that these address layouts are for [[virtual memory]] - unless specified, they could be anywhere in [[physical memory]], and multiple user-land applications could have the same addresses for different physical data.

Although `kseg0` and `kseg1` point to the same physical memory, they are used for different purposes, since `kseg0` is cached and `kseg1` is not.
