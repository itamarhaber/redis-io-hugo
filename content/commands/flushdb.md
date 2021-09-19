{
  "title": "FLUSHDB",
  "summary": "Remove all keys from the current database",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys in the selected database",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "syntax": "[ASYNC|SYNC]",
  "acl_categories": [
    "keyspace",
    "dangerous",
    "write",
    "slow"
  ]
}

Delete all the keys of the currently selected DB.
This command never fails.

By default, [FLUSHDB](/commands/flushdb) will synchronously flush all keys from the database.
Starting with Redis 6.2, setting the **lazyfree-lazy-user-flush** configuration directive to "yes" changes the default flush mode to asynchronous.

It is possible to use one of the following modifiers to dictate the flushing mode explicitly:

* `ASYNC`: flushes the database asynchronously
* `SYNC`: flushes the database synchronously

Note: an asynchronous [FLUSHDB](/commands/flushdb) command only deletes keys that were present at the time the command was invoked. Keys created during an asynchronous flush will be unaffected.
