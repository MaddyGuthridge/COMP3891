When any kind of jump or branch is done, the next instruction always executes. This can be used to optimise code further, but makes it an absolute pain to read disassembled MIPS code.

Also need to do it when using `lw` (load word) since the memory isn't quick enough.