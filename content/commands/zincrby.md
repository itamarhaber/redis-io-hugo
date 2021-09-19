{
  "title": "ZINCRBY",
  "summary": "Increment the score of a member in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)) where N is the number of elements in the sorted set.",
  "since": "1.2.0",
  "return_summary": "@bulk-string-reply: the new score of `member` (a double precision floating point\nnumber), represented as string.",
  "syntax": "key increment member",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Increments the score of `member` in the sorted set stored at `key` by
`increment`.
If `member` does not exist in the sorted set, it is added with `increment` as
its score (as if its previous score was `0.0`).
If `key` does not exist, a new sorted set with the specified `member` as its
sole member is created.

An error is returned when `key` exists but does not hold a sorted set.

The `score` value should be the string representation of a numeric value, and
accepts double precision floating point numbers.
It is possible to provide a negative value to decrement the score.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZINCRBY myzset 2 "one"
ZRANGE myzset 0 -1 WITHSCORES
```

