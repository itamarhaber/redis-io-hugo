{
  "title": "ZREM",
  "summary": "Remove one or more members from a sorted set",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(M*log(N)) with N being the number of elements in the sorted set and M the number of elements to be removed.",
  "since": "1.2.0",
  "return_summary": "@integer-reply, specifically:\n\n* The number of members removed from the sorted set, not including non existing\n  members.",
  "history": [
    [
      "2.4",
      "Accepts multiple elements."
    ]
  ],
  "syntax": "key member ...",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

Removes the specified members from the sorted set stored at `key`.
Non existing members are ignored.

An error is returned when `key` exists and does not hold a sorted set.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZREM myzset "two"
ZRANGE myzset 0 -1 WITHSCORES
```

