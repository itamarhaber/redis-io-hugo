{
  "title": "ZRANK",
  "summary": "Determine the index of a member in a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N))",
  "since": "2.0.0",
  "return_summary": "* If `member` exists in the sorted set, @integer-reply: the rank of `member`.\n* If `member` does not exist in the sorted set or `key` does not exist,\n  @bulk-string-reply: `nil`.",
  "syntax": "key member",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the rank of `member` in the sorted set stored at `key`, with the scores
ordered from low to high.
The rank (or index) is 0-based, which means that the member with the lowest
score has rank `0`.

Use [ZREVRANK](/commands/zrevrank) to get the rank of an element with the scores ordered from high
to low.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZRANK myzset "three"
ZRANK myzset "four"
```

