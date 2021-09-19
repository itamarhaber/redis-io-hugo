{
  "title": "HMSET",
  "summary": "Set multiple hash fields to multiple values",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of fields being set.",
  "since": "2.0.0",
  "return_summary": "@simple-string-reply",
  "deprecated": true,
  "syntax": "key field value ...",
  "acl_categories": [
    "hash",
    "write",
    "slow"
  ]
}

Sets the specified fields to their respective values in the hash stored at
`key`.
This command overwrites any specified fields already existing in the hash.
If `key` does not exist, a new key holding a hash is created.

As per Redis 4.0.0, HMSET is considered deprecated. Please prefer [HSET](/commands/hset) in new code.

@examples

```cli
HMSET myhash field1 "Hello" field2 "World"
HGET myhash field1
HGET myhash field2
```

