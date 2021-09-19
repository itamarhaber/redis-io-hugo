{
  "title": "ZUNION",
  "summary": "Add multiple sorted sets",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(N)+O(M*log(M)) with N being the sum of the sizes of the input sorted sets, and M being the number of elements in the resulting sorted set.",
  "since": "6.2.0",
  "return_summary": "@array-reply: the result of union (optionally with their scores, in case \nthe `WITHSCORES` option is given).",
  "syntax": "numkeys key ... [WEIGHTS weight] [AGGREGATE aggregate] [WITHSCORES]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

This command is similar to [ZUNIONSTORE](/commands/zunionstore), but instead of storing the resulting
sorted set, it is returned to the client.

For a description of the `WEIGHTS` and `AGGREGATE` options, see [ZUNIONSTORE](/commands/zunionstore).

@examples

```cli
ZADD zset1 1 "one"
ZADD zset1 2 "two"
ZADD zset2 1 "one"
ZADD zset2 2 "two"
ZADD zset2 3 "three"
ZUNION 2 zset1 zset2
ZUNION 2 zset1 zset2 WITHSCORES
```

