{
  "title": "ZREMRANGEBYRANK",
  "summary": "Remove all members in a sorted set within the given indexes",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements removed by the operation.",
  "since": "2.0.0",
  "return_summary": "@integer-reply: the number of elements removed.",
  "syntax": "key start stop",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Removes all elements in the sorted set stored at `key` with rank between `start`
and `stop`.
Both `start` and `stop` are `0` -based indexes with `0` being the element with
the lowest score.
These indexes can be negative numbers, where they indicate offsets starting at
the element with the highest score.
For example: `-1` is the element with the highest score, `-2` the element with
the second highest score and so forth.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREMRANGEBYRANK myzset 0 1
ZRANGE myzset 0 -1 WITHSCORES
```
