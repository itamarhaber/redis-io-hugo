{
  "title": "UNLINK",
  "summary": "Delete a key asynchronously in another thread. Otherwise it is just as DEL, but non blocking.",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each key removed regardless of its size. Then the command does O(N) work in a different thread in order to reclaim memory, where N is the number of allocations the deleted objects where composed of.",
  "since": "4.0.0",
  "return_summary": "@integer-reply: The number of keys that were unlinked.",
  "syntax": "key ...",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

This command is very similar to [DEL](/commands/del): it removes the specified keys.
Just like [DEL](/commands/del) a key is ignored if it does not exist. However the command
performs the actual memory reclaiming in a different thread, so it is not
blocking, while [DEL](/commands/del) is. This is where the command name comes from: the
command just **unlinks** the keys from the keyspace. The actual removal
will happen later asynchronously.

@examples

```cli
SET key1 "Hello"
SET key2 "World"
UNLINK key1 key2 key3
```

