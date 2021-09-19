{
  "title": "ZREVRANGEBYSCORE",
  "summary": "Return a range of members in a sorted set, by score, with scores ordered from high to low",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements being returned. If M is constant (e.g. always asking for the first 10 elements with LIMIT), you can consider it O(log(N)).",
  "since": "2.2.0",
  "return_summary": "@array-reply: list of elements in the specified score range (optionally\nwith their scores).",
  "deprecated": true,
  "syntax": "key max min [WITHSCORES] [LIMIT offset count]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns all the elements in the sorted set at `key` with a score between `max`
and `min` (including elements with score equal to `max` or `min`).
In contrary to the default ordering of sorted sets, for this command the
elements are considered to be ordered from high to low scores.

The elements having the same score are returned in reverse lexicographical
order.

Apart from the reversed ordering, [ZREVRANGEBYSCORE](/commands/zrevrangebyscore) is similar to
[ZRANGEBYSCORE](/commands/zrangebyscore).

As per Redis 6.2.0, this command is considered deprecated. Please prefer using the [ZRANGE](/commands/zrange) command with the `BYSCORE` and `REV` arguments in new code.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREVRANGEBYSCORE myzset +inf -inf
ZREVRANGEBYSCORE myzset 2 1
ZREVRANGEBYSCORE myzset 2 (1
ZREVRANGEBYSCORE myzset (2 (1
```

