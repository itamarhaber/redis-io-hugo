{
  "title": "MOVE",
  "summary": "Move a key to another database",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if `key` was moved.\n* `0` if `key` was not moved.",
  "syntax": "key db",
  "acl_categories": [
    "keyspace",
    "write",
    "slow"
  ]
}

Move `key` from the currently selected database (see [SELECT](/commands/select)) to the specified
destination database.
When `key` already exists in the destination database, or it does not exist in
the source database, it does nothing.
It is possible to use [MOVE](/commands/move) as a locking primitive because of this.

