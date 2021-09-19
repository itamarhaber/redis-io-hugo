{
  "title": "ZDIFFSTORE",
  "summary": "Subtract multiple sorted sets and store the resulting sorted set in a new key",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(L + (N-K)log(N)) worst case where L is the total number of elements in all the sets, N is the size of the first set, and K is the size of the result set.",
  "since": "6.2.0",
  "return_summary": "@integer-reply: the number of elements in the resulting sorted set at\n`destination`.",
  "syntax": "destination numkeys key ...",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Computes the difference between the first and all successive input sorted sets
and stores the result in `destination`. The total number of input keys is
specified by `numkeys`.

Keys that do not exist are considered to be empty sets.

If `destination` already exists, it is overwritten.

@examples

```cli
ZADD zset1 1 "one"
ZADD zset1 2 "two"
ZADD zset1 3 "three"
ZADD zset2 1 "one"
ZADD zset2 2 "two"
ZDIFFSTORE out 2 zset1 zset2
ZRANGE out 0 -1 WITHSCORES
```

