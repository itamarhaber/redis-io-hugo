{
  "title": "SMISMEMBER",
  "summary": "Returns the membership associated with the given elements for a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N) where N is the number of elements being checked for membership",
  "since": "6.2.0",
  "return_summary": "@array-reply: list representing the membership of the given elements, in the same\norder as they are requested.",
  "syntax": "key member ...",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns whether each `member` is a member of the set stored at `key`.

For every `member`, `1` is returned if the value is a member of the set, or `0` if the element is not a member of the set or if `key` does not exist.

@examples

```cli
SADD myset "one"
SADD myset "one"
SMISMEMBER myset "one" "notamember"
```

