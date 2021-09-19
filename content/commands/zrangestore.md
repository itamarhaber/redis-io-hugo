{
  "title": "ZRANGESTORE",
  "summary": "Store a range of members from sorted set into another key",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements stored into the destination key.",
  "since": "6.2.0",
  "return_summary": "@integer-reply: the number of elements in the resulting sorted set.",
  "syntax": "dst src min max [BYSCORE|BYLEX] [REV] [LIMIT offset count]",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

This command is like [ZRANGE](/commands/zrange), but stores the result in the `<dst>` destination key.

@examples

```cli
ZADD srczset 1 "one" 2 "two" 3 "three" 4 "four"
ZRANGESTORE dstzset srczset 2 -1
ZRANGE dstzset 0 -1
```

