{
  "title": "FLUSHALL",
  "summary": "Remove all keys from all databases",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the total number of keys in all databases",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply",
  "history": [
    [
      "4.0.0",
      "Added the `ASYNC` flushing mode modifier."
    ],
    [
      "6.2.0",
      "Added the `!SYNC` flushing mode modifier and the **lazyfree-lazy-user-flush** configuration directive."
    ]
  ],
  "syntax": "[ASYNC|SYNC]",
  "acl_categories": [
    "keyspace",
    "dangerous",
    "write",
    "slow"
  ]
}

Delete all the keys of all the existing databases, not just the currently selected one.
This command never fails.

By default, [FLUSHALL](/commands/flushall) will synchronously flush all the databases.
Starting with Redis 6.2, setting the **lazyfree-lazy-user-flush** configuration directive to "yes" changes the default flush mode to asynchronous.

It is possible to use one of the following modifiers to dictate the flushing mode explicitly:

* `ASYNC`: flushes the databases asynchronously
* `SYNC`: flushes the databases synchronously

Note: an asynchronous [FLUSHALL](/commands/flushall) command only deletes keys that were present at the time the command was invoked. Keys created during an asynchronous flush will be unaffected.

