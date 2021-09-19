{
  "title": "SAVE",
  "summary": "Synchronously save the dataset to disk",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "TBD",
  "since": "1.0.0",
  "return_summary": "@simple-string-reply: The commands returns OK on success.",
  "syntax": "",
  "acl_categories": [
    "admin",
    "dangerous",
    "slow"
  ]
}

The [SAVE](/commands/save) commands performs a **synchronous** save of the dataset producing a
_point in time_ snapshot of all the data inside the Redis instance, in the form
of an RDB file.

You almost never want to call [SAVE](/commands/save) in production environments where it will
block all the other clients.
Instead usually [BGSAVE](/commands/bgsave) is used.
However in case of issues preventing Redis to create the background saving child
(for instance errors in the fork(2) system call), the [SAVE](/commands/save) command can be a
good last resort to perform the dump of the latest dataset.

Please refer to the [persistence documentation][tp] for detailed information.

[tp]: /topics/persistence
