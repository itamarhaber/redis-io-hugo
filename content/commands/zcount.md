{
  "title": "ZCOUNT",
  "summary": "Count the members in a sorted set with scores within the given values",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)) with N being the number of elements in the sorted set.",
  "since": "2.0.0",
  "return_summary": "@integer-reply: the number of elements in the specified score range.",
  "syntax": "key min max",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

Returns the number of elements in the sorted set at `key` with a score between
`min` and `max`.

The `min` and `max` arguments have the same semantic as described for
[ZRANGEBYSCORE](/commands/zrangebyscore).

Note: the command has a complexity of just O(log(N)) because it uses elements ranks (see [ZRANK](/commands/zrank)) to get an idea of the range. Because of this there is no need to do a work proportional to the size of the range.

@examples

```cli
ZADD myzset 1 "one"
ZADD myzset 2 "two"
ZADD myzset 3 "three"
ZCOUNT myzset -inf +inf
ZCOUNT myzset (1 3
```

