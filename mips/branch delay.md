In [[MIPS]], when any kind of jump or branch is done, the next instruction always executes. This can be used to optimise code further, and is taken advantage of by compilers, but makes it an absolute pain to read disassembled code.

Also need to do it when using `lw` (load word) since the memory isn't quick enough.

If there is nothing to do while waiting, you should do a `nop` instruction.