For most of the OS course, it is assumed that we're running on a single processor system (this is the case in UNSW's version of [[os-161]], but of course it's always more complicated than that.

Most real-world systems are multiprocessor (MP) systems, meaning they'll have multiple [[CPU]] cores, or even multiple CPUs. [[operating system|Operating systems]] need to be able to allow applications to run with high performance on [[multi-core processor|multi-core]] machines.

This requires design considerations, such as [[scheduling]], [[CPU cache|caching]] and [[bus-based uniform memory access|memory access]].
