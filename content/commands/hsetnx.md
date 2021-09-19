{
  "title": "HSETNX",
  "summary": "Set the value of a hash field, only if the field does not exist",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if `field` is a new field in the hash and `value` was set.\n* `0` if `field` already exists in the hash and no operation was performed.",
  "syntax": "key field value",
  "acl_categories": [
    "hash",
    "write",
    "slow"
  ]
}

Sets `field` in the hash stored at `key` to `value`, only if `field` does not
yet exist.
If `key` does not exist, a new key holding a hash is created.
If `field` already exists, this operation has no effect.

@examples

```cli
HSETNX myhash field "Hello"
HSETNX myhash field "World"
HGET myhash field
```

