{
  "title": "HGET",
  "summary": "Get the value of a hash field",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "2.0.0",
  "return_summary": "@bulk-string-reply: the value associated with `field`, or `nil` when `field` is not\npresent in the hash or `key` does not exist.",
  "syntax": "key field",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns the value associated with `field` in the hash stored at `key`.

@examples

```cli
HSET myhash field1 "foo"
HGET myhash field1
HGET myhash field2
```

