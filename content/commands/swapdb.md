{
  "title": "SWAPDB",
  "summary": "Swaps two Redis databases",
  "group": "server",
  "tags": [
    "Command",
    "Server"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the count of clients watching or blocking on keys from both databases.",
  "since": "4.0.0",
  "return_summary": "@simple-string-reply: `OK` if `SWAPDB` was executed correctly.",
  "syntax": "index1 index2",
  "acl_categories": [
    "keyspace",
    "dangerous",
    "write",
    "slow"
  ]
}

This command swaps two Redis databases, so that immediately all the
clients connected to a given database will see the data of the other database, and
the other way around. Example:

    SWAPDB 0 1

This will swap database 0 with database 1. All the clients connected with database 0 will immediately see the new data, exactly like all the clients connected with database 1 will see the data that was formerly of database 0.

@examples

```
SWAPDB 0 1
```

