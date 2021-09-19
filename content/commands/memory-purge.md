{
  "title": "MEMORY PURGE",
  "summary": "Ask the allocator to release memory",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "4.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "",
  "acl_categories": [
    "slow"
  ]
}

The [MEMORY PURGE](/commands/memory-purge) command attempts to purge dirty pages so these can be
reclaimed by the allocator.

This command is currently implemented only when using **jemalloc** as an
allocator, and evaluates to a benign NOOP for all others.

