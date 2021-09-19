{
  "title": "MEMORY MALLOC-STATS",
  "summary": "Show allocator internal stats",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "4.0.0",
  "return_summary": "@bulk-string-reply: the memory allocator's internal statistics report",
  "syntax": "",
  "acl_categories": [
    "slow"
  ]
}

The [MEMORY MALLOC-STATS](/commands/memory-malloc-stats) command provides an internal statistics report from
the memory allocator.

This command is currently implemented only when using **jemalloc** as an
allocator, and evaluates to a benign NOOP for all others.

