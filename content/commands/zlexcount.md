{
  "title": "ZLEXCOUNT",
  "summary": "Count the number of members in a sorted set between a given lexicographical range",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)) with N being the number of elements in the sorted set.",
  "since": "2.8.9",
  "return_summary": "@integer-reply: the number of elements in the specified score range.",
  "syntax": "key min max",
  "acl_categories": [
    "sortedset",
    "slow"
  ]
}

When all the elements in a sorted set are inserted with the same score, in order to force lexicographical ordering, this command returns the number of elements in the sorted set at `key` with a value between `min` and `max`.

The `min` and `max` arguments have the same meaning as described for
[ZRANGEBYLEX](/commands/zrangebylex).

Note: the command has a complexity of just O(log(N)) because it uses elements ranks (see [ZRANK](/commands/zrank)) to get an idea of the range. Because of this there is no need to do a work proportional to the size of the range.

@examples

```cli
ZADD myzset 0 a 0 b 0 c 0 d 0 e
ZADD myzset 0 f 0 g
ZLEXCOUNT myzset - +
ZLEXCOUNT myzset [b [f
```

