{
  "title": "SISMEMBER",
  "summary": "Determine if a given value is a member of a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply, specifically:\n\n* `1` if the element is a member of the set.\n* `0` if the element is not a member of the set, or if `key` does not exist.",
  "syntax": "key member",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns if `member` is a member of the set stored at `key`.

@examples

```cli
SADD myset "one"
SISMEMBER myset "one"
SISMEMBER myset "two"
```

