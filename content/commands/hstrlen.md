{
  "title": "HSTRLEN",
  "summary": "Get the length of the value of a hash field",
  "group": "hash",
  "tags": [
    "Command",
    "Hash"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "3.2.0",
  "return_summary": "@integer-reply: the string length of the value associated with `field`, or zero when `field` is not present in the hash or `key` does not exist at all.",
  "syntax": "key field",
  "acl_categories": [
    "hash",
    "slow"
  ]
}

Returns the string length of the value associated with `field` in the hash stored at `key`. If the `key` or the `field` do not exist, 0 is returned.

@examples

```cli
HMSET myhash f1 HelloWorld f2 99 f3 -256
HSTRLEN myhash f1
HSTRLEN myhash f2
HSTRLEN myhash f3
```

