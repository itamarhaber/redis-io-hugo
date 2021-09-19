{
  "title": "HGETALL",
  "summary": "Get all the fields and values in a hash",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the size of the hash.",
  "since": "2.0.0",
  "return_summary": "@array-reply: list of fields and their values stored in the hash, or an\nempty list when `key` does not exist.",
  "syntax": "key",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns all fields and values of the hash stored at `key`.
In the returned value, every field name is followed by its value, so the length
of the reply is twice the size of the hash.

@examples

```cli
HSET myhash field1 "Hello"
HSET myhash field2 "World"
HGETALL myhash
```

