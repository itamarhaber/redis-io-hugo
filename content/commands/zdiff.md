{
  "title": "ZDIFF",
  "summary": "Subtract multiple sorted sets",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(L + (N-K)log(N)) worst case where L is the total number of elements in all the sets, N is the size of the first set, and K is the size of the result set.",
  "since": "6.2.0",
  "return_summary": "@array-reply: the result of the difference (optionally with their scores, in case\nthe `WITHSCORES` option is given).",
  "syntax": "numkeys key ... [WITHSCORES]",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

This command is similar to [ZDIFFSTORE](/commands/zdiffstore), but instead of storing the resulting
sorted set, it is returned to the client.

@examples

```cli
ZADD zset1 1 "one"
ZADD zset1 2 "two"
ZADD zset1 3 "three"
ZADD zset2 1 "one"
ZADD zset2 2 "two"
ZDIFF 2 zset1 zset2
ZDIFF 2 zset1 zset2 WITHSCORES
```

