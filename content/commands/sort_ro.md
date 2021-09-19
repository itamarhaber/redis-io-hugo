{
  "title": "SORT_RO",
  "summary": "Sort the elements in a list, set or sorted set. Read-only variant of SORT.",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N+M*log(M)) where N is the number of elements in the list or set to sort, and M the number of returned elements. When the elements are not sorted, complexity is O(N).",
  "since": "7.0.0",
  "return_summary": "@array-reply: a list of sorted elements.",
  "syntax": "key [BY pattern] [LIMIT offset count] [GET pattern ...] [ASC|DESC] [ALPHA]",
  "acl_categories": [
    "list",
    "set",
    "sortedset",
    "dangerous",
    "slow"
  ]
}

Read-only variant of the [SORT](/commands/sort) command. It is exactly like the original [SORT](/commands/sort) but refuses the `STORE` option and can safely be used in read-only replicas.

Since the original [SORT](/commands/sort) has a `STORE` option it is technically flagged as a writing command in the Redis command table. For this reason read-only replicas in a Redis Cluster will redirect it to the master instance even if the connection is in read-only mode (see the [READONLY](/commands/readonly) command of Redis Cluster).

Since Redis 7.0.0, the [SORT_RO](/commands/sort_ro) variant was introduced in order to allow [SORT](/commands/sort) behavior in read-only replicas without breaking compatibility on command flags.

See original [SORT](/commands/sort) for more details.

@examples

```
SORT_RO mylist BY weight_*->fieldname GET object_*->fieldname
```

