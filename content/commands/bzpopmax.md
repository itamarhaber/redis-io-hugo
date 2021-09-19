{
  "title": "BZPOPMAX",
  "summary": "Remove and return the member with the highest score from one or more sorted sets, or block until one is available",
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

[BZPOPMAX](/commands/bzpopmax) is the blocking variant of the sorted set [ZPOPMAX](/commands/zpopmax) primitive.

It is the blocking version because it blocks the connection when there are no
members to pop from any of the given sorted sets.
A member with the highest score is popped from first sorted set that is
non-empty, with the given keys being checked in the order that they are given.

The `timeout` argument is interpreted as a double value specifying the maximum
number of seconds to block. A timeout of zero can be used to block indefinitely.

See the [BZPOPMIN documentation][cb] for the exact semantics, since [BZPOPMAX](/commands/bzpopmax)
is identical to [BZPOPMIN](/commands/bzpopmin) with the only difference being that it pops members
with the highest scores instead of popping the ones with the lowest scores.

[cb]: /commands/bzpopmin

@examples

```
redis> DEL zset1 zset2
(integer) 0
redis> ZADD zset1 0 a 1 b 2 c
(integer) 3
redis> BZPOPMAX zset1 zset2 0
1) "zset1"
2) "c"
3) "2"
```

