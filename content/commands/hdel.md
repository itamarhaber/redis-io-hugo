{
  "title": "HDEL",
  "summary": "Delete one or more hash fields",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of fields to be removed.",
  "since": "2.0.0",
  "return_summary": "@integer-reply: the number of fields that were removed from the hash, not\nincluding specified but non existing fields.",
  "syntax": "key field ...",
  "acl_categories": [
    "hash",
    "write",
    "slow"
  ]
}

Removes the specified fields from the hash stored at `key`.
Specified fields that do not exist within this hash are ignored.
If `key` does not exist, it is treated as an empty hash and this command returns
`0`.

@examples

```cli
HSET myhash field1 "foo"
HDEL myhash field1
HDEL myhash field2
```

