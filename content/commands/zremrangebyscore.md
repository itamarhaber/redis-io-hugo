{
  "title": "ZREMRANGEBYSCORE",
  "summary": "Remove all members in a sorted set within the given scores",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements removed by the operation.",
  "since": "1.2.0",
  "return_summary": "@integer-reply: the number of elements removed.",
  "syntax": "key min max",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Removes all elements in the sorted set stored at `key` with a score between
`min` and `max` (inclusive).

Since version 2.1.6, `min` and `max` can be exclusive, following the syntax of
[ZRANGEBYSCORE](/commands/zrangebyscore).

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREMRANGEBYSCORE myzset -inf (2
ZRANGE myzset 0 -1 WITHSCORES
```

