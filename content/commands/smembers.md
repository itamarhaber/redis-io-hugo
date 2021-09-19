{
  "title": "SMEMBERS",
  "summary": "Get all the members in a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the set cardinality.",
  "since": "1.0.0",
  "return_summary": "@array-reply: all elements of the set.",
  "syntax": "key",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns all the members of the set value stored at `key`.

This has the same effect as running [SINTER](/commands/sinter) with one argument `key`.

@examples

```cli
SADD myset "Hello"
SADD myset "World"
SMEMBERS myset
```

