{
  "title": "HLEN",
  "summary": "Get the number of fields in a hash",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@integer-reply: number of fields in the hash, or `0` when `key` does not exist.",
  "syntax": "key",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns the number of fields contained in the hash stored at `key`.

@examples

```cli
HSET myhash field1 "Hello"
HSET myhash field2 "World"
HLEN myhash
```

