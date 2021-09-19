{
  "title": "ZCARD",
  "summary": "Get the number of members in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(1)",
  "since": "1.2.0",
  "return_summary": "@integer-reply: the cardinality (number of elements) of the sorted set, or `0`\nif `key` does not exist.",
  "syntax": "key",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the sorted set cardinality (number of elements) of the sorted set stored
at `key`.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZCARD myzset
```

