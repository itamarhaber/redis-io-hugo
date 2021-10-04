The [MEMORY MALLOC-STATS](/commands/memory-malloc-stats) command provides an internal statistics report from
the memory allocator.

This command is currently implemented only when using **jemalloc** as an
allocator, and evaluates to a benign NOOP for all others.

