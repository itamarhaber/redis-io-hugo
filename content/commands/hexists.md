{
  "title": "HEXISTS",
  "summary": "Determine if a hash field exists",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the hash contains `field`.\n* `0` if the hash does not contain `field`, or `key` does not exist.",
  "syntax": "key field",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns if `field` is an existing field in the hash stored at `key`.

@examples

```cli
HSET myhash field1 "foo"
HEXISTS myhash field1
HEXISTS myhash field2
```

