{
  "title": "ZINTERCARD",
  "summary": "Intersect multiple sorted sets and return the cardinality of the result",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N*K) worst case with N being the smallest input sorted set, K being the number of input sorted sets.",
  "since": "7.0.0",
  "return_summary": "@integer-reply: the number of elements in the resulting intersection.",
  "syntax": "numkeys key ...",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

This command is similar to [ZINTER](/commands/zinter), but instead of returning the result set, it returns just the cardinality of the result.

Keys that do not exist are considered to be empty sets.
With one of the keys being an empty set, the resulting set is also empty (since set intersection with an empty set always results in an empty set).

@examples

```cli
ZADD zset1 1 "one"
ZADD zset1 2 "two"
ZADD zset2 1 "one"
ZADD zset2 2 "two"
ZADD zset2 3 "three"
ZINTER 2 zset1 zset2
ZINTERCARD 2 zset1 zset2
```

