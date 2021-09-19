{
  "title": "SINTERSTORE",
  "summary": "Intersect multiple sets and store the resulting set in a key",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N*M) worst case where N is the cardinality of the smallest set and M is the number of sets.",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the number of elements in the resulting set.",
  "syntax": "destination key ...",
  "acl_categories": [
    "set",
    "write",
    "slow"
  ]
}

This command is equal to [SINTER](/commands/sinter), but instead of returning the resulting set,
it is stored in `destination`.

If `destination` already exists, it is overwritten.

@examples

```cli
SADD key1 "a"
SADD key1 "b"
SADD key1 "c"
SADD key2 "c"
SADD key2 "d"
SADD key2 "e"
SINTERSTORE key key1 key2
SMEMBERS key
```

