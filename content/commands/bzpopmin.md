{
  "title": "BZPOPMIN",
  "summary": "Remove and return the member with the lowest score from one or more sorted sets, or block until one is available",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)) with N being the number of elements in the sorted set.",
  "since": "5.0.0",
  "return_summary": "@array-reply: specifically:\n\n* A `nil` multi-bulk when no element could be popped and the timeout expired.\n* A three-element multi-bulk with the first element being the name of the key\n  where a member was popped, the second element is the popped member itself,\n  and the third element is the score of the popped element.",
  "history": [
    [
      "6.0",
      "`timeout` is interpreted as a double instead of an integer."
    ]
  ],
  "syntax": "key ... timeout",
  "acl_categories": [
    "sortedset",
    "blocking",
    "write",
    "slow"
  ]
}

[BZPOPMIN](/commands/bzpopmin) is the blocking variant of the sorted set [ZPOPMIN](/commands/zpopmin) primitive.

It is the blocking version because it blocks the connection when there are no
members to pop from any of the given sorted sets.
A member with the lowest score is popped from first sorted set that is
non-empty, with the given keys being checked in the order that they are given.

The `timeout` argument is interpreted as an double value specifying the maximum
number of seconds to block. A timeout of zero can be used to block indefinitely.

See the [BLPOP documentation][cl] for the exact semantics, since [BZPOPMIN](/commands/bzpopmin) is
identical to [BLPOP](/commands/blpop) with the only difference being the data structure being
popped from.

[cl]: /commands/blpop

@examples

```
redis> DEL zset1 zset2
(integer) 0
redis> ZADD zset1 0 a 1 b 2 c
(integer) 3
redis> BZPOPMIN zset1 zset2 0
1) "zset1"
2) "a"
3) "0"
```

