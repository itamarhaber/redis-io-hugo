{
  "title": "HSET",
  "summary": "Set the string value of a hash field",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1) for each field/value pair added, so O(N) to add N field/value pairs when the command is called with multiple field/value pairs.",
  "since": "2.0.0",
  "return_summary": "@integer-reply: The number of fields that were added.",
  "syntax": "key field value ...",
  "acl_categories": [
    "hash",
    "write",
    "slow"
  ]
}

Sets `field` in the hash stored at `key` to `value`.
If `key` does not exist, a new key holding a hash is created.
If `field` already exists in the hash, it is overwritten.

As of Redis 4.0.0, HSET is variadic and allows for multiple `field`/`value` pairs.

@examples

```cli
HSET myhash field1 "Hello"
HGET myhash field1
```

