{
  "title": "MODULE LOAD",
  "summary": "Load a module",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "4.0.0",
  "return_summary": "@simple-string-reply: `OK` if module was loaded.",
  "syntax": "path [arg]",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

Loads a module from a dynamic library at runtime.

This command loads and initializes the Redis module from the dynamic library
specified by the `path` argument. The `path` should be the absolute path of the
library, including the full filename. Any additional arguments are passed
unmodified to the module.

**Note**: modules can also be loaded at server startup with `loadmodule`
configuration directive in `redis.conf`.

