{
  "title": "ZREVRANGEBYLEX",
  "summary": "Return a range of members in a sorted set, by lexicographical range, ordered from higher to lower strings.",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements being returned. If M is constant (e.g. always asking for the first 10 elements with LIMIT), you can consider it O(log(N)).",
  "since": "2.8.9",
  "return_summary": "@array-reply: list of elements in the specified score range.",
  "deprecated": true,
  "syntax": "key max min [LIMIT offset count]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

When all the elements in a sorted set are inserted with the same score, in order to force lexicographical ordering, this command returns all the elements in the sorted set at `key` with a value between `max` and `min`.

Apart from the reversed ordering, [ZREVRANGEBYLEX](/commands/zrevrangebylex) is similar to [ZRANGEBYLEX](/commands/zrangebylex).

As per Redis 6.2.0, this command is considered deprecated. Please prefer using the [ZRANGE](/commands/zrange) command with the `BYLEX` and `REV` arguments in new code.

@examples

```cli
ZADD myzset 0 a 0 b 0 c 0 d 0 e 0 f 0 g
ZREVRANGEBYLEX myzset [c -
ZREVRANGEBYLEX myzset (c -
ZREVRANGEBYLEX myzset (g [aaa
```

