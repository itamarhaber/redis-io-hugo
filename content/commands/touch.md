{
  "title": "TOUCH",
  "summary": "Alters the last access time of a key(s). Returns the number of existing keys specified.",
  "group": "generic",
  "tags": [
    "Command",
    "Generic"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of keys that will be touched.",
  "since": "3.2.1",
  "return_summary": "@integer-reply: The number of keys that were touched.",
  "syntax": "key ...",
  "acl_categories": [
    "keyspace",
    "slow"
  ]
}

Alters the last access time of a key(s).
A key is ignored if it does not exist.

@examples

```cli
SET key1 "Hello"
SET key2 "World"
TOUCH key1 key2
```

