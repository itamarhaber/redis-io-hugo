{
  "title": "ZREVRANGE",
  "summary": "Return a range of members in a sorted set, by index, with scores ordered from high to low",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements returned.",
  "since": "1.2.0",
  "return_summary": "@array-reply: list of elements in the specified range (optionally with\ntheir scores).",
  "deprecated": true,
  "syntax": "key start stop [WITHSCORES]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the specified range of elements in the sorted set stored at `key`.
The elements are considered to be ordered from the highest to the lowest score.
Descending lexicographical order is used for elements with equal score.

Apart from the reversed ordering, [ZREVRANGE](/commands/zrevrange) is similar to [ZRANGE](/commands/zrange).

As per Redis 6.2.0, this command is considered deprecated. Please prefer using the [ZRANGE](/commands/zrange) command with the `REV` argument in new code.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREVRANGE myzset 0 -1
ZREVRANGE myzset 2 3
ZREVRANGE myzset -2 -1
```

