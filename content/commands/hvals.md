{
  "title": "HVALS",
  "summary": "Get all the values in a hash",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the size of the hash.",
  "since": "2.0.0",
  "return_summary": "@array-reply: list of values in the hash, or an empty list when `key` does\nnot exist.",
  "syntax": "key",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns all values in the hash stored at `key`.

@examples

```cli
HSET myhash field1 "Hello"
HSET myhash field2 "World"
HVALS myhash
```

