{
  "title": "SDIFFSTORE",
  "summary": "Subtract multiple sets and store the resulting set in a key",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the total number of elements in all given sets.",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the number of elements in the resulting set.",
  "syntax": "destination key ...",
  "acl_categories": [
    "set",
    "write",
    "slow"
  ]
}

This command is equal to [SDIFF](/commands/sdiff), but instead of returning the resulting set, it
is stored in `destination`.

If `destination` already exists, it is overwritten.

@examples

```cli
SADD key1 "a"
SADD key1 "b"
SADD key1 "c"
SADD key2 "c"
SADD key2 "d"
SADD key2 "e"
SDIFFSTORE key key1 key2
SMEMBERS key
```

