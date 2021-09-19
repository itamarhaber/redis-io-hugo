{
  "title": "ZREMRANGEBYLEX",
  "summary": "Remove all members in a sorted set between the given lexicographical range",
  "group": "sorted_set",
  "tags": [
    "Command",
    "Sorted_set"
  ],
  "date": "2001-02-03",
  "lastmod": "2001-02-03",
  "complexity": "O(log(N)+M) with N being the number of elements in the sorted set and M the number of elements removed by the operation.",
  "since": "2.8.9",
  "return_summary": "@integer-reply: the number of elements removed.",
  "syntax": "key min max",
  "acl_categories": [
    "sortedset",
    "write",
    "slow"
  ]
}

When all the elements in a sorted set are inserted with the same score, in order to force lexicographical ordering, this command removes all elements in the sorted set stored at `key` between the lexicographical range specified by `min` and `max`.

The meaning of `min` and `max` are the same of the [ZRANGEBYLEX](/commands/zrangebylex) command. Similarly, this command actually removes the same elements that [ZRANGEBYLEX](/commands/zrangebylex) would return if called with the same `min` and `max` arguments.

@examples

```cli
ZADD myzset 0 aaaa 0 b 0 c 0 d 0 e
ZADD myzset 0 foo 0 zap 0 zip 0 ALPHA 0 alpha
ZRANGE myzset 0 -1
ZREMRANGEBYLEX myzset [alpha [omega
ZRANGE myzset 0 -1
```

