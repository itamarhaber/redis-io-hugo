{
  "title": "SCARD",
  "summary": "Get the number of members in a set",
  "group": "set",
  "tags": [
    "Command",
    "Set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.0.0",
  "return_summary": "@integer-reply: the cardinality (number of elements) of the set, or `0` if `key`\ndoes not exist.",
  "syntax": "key",
  "acl_categories": [
    "set",
    "slow"
  ]
}

Returns the set cardinality (number of elements) of the set stored at `key`.

@examples

```cli
SADD myset "Hello"
SADD myset "World"
SCARD myset
```

